---
id: set-field-blob
title: setFieldBlob
description: The function setFieldBlob is used to enable the upload functionality for Blob field type. 
permalink: docs/set-field-blob
previous: field-type-read-form
next: set-texteditor
enterprise: 1
---

# setFieldBlob


<pre><code class="language-php">setFieldBlob(string $fieldName, string $filenameField, string $temporaryUploadDirectory, string $maxUploadSize)</code></pre>
Enable the upload functionality for Blob field type. For example: BLOB, MEDIUMBLOB,... e.t.c. 
<ul>
	<li><strong>$fieldName:</strong> The field name that has the blob field type. For example: BLOB, MEDIUMBLOB,... e.t.c. Please also consider to have it NULL-able in case this field is not required.</li>
	<li><strong>$filenameField:</strong> The field name to store the filename of the blob file. As we are using two fields and the functionality is not supporting editing functionality for the filename (for now), it is strongly suggested for you to remove the field name from editing by simply using: <pre><code class="language-php">$crud->unsetFields(['image_filename']);</code></pre></li>
        <li><strong>$temporaryUploadDirectory:</strong> Please use a private folder for security (e.g. to not be accessible via public link). Also make sure that you have write access to the folder. This folder is <strong>only</strong> used in order to temporary upload the file and then Grocery CRUD will delete the uploaded file automatically. This folder is a required field for security reasons as it is also required by PHP.</li>
	<li><strong>$maxUploadSize:</strong> One letter maximum file size. For example: '1M' equals with 1MB, '256K' equals '256KB',.... e.t.c. This is a required field as we are not always certain about the specific maximum upload size that we would like our system to support. If you would like to use the standard fixed maximum size per field type you can use <code>GroceryCrud\Core\Helpers\BlobFieldTypeHelper</code>. For more you can also check the <a href="#full-example">full example</a> below</li>
</ul>

For example:
<pre><code class="language-php">$crud->setFieldBlob('my_blob', 'blob_filename',  'application/private/tmp', '2M');</code></pre>

## Example

<pre><code class="language-php">

use GroceryCrud\Core\Helpers\BlobFieldTypeHelper;
...

$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit', 'image']);

// You will need to make sure that you unset the image_filename field as this is not an editable field
$crud->unsetFields(['image_filename']);
$crud->unsetColumns(['image_filename']);
$crud->setFieldBlob('image', 'image_filename', 'application/private/tmp', BlobFieldTypeHelper::getFilesizeFromFieldType('MEDIUMBLOB'));

$output = $crud->render();</code></pre>

