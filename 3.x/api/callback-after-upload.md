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
    if ($result instanceof \GroceryCrud\Core\Upload\UploadedFiles) {
        var_dump($result->getFirstUploadedFile());
    }

    return false;
});</code></pre>

<pre><code>string(21) "0266554465-da738.jpeg"</code></pre>

A very common usage of the callbackAfterUpload in order to resize the image right after the upload. For example:
<pre><code class="language-php">
// Add this at the beginning of your file. 
// For more instructions of how to install it with composer
// go to: https://github.com/eventviva/php-image-resize
use Eventviva\ImageResize;
...
$crud->callbackAfterUpload(function ($result) {
   $fileName = $result->getFirstUploadedFile();

   $fullPath = '/path/to/upload/folder/' . $fileName;   

   $image = new ImageResize($fullPath);
   $image->resizeToBestFit(500, 300);
   $image->save($fullPath);

    return $result;
});</code></pre>