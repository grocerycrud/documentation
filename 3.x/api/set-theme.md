---
id: set-theme
title: setTheme
description: 
canonical: docs/set-theme
previous: set-texteditor
next: set-theme-path
---

# setTheme

<pre><code class="language-php">setTheme(string $theme)</code></pre>
The `setTheme` function in Grocery CRUD enables you to customize the visual theme of your CRUD interface. 
As of now, Grocery CRUD offers only two themes, but we have plans to introduce more themes in the future.
Please note that a theme involves the entire HTML, JS, and CSS structure, not just color changes. 
The syntax for using this function is straightforward:

<pre><code class="language-php">$crud->setTheme('myTheme')</code></pre>

You have the option to select from two available themes:

- bootstrap-v4
- bootstrap-v5 (default)

In the future (but it is too early to give any roadmap) we would like to introduce 3 more themes:
- grocery-crud-v3 (a theme based on bootstrap but customized)
- materialize-v1 (a theme based on Materialize UI version 1)
- tailwind-v3 (a theme based on Tailwind CSS version 3)

## Example

<pre><code class="language-php">$crud->setTheme('bootstrap-v4');
$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);</code></pre>

