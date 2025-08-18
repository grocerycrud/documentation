---
id: inline-edit-fields
title: inlineEditFields
description: The fields that will have inline quick edit functionality with double-click on datagrid.
canonical: docs/inline-edit-fields
previous: callback-update
next: set-edit
---

# inlineEditFields

<pre><code class="language-php">inlineEditFields(array $inlineEditFields)</code></pre>

The fields that will have inline quick edit functionality with double-click on datagrid. For example:
<pre><code class="language-php">$crud->inlineEditFields(['first_name', 'last_name', 'fullname', 'address'])</code></pre>

You can see a full working example below:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');

$crud->columns(['customerName','phone','addressLine1','creditLimit']);
$crud->inlineEditFields(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();</code></pre>

You can see the result of the above code below. Try to double-click on any of the fields that you specified in 
the `inlineEditFields` function. You will notice that the field will become instantly editable and a save button will 
appear next to it.

`embed:demo_inline-edit-fields`