---
id: callback-after-upload
title: callbackAfterUpload
description: The callback that will be triggered right after the upload.
canonical: docs/callback-after-upload
previous: unset-clone-fields
next: callback-before-upload
---

# callbackAfterUpload

<pre><code class="language-php">callbackAfterUpload(callable $callback)</code></pre>
The callback that will be triggered right after the upload.

For example the below code will show us an error at the page (so we can dump the data after the upload):
<pre><code class="language-php">$crud->callbackAfterUpload(function ($result) {
    var_dump($result);
    die;

});</code></pre>

<pre><code>object(stdClass)#76 (2) {
  ["uploadResult"]=> string(21) "0266554465-bdeec.jpeg"
  ["stateParameters"]=>
  object(stdClass)#85 (6) {
    ["fieldName"]=> string(9) "photo_url"
    ["uploadFieldName"]=> string(28) "photo_url__gcrud_upload"
    ["uploadPath"]=> string(81) "/path/to/project/Uploads"
    ["maxUploadSize"]=> string(3) "20M"
    ["minUploadSize"]=> string(2) "1B"
    ["allowedFileTypes"]=>   array(4) {
        [0]=> string(3) "gif"
        [1]=> string(4) "jpeg"
        [2]=> string(3) "jpg"
        [3]=> string(3) "png"
    }
  }
}</code></pre>

A very common usage of the callbackAfterUpload in order to resize the image right after the upload. For example:
<pre><code class="language-php">
// Add this at the beginning of your file. 
// For more instructions of how to install it with composer
// go to: https://github.com/eventviva/php-image-resize
use Eventviva\ImageResize;
...
$crud->callbackAfterUpload(function ($result) {
   $fileName = $result->uploadResult;

   $fullPath = $result->uploadPath . $fileName;   

   $image = new ImageResize($fullPath);
   $image->resizeToBestFit(500, 300);
   $image->save($fullPath);

    return $result;
});</code></pre>