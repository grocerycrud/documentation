---
id: set-validation-rules
title: Set validation rules
description: Set backend validation rules for extra security of your data with Grocery CRUD. 
canonical: docs/set-validation-rules
previous: full-example
next: set-database-relation
---

# Set validation rules

A common usage of a CRUD is to use validation rules. 
For that reason Grocery CRUD Enterprise is using 
<a href="https://github.com/vlucas/valitron" target="_blank" rel="noopener noreferrer">Valitron</a> for validation. 
For more you can read the full documentation at: [setRule](/docs/set-rule)

## Example

A full example with validations can be found below:
<pre><code class="language-php">$crud->setTable('products');
$crud->setSubject('Product', 'Products');
$crud->columns(['productName', 'buyPrice', 'quantityInStock']);

$crud->displayAs('productName', 'Product');
$crud->displayAs('buyPrice', 'Price');
$crud->displayAs('quantityInStock', 'Quantity');

$crud->setRule('buyPrice', 'numeric');
$crud->setRule('quantityInStock', 'integer');

$output = $crud->render();
</code></pre>

As you can see from the above code, the labels for productName, buyPrice, quantityInStock will change and this will also be the label at the error. For example at the below example try to add a non numeric value as a price. You will see that the error will give you the displayAs label.

`embed:demo_set-validation-rules`