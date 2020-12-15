---
id: callback-upload
title: callbackUpload
permalink: docs/callback-upload
previous: callback-update
next: clone-fields
---

# callbackUpload


<pre><code class="language-php">callbackUpload(string $fieldName, callable $callback)</code></pre>
The callbackUpload is used when we need to replace the default upload functionality of Grocery CRUD Enterprise.

For example the below code will show us an error at the page (so we can dump the data after the upload):

<pre><code class="language-php">$crud->callbackUpload(function ($test1 = null) {
    var_dump($test1);
    var_dump($_FILES);

    return false;
});</code></pre>

will result the below:

<pre><code>object(stdClass)[36]
  public 'field_name' => string 'photo_url' (length=14)</code></pre>

<pre><code>array (size=1)
  'photo_url' => 
    array (size=5)
      'name' => string 'photo-1191.jpg' (length=14)
      'type' => string 'image/jpeg' (length=10)
      'tmp_name' => string '/tmp/php/phpxSfeuZ' (length=19)
      'error' => int 0
      'size' => int 6756
</code></pre>

Please have in mind that this is completely <strong>replacing</strong> the functionality of the default upload. That means that once you use this function you will need to make sure that:
<ul>
	<li>You will upload the file with extra code that you will create</li>
	<li>That you will handle any possible error</li>
	<li>Validate your data</li>
	<li>That you will return the correct results to the function or else throw an error (example follows below)</li>
</ul>

For example you can see a full working example below. The example is pretty big as it handles all of the above bullet points.

<pre><code class="language-php">// At this example we are using the library of: https://packagist.org/packages/codeguy/upload
// So please make sure that if you are going to use the below code you will need to install this library first

$crud->callbackUpload(function ($uploadData)  {
    // Hardcoded paths. Please make sure that in case you just copy the below code that you replace these
    // two variables with yours
    $uploadPath = '/real/upload/path/'; // directory of the drive
    $publicPath = '/Uploads/'; // public directory (at the URL)

    $fieldName = $uploadData->field_name;

    $storage = new \Upload\Storage\FileSystem($uploadPath);
    $file = new \Upload\File($fieldName, $storage);

    $filename = isset($_FILES[$fieldName]) ? $_FILES[$fieldName]['name'] : null;

    if ($filename === null) {
        return false;
    }

    // The library that we are using want us to remove the file extension as it is adding it by itself!
    $filename = preg_replace('/\\.[^.\\s]{3,4}$/', '', $filename);
    // Replace illegal characters with an underscore
    $filename = preg_replace("/([^a-zA-Z0-9\-\_]+?){1}/i", '_', $filename);

    $file->setName($filename);

    // Validate file upload
    $file->addValidations([
        new \Upload\Validation\Extension(['gif', 'jpeg', 'jpg', 'png']),
        new \Upload\Validation\Size('20M')
    ]);

    // Work around so the try catch will work as expected.
    // Upload file will not yield any error if the error_reporting is 0
    $display_errors = ini_get('display_errors');
    $error_reporting = error_reporting();
    ini_set('display_errors', 'on');
    error_reporting(E_ALL);

    // Upload file
    try {
        // Success!
        $file->upload();

    } catch (\Upload\Exception\UploadException $e) {
        // Upload error, return a custom message
        $errors = print_r($file->getErrors(), true);
        return (new \GroceryCrud\Core\Error\ErrorMessage())->setMessage("There was an error with the upload:\n" . $errors);
    } catch (\Exception $e) {
        throw $e;
    }

    ini_set('display_errors', $display_errors);
    error_reporting($error_reporting);

    $filename = $file->getNameWithExtension();

    // Make sure that you return the results
    $uploadData->filePath = $publicPath . '/' . $filename;
    $uploadData->filename = $filename;

    return $uploadData;
});</code></pre>


`embed:demo_callback-upload`