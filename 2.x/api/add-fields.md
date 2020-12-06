---
id: add-fields
title: addFields
permalink: docs/gcc/2.x/add-fields
previous: 
next: clone-fields
---

# addFields
<pre><code class="language-php">addFields(array $addFields)</code></pre>
The fields that will be visible to the end user for add/insert form. For example:

<pre><code class="language-php">$crud->addFields(['first_name', 'last_name', 'fullname', 'address'])</code></pre>

You can see a full working example below:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->addFields(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();</code></pre>


You can see the result of the above code below.The main difference that you will notice is that when you will press the "Add customer" button. The fields are less when you add one (these are the fields that was specified at the addFields functions) than by pressing the edit button.

`embed:demo_add_fields`
