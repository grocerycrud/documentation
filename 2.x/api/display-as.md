---
id: display-as
title: displayAs
description: Displaying the field name with a more readable label to the end-user.
permalink: docs/display-as
previous: set-subject
next: set-language
---

# displayAs

<pre><code class="language-php">displayAs(string $fieldName, string $displayAs)</code></pre>
or
<pre><code class="language-php">displayAs(array $displayAsArray)</code></pre>
The displayAs function is used when we would like to change the field name so it can be more readable from the user. The displayAs can also be used for translated strings. 

The display type can be used either by adding 2 string parameters, either by adding an array of values.

For example:
<pre><code class="language-php">$crud->displayAs('address_line_1', 'Address 1');
$crud->displayAs('contact_first_name', 'First Name');
$crud->displayAs('contact_last_name', 'Surname');
</code></pre>

or the exact same with an array:
<pre><code class="language-php">$crud->displayAs(array(
    'address_line_1' => 'Address 1'
    'contact_first_name' => 'First Name',
    'contact_last_name' => 'Surname'
));</code></pre>


You can find a full working example below:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);
$crud->setRead();

$crud->displayAs([
    'customerName'=> 'Customer Name',
    'addressLine1'=> 'Address 1',
    'creditLimit'=> 'Credit Limit',
    'contactLastName' => 'Last Name',
    'contactFirstName'=> 'First Name',
    'addressLine2' => 'Address 2',
    'postalCode' => 'Postal Code',
    'salesRepEmployeeNumber' => 'Employee Number'
]);

$output = $crud->render();</code></pre>

You can see that the fields changed to the columns and also at add/edit/view form. You can see the result of the above code here:

`embed:demo_display-as`
