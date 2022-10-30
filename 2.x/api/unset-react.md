---
id: unset-react
title: unsetReact
description: 
canonical: docs/unset-react
previous: unset-print
next: unset-read
---

# unsetReact


<pre><code class="language-php">unsetReact(void)</code></pre>
A common usage of GroceryCRUD is to be used in an already existing admin template or an already existing project. As React is a bit heavy library by its own, it is important to be loaded only once. For example, if your project already have React we don't have to load it again. In that case we are using the <code>unsetReact</code> method. The syntax is simple as it doesn't take any parameters. 

For example:
<pre><code class="language-php">$crud->unsetReact()</code></pre>

The most common usages of this method is:

<ol>
	<li>When you've already have loaded React to your template and you don't want to load it twice with Grocery CRUD</li>
        <li>You would like to experiment with newer versions of React</li>
        <li>You are using React library through CDN</li>
</ol>

You can see a full example below:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->unsetReact();

$output = $crud->render();</code></pre>