---
id: callback-before-upload
title: callbackBeforeUpload
permalink: docs/callback-before-upload
previous: callback-before-update
next: callback-clone-field
---

# callbackBeforeUpload


<pre><code class="language-php">callbackBeforeUpload(string $fieldName, callable $callback)</code></pre>
The callback is used in cases we need to filter the uploaded data before the upload functionality. This can also be used to cancel an upload in case that it doesn't fit with the requirements.

First of all, if we just want to dump the data that we will receive we can easily do it with the below code:

<pre><code class="language-php">$crud->callbackBeforeUpload(function ($test1 = null) {
    var_dump($test1);
    var_dump($_FILES);

    return false;
});</code></pre>

will result the below output:

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

The most common usage of callback before upload is when we need to validate the data with some extra custom validation. For example at the below example we are validating the upload to make sure that it has an image extension only. A full example will be as follows:

<pre><code class="language-php">$crud->callbackBeforeUpload(function ($uploadData) {
    $fieldName = $uploadData->field_name;

    $filename = isset($_FILES[$fieldName]) ? $_FILES[$fieldName]['name'] : null;

    if (!preg_match('/\.(png|jpg|jpeg|gif)$/',$filename)) {
        return (new \GroceryCrud\Core\Error\ErrorMessage())
            ->setMessage("The file extension for filename: '" . $filename. "'' is not supported!");
    }

    // Don't forget to return the uploadData at the end
    return $uploadData;
});</code></pre>

`embed:demo_callback-before-upload`