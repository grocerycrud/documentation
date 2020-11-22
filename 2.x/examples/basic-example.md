---
id: basic-example
title: Basic Example
permalink: docs/basic-example
previous: 
next: full-example
---

# Basic Example

A very simple example to start with is the below 4 lines of code. These are the most common functions that you will use:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();
</code></pre>

More specifically let's describe what the functions are doing:
<ol>
	<li>setTable: The function setTable is setting the basic database table that we will use. Grocery CRUD Enterprise is clever enough to understand all the fields and types so you will not need to add some obvious default functionality that a CRUD should have</li>
	<li>setSubject: The setSubject is the subject of the CRUD for the end user. There are two parameters, the first is the subject as non-plural and the second one the subject as plural. This helps the end-user to understand what is the CRUD. For example, instead of "Insert", it will be replaced with "Insert Customer" and this is making it very clear to the end-user that this will record will insert a customer</li>
	<li>columns: The columns function is the one that it is mostly used as usually the fields are plenty and we need to show only few at the datagrid for simplicity</li>
	<li>render: The render function is the function that all the magic is happening. Without this function, nothing works really. The render method is recognising automatically it's state through the URL and the parameters of the request.</li>
</ol>

## Basic Example

Let's see what the above code will give us as a result:

`embed:demo_customers`