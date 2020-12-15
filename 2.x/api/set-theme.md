---
id: set-theme
title: setTheme
permalink: docs/set-theme
previous: set-texteditor
next: set-theme-path
---

# setTheme


<pre><code class="language-php">setTheme(string $theme)</code></pre>
The setTheme is used in order to change the default theme (bootstrap). Have in mind that a theme is the full HTML,JS and CSS so it is not only re-skinning. The syntax is simple:

<pre><code class="language-php">$crud->setTheme('myCustomTheme')</code></pre>

Example:

<pre><code class="language-php">$crud->setTheme('darklyBootstrap');
$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);</code></pre>

<strong>Important notice:</strong> The above example theme does NOT exist at the default core functionality of grocery CRUD. In order to use the setTheme you will need to create your own theme almost from scratch. This is just a demonstration to see how easy you can use another theme once it is created.

Also it is suggested to use the <a href="/enterprise/api-and-function-list/setThemePath">setThemePath</a> as well with the setTheme to use your own path when you are creating a theme.

`embed:demo_set-theme`