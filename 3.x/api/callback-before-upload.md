---
id: callback-before-upload
title: callbackBeforeUpload
description: The callback is used in cases we need to filter the uploaded data before the upload functionality.
canonical: docs/callback-before-upload
previous: callback-after-upload
next: callback-upload
---

# callbackBeforeUpload

<pre><code class="language-php">callbackBeforeUpload(string $fieldName, callable $callback)</code></pre>
The callback is used in cases we need to filter the uploaded data before the upload functionality. 
This can also be used to cancel an upload in case that it doesn't fit with the requirements.

First of all, if we just want to dump the data that we will receive within the callback we can easily do it with the below code:

<pre><code class="language-php">$crud->callbackBeforeUpload(function ($test1 = null) {
    var_dump($test1);

    return false;
});</code></pre>

will result the below output:

<pre><code>object(stdClass)#85 (5) {
  ["uploadFieldName"]=>
  string(28) "photo_url__gcrud_upload"
  ["uploadPath"]=>
  string(81) "/path/to/project/Uploads"
  ["maxUploadSize"]=>
  string(3) "20M"
  ["minUploadSize"]=>
  string(2) "1B"
  ["allowedFileTypes"]=>
  array(4) {
    [0]=> string(3) "gif"
    [1]=> string(4) "jpeg"
    [2]=> string(3) "jpg"
    [3]=> string(3) "png"
  }
}</code></pre>

The most common usage of callback before upload is when we need to validate the data with some extra custom validation. For example at the below example we are validating the upload to make sure that it has an image extension only. A full example will be as follows:

<pre><code class="language-php">$crud->callbackBeforeUpload(function ($uploadData) {
    $fieldName = $uploadData->uploadFieldName;

    $filename = !empty($_FILES["data"]) ? $_FILES["data"]["name"][$fieldName][0] : '';

    if (!preg_match('/\.(png|jpg|jpeg|gif)$/',$filename)) {
        return (new \GroceryCrud\Core\Error\ErrorMessage())
            ->setMessage("The file extension for filename: '" . $filename. "'' is not supported!");
    }

    // Don't forget to return the uploadData at the end
    return $uploadData;
});</code></pre>