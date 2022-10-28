---
id: set-table
title: setTable
description: The main database table that you will use for your CRUD.  
permalink: docs/set-table
previous: render
next: set-subject
---

# setTable

<pre><code class="language-php">setTable(string $tableName)</code></pre>

setTable is the only required function that you have to use (it is not optional)

The usage is simple. You have to provide the database table name that you will use. For example if our table name is 'customers' you should use it like this:

<pre><code class="language-php">$crud->setTable('customers');</code></pre>

## Example

You can find a complete working example with the below code:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();</code></pre>

The result of the above code would be:

`embed:demo_set-table`
