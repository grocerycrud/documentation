---
id: set-skin
title: setSkin
permalink: docs/set-skin
previous: set-language
next: columns
---

# setSkin

<pre><code class="language-php">setSkin(string $skin)</code></pre>

Choose between two skins: Bootstrap v3 and Bootstrap V4

The default skin is Bootstrap V3 or else you can set the skin as 'bootstrap-v3'. In order to change the default skin to Bootstrap V4, you simply need to add the below line of code:

<pre><code class="language-php">$crud->setSkin('bootstrap-v4');</code></pre>

You can find a full example below:

<pre><code class="language-php">
$crud->setSkin('bootstrap-v4');
$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();</code></pre>

You can see the results of the above code below:
