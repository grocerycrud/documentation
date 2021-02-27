---
id: full-example
title: Full Example
description: A full example with the most common functions that are used with Grocery CRUD. 
permalink: docs/full-example
previous: basic-example
next: set-validation-rules
---

# Full Example

Below you can see a full example with the most popular functions that are in use.

<pre><code class="language-php">$crud->setTable('customers')
    ->setSubject('Customer', 'Customers')
    ->columns(['customerName', 'contactLastName', 'phone', 'city', 'country', 'creditLimit'])
    ->displayAs('customerName', 'Name')
    ->displayAs('contactLastName', 'Last Name')
    ->fields(['customerName', 'contactLastName', 'phone', 'city', 'country', 'creditLimit'])
    ->requiredFields(['customerName', 'contactLastName']);

$output = $crud->render();</code></pre>

As you will also notice, we are not repeating the <code>$crud</code> code all the time. Have in mind that all the functions - expect the get functions (e.g. getState) and render - return the CRUD object so you can always extend the line by simply adding the symbol <code>-&gt;</code>. Something like the dot of jQuery in a way!

<strong>displayAs:</strong> is changing the field name to a more readable string. For example instead of "contactLastName" we are replacing it with "Last Name". You are free to add your language translation at the displayAs without any issue

<strong>requiredFields:</strong> It is validating that the fields are not empty. You can check the validation if you try to add a customer without the "Name" or "Last Name"

<strong>fields:</strong> The fields are the fields that will be visible in insert/update/view operations only. Have in mind that these are different from the columns fields.

The below grid is the result of the above code:

`embed:demo_full-example`