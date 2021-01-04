---
id: fields
title: fields
permalink: docs/fields
previous: edit-fields
next: field-type
---

# fields


<pre><code class="language-php">fields(array $fields);</code></pre>

This is simply an alias of using addFields, editFields, readFields and cloneFields. This method was created as it is very common that at the add/edit/read/clone form to have the same fields.

So for example the below line of code:
<pre><code class="language-php">$crud->fields(['first_name', 'last_name', 'address']);</code></pre>

is exactly the same as:
<pre><code class="language-php">$crud->addFields(['first_name', 'last_name', 'address']);
$crud->editFields(['first_name', 'last_name', 'address']);
$crud->readFields(['first_name', 'last_name', 'address']);
$crud->cloneFields(['first_name', 'last_name', 'address']);
</code></pre>

You can see a full working example below. At the below example as you will notice, we haven't added any <a href="/enterprise/api-and-function-list/columns-2">columns</a> so you can see that the fields are more than 4 at the datagrid but only 4 on each form layer (e.g. if you try to edit one row).

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->fields(['customerName', 'phone', 'addressLine1', 'creditLimit']);

$output $crud->render();</code></pre>

You can see the result of the above code here:
`embed:demo_fields`
