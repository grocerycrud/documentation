---
id: unset-jquery-ui
title: unsetJqueryUi
permalink: docs/unset-jquery-ui
previous: unset-jquery
next: unset-modernizr
---

# unsetJqueryUi


<pre><code class="php">unsetJqueryUi(void)</code></pre>
A common usage of GroceryCRUD is to be used in an already existing admin template or an already existing project. As jQueryUI is a bit heavy library by its own, it is important to be loaded only once. For example, if your project already have jQueryUI we don't have to load it again. In that case we are using the <code>unsetJqueryUi</code> method. The syntax is simple as it doesn't take any parameters. 

For example:
<pre><code class="php">$crud->unsetJqueryUi()</code></pre>

With the above code, the Javascript <strong>and</strong> the CSS of jQueryUI is removed. It important to be aware of that as you need to make sure that the template offers the required JavaScript and the CSS for the jQueryUI before using the function <code>unsetJqueryUi</code>

You can see a full example below:
<pre><code class="php">$crud->setTable('orders');
$crud->setSubject('Order', 'Orders');
$crud->unsetAdd();

$crud->unsetJqueryUi();

$output = $crud->render();</code></pre>

The result of the above code you can see it here. However it is hard for you to see the difference! So in order to do that you will need see the source of this page (by pressing right click "View Page Source"). If you scroll at the bottom of the source (right before the <code>&lt;/body&gt;</code> for the JavaScript) there you can see that we've already loaded the jQueryUI Javascript from the CDN of jQueryUI and we don't need to load it again. And hence we will need to unset jQueryUI from loading from grocery CRUD.

[demo]demo_unset_jquery_ui[/demo]