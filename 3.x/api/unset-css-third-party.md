---
id: unset-css-third-party
title: unsetCssThirdParty
description: 
canonical: docs/unset-css-third-party
previous: unset-css-icons
next: unset-autoload-javascript
---

# unsetCssThirdParty

<pre><code class="language-php">unsetCssThirdParty(void)</code></pre>
The `unsetCssThirdParty` function is used to remove any third-party CSS calls that might be affecting the styling of 
your application. This can include external libraries such as datepicker or other custom CSS components.

By invoking this function, you can effectively detach third-party styling from your application, 
giving you more control over its appearance and preventing potential conflicts.

The function does not require any parameters. For example:
<pre><code class="language-php">$crud->unsetCssThirdParty();</code></pre>

This will unset any third-party CSS calls that might be affecting the styling.

## Example

Here's an example of how you might use the `unsetCssThirdParty` function:
<pre><code class="language-php">$crud->setTable('orders');
$crud->setSubject('Order', 'Orders');
$crud->columns(['orderNumber', 'orderDate', 'status', 'totalAmount']);

$crud->unsetCssThirdParty();

$output = $crud->render();</code></pre>
