---
id: field-type-edit-form
title: fieldTypeEditForm
description: 	The function fieldTypeEditForm is used for cases that you need to change the field type but only for the edit/update form.
canonical: docs/field-type-edit-form
previous: field-type-column
next: field-type-form-fields
---

# fieldTypeEditForm


<pre><code class="language-php">fieldTypeEditForm(string $fieldName, string|ModelFieldType $fieldType)</code></pre>
This function is used for cases that you need to change the field type but only for the edit/update form. You can choose any field type from the <a href="https://www.grocerycrud.com/enterprise/api-and-function-list/fieldType">list of field types</a>.

Any of the of the below 2 examples have the exact same results:
<pre><code class="language-php">$crud-&gt;fieldTypeEditForm('birth_date_year', GroceryCrud::FIELD_TYPE_NUMERIC);</code></pre>

or:

<pre><code class="language-php">$crud-&gt;fieldTypeEditForm('birth_date_year', 'numeric');</code></pre>

You can also use the ModelFieldType object as an input. For example:

<pre><code class="language-php">&lt;?php
// ModelFieldType is only available on Grocery CRUD Enterprise
// Add the below code at the beginning of the file
use GroceryCrud\Core\Model\ModelFieldType;
...
// At your code
$myField = new ModelFieldType();
$myField-&gt;setDataType(GroceryCrud::FIELD_TYPE_NUMERIC);
$myField-&gt;setIsNullable(true);

$crud-&gt;fieldTypeEditForm('birth_date_year', $myField);</code></pre>