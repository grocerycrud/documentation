---
id: render
title: render
permalink: docs/render
previous: basic-example
next: set-table
---

# render

<pre><code class="language-php">render()</code></pre>

This is the most basic function that exists in grocery CRUD. In other words this means “make it work”.

## Example

A very simple example of the below lines:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();
</code></pre>

Can have the below result. The below code is <strong>not</strong> an iframe so you can also check the code produced by simply checking the page source of the webpage

`embed:demo_customers`
