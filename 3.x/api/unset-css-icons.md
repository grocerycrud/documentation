---
id: unset-css-icons
title: unsetCssIcons
description: 
canonical: docs/unset-css-icons
previous: unset-css-theme
next: unset-css-third-party
---

# unsetCssIcons

<pre><code class="language-php">unsetCssIcons(void)</code></pre>
The `unsetCssIcons` function allows you to remove the CSS call of the icon set that is currently being used. 
Icon sets, such as Font Awesome, provide a collection of icons that can be used in your application's interface.

By using this function, you can remove the CSS related to the icon set, giving you more control over the icons you use 
and how they are styled. 

The function doesn't require any parameters. For instance:
<pre><code class="language-php">$crud->unsetCssIcons();</code></pre>

This will unset the CSS of the current icon set being used.

## Example

Here's an example of using the `unsetCssIcons` function:
<pre><code class="language-php">$crud->setTable('employees');
$crud->setSubject('Employee', 'Employees');
$crud->columns(['firstName', 'lastName', 'position', 'salary']);

$crud->unsetCssIcons();

$output = $crud->render();</code></pre>
