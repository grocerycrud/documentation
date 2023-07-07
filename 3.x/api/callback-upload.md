---
id: callback-upload
title: callbackUpload
description: The callbackUpload is used when we need to replace the default upload functionality of Grocery CRUD Enterprise.
canonical: docs/callback-upload
previous: callback-before-upload
next: set-field-upload
---

# callbackUpload

<pre><code class="language-php">callbackUpload(string $fieldName, callable $callback)</code></pre>
The callbackUpload is used when we need to replace the default upload functionality of Grocery CRUD Enterprise.

For example the below code will show us an error at the page (so we can dump the data after the upload):

<pre><code class="language-php">$crud->callbackUpload(function ($test1 = null) {
    var_dump($test1);

    return false;
});</code></pre>

will result the below output:

<pre><code>object(stdClass)#85 (5) {
  ["fieldName"] => string(9) "photo_url"
  ["uploadFieldName"] => string(28) "photo_url__gcrud_upload"
  ["uploadPath"] => string(81) "/path/to/project/Uploads"
  ["maxUploadSize"] => string(3) "20M"
  ["minUploadSize"] => string(2) "1B"
  ["allowedFileTypes"] => array(4) {
    [0] => string(3) "gif"
    [1] => string(4) "jpeg"
    [2] => string(3) "jpg"
    [3] => string(3) "png"
  }
}</code></pre>

Please have in mind that this is completely <strong>replacing</strong> the functionality of the default upload. That means that once you use this function you will need to make sure that:
<ul>
	<li>You will upload the file with extra code that you will create</li>
	<li>That you will handle any possible error</li>
	<li>Validate your data</li>
	<li>That you will return the correct results to the function or else throw an error (example follows below)</li>
</ul>

For example you can see a full working example below. The example is pretty big as it handles all of the above bullet points.

<pre><code class="language-php">// At this example we are using the Grocery CRUD Upload library. 
// However, you can replace it with any other library you wish! 
// Just make sure that you are returning the correct values as the below example.

$crud->callbackUpload(function ($uploadData)  {

    $uploadPath = $uploadData->uploadPath;
    $fieldName = $uploadData->uploadFieldName;
    $allowedFileTypes = $uploadData->allowedFileTypes;
    $maxUploadSize = $uploadData->maxUploadSize;
    $minUploadSize = $uploadData->minUploadSize;

    $uploader = new \GroceryCrud\Core\Upload\Upload($fieldName, $uploadPath);

    $uploader->setValidationAllowedExtensions($allowedFileTypes);
    $uploader->setValidationMaxUploadSize($maxUploadSize);
    $uploader->setValidationMinUploadSize($minUploadSize);

    if ($uploader->validate() === true) {
        $uploader->upload();
    } else {
        $errors = "- " . implode("\n -", $uploader->getValidationErrors());
        return (new \GroceryCrud\Core\Error\ErrorMessage())->setMessage("There were some validation errors with the upload:\n" . $errors);
    }

    $uploadResult = $uploader->getUploadedFiles()->getFirstUploadedFile();

    return (object)[
        'uploadResult' => $uploadResult,
        'stateParameters' => $uploadData
    ];
});</code></pre>