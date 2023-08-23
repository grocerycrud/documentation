---
id: unset-css-theme
title: unsetCssTheme
description: 
canonical: docs/unset-css-theme
previous: unique-fields
next: unset-css-icons
---

# unsetCssTheme

<pre><code class="language-php">unsetCssTheme(void)</code></pre>
The `unsetCssTheme` function is used to remove the CSS call of the current theme being used. 
This is particularly useful when you want to manage the styling of your application yourself, rather than relying on 
the default theme's CSS.

By calling this function, you can unbind the current theme's CSS, which can be especially handy if you intend to apply 
a custom theme or styling to your application.

The function does not require any parameters. For example:
<pre><code class="language-php">$crud->unsetCssTheme();</code></pre>

Keep in mind that this will unset the CSS of the current theme that is in use.

## Example

Here's an example of how you might use the `unsetCssTheme` function:
<pre><code class="language-php">$crud->setTable('products');
$crud->setSubject('Product', 'Products');
$crud->columns(['productName', 'category', 'price']);

$crud->unsetCssTheme();

$output = $crud->render();</code></pre>
