---
id: field-type-read-form
title: fieldTypeReadForm
permalink: docs/field-type-read-form
previous: field-type-form-fields
next: get-state
---

# fieldTypeReadForm


<pre><code class="language-php">fieldTypeReadForm(string $fieldName, string|ModelFieldType $fieldType)</code></pre>
This function is used when you need to change the field type but only for the read/view form.  You can choose any field type from the <a href="https://www.grocerycrud.com/enterprise/api-and-function-list/fieldType">list of field types</a>.

Any of the of the below 2 examples have the exact same results:
<pre><code class="language-php">$crud-&gt;fieldTypeReadForm('date_of_birth', GroceryCrud::FIELD_TYPE_DATE);</code></pre>

or:

<pre><code class="language-php">$crud-&gt;fieldTypeReadForm('date_of_birth', 'date');</code></pre>

You can also use the ModelFieldType object as an input. For example:

<pre><code class="language-php">
// At the beginning of the file
use GroceryCrud\Core\Model\ModelFieldType;
...
// At your code
$myField = new ModelFieldType();
$myField-&gt;setDataType(GroceryCrud::FIELD_TYPE_DATE);
$myField-&gt;setIsNullable(true);

$crud-&gt;fieldTypeReadForm('date_of_birth', $myField);</code></pre>

The default value of the <code>ModelFieldType</code> object is <code>'varchar'</code> so for example if you have the below line:

<code>$crud-&gt;fieldTypeReadForm('date_of_birth', new ModelFieldType());</code>

or:

<pre><code class="language-php">
$myField = new ModelFieldType();
$crud-&gt;fieldTypeReadForm('date_of_birth', $myField);</code></pre>

the field type for read form will be <code>'varchar'</code>
