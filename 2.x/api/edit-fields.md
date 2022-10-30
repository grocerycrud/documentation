---
id: edit-fields
title: editFields
description: The fields that will be visible to the end user for edit/update form.
canonical: docs/edit-fields
previous: callback-update
next: set-edit
---

# editFields

<pre><code class="language-php">editFields(array $editFields)</code></pre>
The fields that will be visible to the end user for edit/update form. For example:

<pre><code class="language-php">$crud->editFields(['first_name', 'last_name', 'fullname', 'address'])</code></pre>

You can see a full working example below:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->editFields(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();</code></pre>


You can see the result of the above code below.The main difference that you will notice is that when you will press the "Edit customer" button at any row. The fields are less when you edit one (these are the fields that was specified at the editFields functions). You can simply compare the differences by also trying to press the "Add customer" button and see all the existing fields.
`embed:demo_edit-fields`