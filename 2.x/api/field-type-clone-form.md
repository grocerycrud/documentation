---
id: field-type-clone-form
title: fieldTypeCloneForm
permalink: docs/field-type-clone-form
previous: clone-fields
next: set-clone
---

# fieldTypeCloneForm


<pre><code class="language-php">fieldTypeCloneForm(string $fieldName, string|ModelFieldType $fieldType)</code></pre>
This function is used for cases that you need to change the field type but only for the Clone form. You can choose any field type from the <a href="https://www.grocerycrud.com/enterprise/api-and-function-list/fieldType">list of field types</a>.

Both 3 below examples will have the exact same results:
<pre><code class="language-php">$crud-&gt;fieldTypeCloneForm('date_birth_year', 'numeric');</code></pre>
or:
<pre><code class="language-php">$crud-&gt;fieldTypeCloneForm('date_birth_year', GroceryCrud::FIELD_TYPE_NUMERIC);</code></pre>
or:
<pre><code class="language-php">
// At the beginning of the file
use GroceryCrud\Core\Model\ModelFieldType;
...
$myField = new ModelFieldType();
$myField-&gt;setDataType(GroceryCrud::FIELD_TYPE_NUMERIC);
$crud-&gt;fieldTypeCloneForm('date_birth_year', $myField);</code></pre>