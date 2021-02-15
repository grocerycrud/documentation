---
id: required-fields
title: requiredFields
description: 
permalink: docs/required-fields
previous: render
next: set-action-button
---

# requiredFields


<pre><code class="language-php">requiredFields(array $fields)</code></pre>
A common validation for pretty much all the forms is the validation of required fields. Use the <code>requiredFields</code> method to add all the fields that are required. By adding a field as required you are getting:
<ol>
	<li>An asterisk at the left of the name so the user can understand that this field is required</li>
	<li>A <strong>client side</strong> validation for the required field. That means that you will get a prompt that this field is required <strong>before</strong> even the data is sent to the server</li>
	<li>A server side validation in case the client side was skipped for any reason</li>
</ol>

The syntax is simple, you just need to add the field names from the database that are required. For example:
<pre><code class="language-php">$crud->requiredFields(['first_name', 'last_name'])</code></pre>

You can see a full working example below:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->requiredFields(['customerName', 'contactLastName', 'contactFirstName']);

$output = $crud->render();</code></pre>

You can see live the required fields if you try to add or edit any row and save the form without a value for either one of the 3 required fields
`embed:demo_required-fields`