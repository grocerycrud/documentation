---
id: unset-jquery
title: unsetJquery
permalink: docs/unset-jquery
previous: unset-bootstrap
next: unset-jquery-ui
---

# unsetJquery


<pre><code class="language-php">unsetJquery(void)</code></pre>
A common usage of GroceryCRUD is to be used in an already existing admin template or an already existing project. As jQuery is a bit heavy library by its own, it is important to be loaded only once. For example, if your project already have jQuery we don't have to load it again. In that case we are using the <code>unsetJquery</code> method. The syntax is simple as it doesn't take any parameters. 

For example:
<pre><code class="language-php">$crud->unsetJquery()</code></pre>

In some cases, maybe because it is required to add this one liner Grocery CRUD may not load! So be careful with how you load your Javascript to prevent these kind of issues. The most of the cases that Grocery CRUD doesn't load is because the user already have jQuery loaded and the jQuery of grocery CRUD was overridden.

## Example

You can see a full example below:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->unsetJquery();

$output = $crud->render();</code></pre>