---
id: set-field-upload
title: setFieldUpload
permalink: docs/set-field-upload
previous: set-field-blob
next: set-lang-string
---

# setFieldUpload


<pre><code class="php">setFieldUpload(string $fieldName, string $privateUploadFolder, string $publicFolderPath)</code></pre>
There is a special type of field for uploading data or images and in order to trigger this type, you will need to use the <code>setFieldUpload</code> method. The usage is fairly easy and everything will work out of the box. You just need to make sure that the server has access to the specified folders.

The method is taking 3 parameters:
<ol>
	<li>The first parameter is the field name in the database. Have in mind that only the name of the file (without the full path) is stored</li>
	<li>The second parameter is the field that the file will actually be stored. If the path is the same as the public one then the second parameter will be the same with the 3rd</li>
	<li>The public path that the file can be accessed by the end-user that will need to be the full path</li>
</ol>

For example:
<pre><code class="php">$crud->setFieldUpload('image', 'uploader/customer-image', '/assets/images/customers');</code></pre>

<strong>Notice:</strong> Please have in mind that the the public path will need to have the full URL of the folder. For example if you are using Codeigniter and the public path is the same with the private path then you will need to do something like this:

<pre><code class="php">$crud->setFieldUpload('profile_image', 'assets/uploads', base_url() . '/assets/uploads');</code></pre>

For security reasons of this website we currently don't have a full example of the <code>setFieldUpload</code>.
