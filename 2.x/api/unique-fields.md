---
id: unique-fields
title: uniqueFields
description: 
canonical: docs/unique-fields
previous: set-unique-id
next: unset-add
---

# uniqueFields


<pre><code class="language-php">uniqueFields(array $fields)</code></pre>
It is common to have some fields that are unique (that needs to make sure that the value is unique to the whole table) such as url, product number,... e.t.c. This is a very common validation, however it can be a bit more hard as there are lot of things to check. The <code>uniqueFields</code> was created to solve that complexity. The syntax is simple and you just need to add the fields that are unique. Nothing more than that! Once the add or edit form validates that the field is not unique, it will show a validation error that the user will need to solve.

The syntax is simple:
<pre><code class="language-php">$crud->uniqueFields(['url', 'reference_id'])</code></pre>

It is better to see it working to understand 100% the functionality. So at the below example:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->uniqueFields(['salesRepEmployeeNumber']);

return $crud->render();</code></pre>

We did set as unique field the salesRepEmployeeNumber. In order to get the error on your page, try to add a value at the field SalesRepEmployeeNumber (e.g. 1234) and then try to edit another row and edit the same number (e.g. try 1234). The form will not let you to add this value and it will throw a validation error "SalesRepEmployeeNumber must contain a unique value.". You can see by your own at the below datagrid:

`embed:demo_unique-fields`