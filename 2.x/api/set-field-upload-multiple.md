---
id: set-field-upload-multiple
title: setFieldUploadMultiple
description: Upload data with the same use of setFieldUpload but with multiple uploads separated by comma in one field
permalink: docs/set-field-upload-multiple
previous: set-field-upload
next: callback-upload
enterprise: 1
---

# setFieldUploadMultiple

<pre><code class="language-php">setFieldUploadMultiple(string $fieldName, string $privateUploadFolder, string $publicFolderPath [, array $options])</code></pre>
There is a special type of field for uploading data or images and in order to trigger this type, you will need to use the <code>setFieldUploadMultiple</code> method. The usage is fairly easy and everything will work out of the box. You just need to make sure that the server has access to the specified folders.

The method is taking 3 parameters:
<ol>
	<li>The first parameter is the field name in the database. Have in mind that only the name of the file (without the full path) is stored</li>
	<li>The second parameter is the field that the file will actually be stored. If the path is the same as the public one then the second parameter will be the same with the 3rd</li>
	<li>The public path that the file can be accessed by the end-user that will need to be the full path</li>
</ol>

## Example
<pre><code class="language-php">$crud->setFieldUploadMultiple('image', 'uploader/customer-image', '/assets/images/customers');</code></pre>

<strong>Notice:</strong> Please have in mind that the public path will need to have the full URL of the folder. For example if you are using Codeigniter and the public path is the same with the private path then you will need to do something like this:

<pre><code class="language-php">$crud->setFieldUploadMultiple('profile_image', 'assets/uploads', base_url() . '/assets/uploads');</code></pre>

For security reasons of this website we currently don't have a full example of the <code>setFieldUploadMultiple</code>.

## Upload validations per field

After version 2.9.0 we also have a 4th parameter into the function that you can specify the upload validations per field. More specifically we have:

 - `maxUploadSize`. String value to specify the maximum upload size that a user can upload per file. Default: `'20M'` (20 Mega Bytes). Use "B", "K", "M" or "G". 
 - `minUploadSize`. String value to specify the minimum upload size that a user can upload per file. Default: `'1B'` (1 Byte). Use "B", "K", "M" or "G".
 - `allowedFileTypes`. An array of string values to specify the allowed field types. Default:
```
['gif', 'jpeg', 'jpg', 'png', 'svg', 'tiff', 'doc', 'docx',  'rtf', 'txt', 'odt', 'xls', 'xlsx', 'pdf',
'ppt', 'pptx', 'pps', 'ppsx', 'mp3', 'm4a', 'ogg', 'wav', 'mp4', 'm4v', 'mov', 'wmv', 'flv', 'avi',
'mpg', 'ogv', '3gp', '3g2']
```

Example:

<pre><code class="language-php">$uploadValidations = [
    'maxUploadSize' => '20M', // 20 Mega Bytes
    'minUploadSize' => '1K', // 1 Kilo Byte
    'allowedFileTypes' => [
        'gif', 'jpeg', 'jpg', 'png', 'tiff'
    ]
];
$crud->setFieldUploadMultiple(
    'image', 
    'uploader/customer-image', 
    '/assets/images/customers', 
    $uploadValidations
);</code></pre>

