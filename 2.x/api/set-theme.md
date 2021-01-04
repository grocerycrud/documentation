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

This is one of the few functions that are used differently in community edition from Grocery CRUD Enterprise.

More specifically in community edition we can use the `setTheme` for the existing themes that we have, more specifically:

 - flexigrid (default)
 - datatables
 - bootstrap-v3 (only with after a purchase)
 - bootstrap-v4 (only with after a purchase)

## Example (Community edition)

<pre><code class="language-php">$crud->setTheme('bootstrap-v3');
$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);</code></pre>

However, for Grocery CRUD Enterprise edition this is a more advanced technique when you would like to create a custom new theme.
For this reason we combine the `setTheme` with [setThemePath](/docs/set-theme-path) and this is only for advanced users.

If you are using Grocery CRUD Enterprise, and you would like to change the theme you should use the [setSkin](/docs/set-skin) function instead.

