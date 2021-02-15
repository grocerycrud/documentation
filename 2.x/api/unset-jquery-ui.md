---
id: unset-jquery-ui
title: unsetJqueryUi
description: 
permalink: docs/unset-jquery-ui
previous: unset-jquery
next: unset-modernizr
---

# unsetJqueryUi


<pre><code class="language-php">unsetJqueryUi(void)</code></pre>
A common usage of GroceryCRUD is to be used in an already existing admin template or an already existing project. As jQueryUI is a bit heavy library by its own, it is important to be loaded only once. For example, if your project already have jQueryUI we don't have to load it again. In that case we are using the <code>unsetJqueryUi</code> method. The syntax is simple as it doesn't take any parameters. 

For example:
<pre><code class="language-php">$crud->unsetJqueryUi()</code></pre>

With the above code, the Javascript <strong>and the CSS</strong> of jQueryUI is removed. It important to be aware of that as you need to make sure that the template offers the required JavaScript and the CSS for the jQueryUI before using the function <code>unsetJqueryUi</code>

## Example

You can see a full example below:
<pre><code class="language-php">$crud->setTable('orders');
$crud->setSubject('Order', 'Orders');
$crud->unsetAdd();

$crud->unsetJqueryUi();

$output = $crud->render();</code></pre>