---
id: set-skin
title: setSkin
description: Change the default skin for the CRUD. So far we have two skins: bootstrap v3 and bootstrap v4. 
permalink: docs/set-skin
previous: where
next: columns
---

# setSkin

<pre><code class="language-php">setSkin(string $skin)</code></pre>

Choose between two skins: Bootstrap v3 and Bootstrap V4

The default skin is Bootstrap V4 or else you can set the skin as 'bootstrap-v4'. In order to change the default skin to Bootstrap V4, you simply need to add the below line of code:

<pre><code class="language-php">// Choose between 'bootstrap-v3', 'bootstrap-v4' and 'bootstrap-v5'
$crud->setSkin('bootstrap-v3'); </code></pre>

<pre><code class="language-php">
$crud->setSkin('bootstrap-v3');
$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();</code></pre>

You can see the results of the above code below:

`embed:demo_change-theme-skin`
