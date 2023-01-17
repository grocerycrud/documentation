---
id: change-theme-skin
title: Change theme skin
description: Change the default theme of Grocery CRUD Enterprise.
canonical: docs/change-theme-skin
previous: set-database-relation
next: api-and-functions-list
---

# Change theme skin

In case you would like to have the latest theme for bootstrap version 4 then you will simply need to add the below line of code at your PHP CRUD:

<pre><code class="language-php">$crud->setSkin('bootstrap-v4');</code></pre>

## Example

Below you can find a full working example with bootstrap version 3 theme:

<pre><code class="language-php">
$crud->setSkin('bootstrap-v4');
$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();</code></pre>

You can see the results of the above code below:

`embed:demo_change-theme-skin`