---
id: set-skin
title: setSkin
description: Change the default skin for the CRUD. So far we have two skins: light and dark. 
canonical: docs/set-skin
previous: where
next: columns
---

# setSkin

<pre><code class="language-php">setSkin(string $skin)</code></pre>

Choose between two skins: 'light' and 'dark'. The default skin is 'light'.

## Example

<pre><code class="language-php">$crud->setSkin('dark'); </code></pre>

## Full Example

<pre><code class="language-php">$crud->setSkin('dark');
$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();</code></pre>

You can see the results of the above code below:

`embed:demo_change-theme-skin`
