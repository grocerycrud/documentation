---
id: set-theme-path
title: setThemePath
permalink: docs/set-theme-path
previous: set-theme
next: set-unique-id
---

# setThemePath


<pre><code class="language-php">setThemePath(string $themePath)</code></pre>
<code>setThemePath</code> is used when we want to change the folder that the theme exists. This is usually a case when we need to create a custom theme that will not be included at the default core of Grocery CRUD. 

To change the default theme path is easy. For example:

<pre><code class="language-php">$crud->setThemePath('/my/custom/theme/path/')</code></pre>

You can see a full example below:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->setTheme('Cyborg');
$crud->setThemePath('private/themes/');

$output = $crud->render();</code></pre>