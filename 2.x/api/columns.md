---
id: columns
title: columns
permalink: docs/columns
previous: set-skin
next: callback-column
---

# columns

<pre><code class="language-php">columns(array $columns)</code></pre>

Simply specify the fields that the end user will see as the datagrid columns. An example of the syntax is the below:

<pre><code class="language-php">$crud->columns(['first_name', 'last_name', 'age']);</code></pre>

If you want to check a full working example you can see the below example. The table customers has something like 12 fields, however at the datagrid we want to show only 4 columns:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();</code></pre>

So the above code will produce the below working example:

`embed:demo_customers`
