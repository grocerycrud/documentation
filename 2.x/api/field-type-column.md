---
id: field-type-column
title: fieldTypeColumn
permalink: docs/field-type-column
previous: field-type-clone-form
next: field-type-edit-form
---

# fieldTypeColumn

<pre><code class="language-php">fieldTypeColumn(string $columnName, string|ModelFieldType $fieldType)</code></pre>
This function is used for cases that you need to change the field type but only for the column (e.g. not for add/edit/read form). You can choose any field type from the <a href="https://www.grocerycrud.com/enterprise/api-and-function-list/fieldType">list of field types</a>.

<h2>Example</h2>

Let's say that we need to show a field that by default is datetime field but on the columns we would like to show it as date (remove the time from the columns).

In order to do that any of the of the below 2 examples have the exact same results:
<pre><code class="language-php">$crud-&gt;fieldTypeColumn('order_datetime', GroceryCrud::FIELD_TYPE_DATE);</code></pre>

or:

<pre><code class="language-php">$crud-&gt;fieldTypeColumn('order_datetime', 'date');</code></pre>

And the above example will safely change the fieldType but only for the columns of the datagrid.
