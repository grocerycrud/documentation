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
<pre><code class="language-php">$crud->callbackAfterUpload(function ($test1) {
    var_dump($test1);

    return false;
});</code></pre>

<pre><code>object(stdClass)[91]
  public 'filename' => string 'my-image.png',
  public 'filePath' => string '/Uploads/my-image.png',
  public 'fieldName' => string 'profile_thumbnail' // &lt;-- Available at version 2.4.0 or higher</code></pre>

A very common usage of the callbackAfterUpload in order to resize the image right after the upload. For example:
<pre><code class="language-php">
// Add this at the beginning of your file. 
// For more instructions of how to install it with composer
// go to: https://github.com/eventviva/php-image-resize
use Eventviva\ImageResize;
...
$crud->callbackAfterUpload(function ($data = null) {
   $fullPath = '/path/to/upload/folder/' . $data->filename;   

   $image = new ImageResize($fullPath);
   $image->resizeToBestFit(500, 300);
   $image->save($fullPath);

    return $data;
});</code></pre>