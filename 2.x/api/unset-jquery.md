---
id: unset-jquery
title: unsetJquery
permalink: docs/unset-jquery
previous: unset-fields
next: unset-jquery-ui
---

# unsetJquery


<pre><code class="language-php">unsetJquery(void)</code></pre>
A common usage of GroceryCRUD is to be used in an already existing admin template or an already existing project. As jQuery is a bit heavy library by its own, it is important to be loaded only once. For example, if your project already have jQuery we don't have to load it again. In that case we are using the <code>unsetJquery</code> method. The syntax is simple as it doesn't take any parameters. 

For example:
<pre><code class="language-php">$crud->unsetJquery()</code></pre>

In some cases, maybe because it is required to add this one liner Grocery CRUD may not load! So be careful with how you load your Javascript to prevent these kind of issues. The most of the cases that Grocery CRUD doesn't load is because the user already have jQuery loaded and the jQuery of grocery CRUD was overridden.

You can see a full example below:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->unsetJquery();

$output = $crud->render();</code></pre>

The result of the above code you can see it here. However it is hard for you to see the difference! So in order to do that you will need see the source of this page (by pressing right click "View Page Source"). If you scroll at the bottom of the source (right before the <code>&lt;/body&gt;</code>) There you can see that we've already loaded the jQuery from the CDN of jQuery and we don't need to load it again. And hence we will need to unset jQuery from loading from grocery CRUD.

[demo]demo_unset_jquery[/demo]