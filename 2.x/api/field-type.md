---
id: field-type
title: fieldType
description: Changing the default field type from the database to fit to our needs. 
permalink: docs/field-type
previous:
next: field-type-add-form
---

# fieldType

<pre><code class="language-php">fieldType(string $fieldName, string $fieldType[, array $permittedValues[, array $options]])</code></pre>

The are many cases that the default field type of the database is not the required or that the field type is a simple varchar although we need to have a specific type for add/edit/view. In that case you can use the function <code>fieldType</code> to force the field as that kind of type. Have in mind that this function was renamed from <code>changeFieldType </code>for simplicity.

Below you can see an example:
<pre><code class="language-php">$crud->fieldType('website_url', GroceryCrud::FIELD_TYPE_URL);</code></pre>

or:

<pre><code class="language-php">$crud->fieldType('website_url', 'url');</code></pre>

You can find all the types that exists from grocery crud by typing <code>GroceryCrud:FIELD_</code> if you are using an editor that it is recognizing the field types then you should see all the list of available fields. To make things more simple to you we have the full list (that will be always up to date) in case you need to copy-paste it really fast. Although it is strongly suggested to use the constants of GroceryCrud class for that:

<pre><code class="language-php">'string' //default
'text' 
'date'
'enum'
'enum_searchable'
'datetime'
'hidden'
'timestamp'
'int'
'password'
'numeric'
'checkbox_boolean'
'url'
'email'
'color'
'dropdown'
'dropdown_search' // version 2.3.0 or later
'relational_native' // version 2.3.0 or later
'multiselect_searchable' // version 2.3.4 or later
'multiselect_native' // version 2.3.4 or later
'float' // version 2.7.1 or later
'time' // version 2.7.4 or later
'invisible' // version 2.8.0 or later
</code></pre>

<h2>Examples</h2>

<h3 id="float">float</h3>

In order to change the field type into a float number is as simple as one line of code:

<pre><code class="language-php">$crud->fieldType('total_distance', 'float');</code></pre>


<h3 id="dropdown_search">dropdown_search</h3>
A dropdown list that it is also searchable.

<pre><code class="language-php">// Example by referring to a database id (e.g.12,13, 14... e.t.c.)
$crud->fieldType('contact_title', 'dropdown_search', [
    '12' => 'Master',
    '13' => 'Mr',
    '14' => 'Miss',
    '15' => 'Mrs',
    '16' => 'Missus',
    '17' => 'Ms',
    '18' => 'Mx'
]);</code></pre>

<pre><code class="language-php">// Example by adding the actual value
$crud->fieldType('contact_title', 'dropdown_search', [
    'Master' => 'Master',
    'Mr' => 'Mr',
    'Miss' => 'Miss',
    'Mrs' => 'Mrs',
    'Missus' => 'Missus',
    'Ms' => 'Ms',
    'Mx' => 'Mx'
]);</code></pre>


<h3>multiselect_native</h3>
A multiselect HTML field. More specifically the native &lt;select multiple="multiple"&gt; On insert and update, all the values are inserted to the same field separated by comma.

<pre><code class="language-php">$crud->fieldType('gift_category', 'multiselect_native', [
    'baby' => 'Baby',
    'beauty' => 'Beauty',
    'stripbooks' => 'Books',
    'automotive' => 'Car & Motorbike',
    'popular' => 'CDs & Vinyl',
    'classical' => 'Classical Music',
    'clothing' => 'Clothing',
    'computers' => 'Computers & Accessories',
    'outdoor' => 'Garden & Outdoors',
    'gift-cards' => 'Gift Cards'
]);</code></pre>

<h3>multiselect_searchable</h3>
A multiselect field with the ability to search. On insert and update, all the values are inserted to the same field separated by comma.

<pre><code class="language-php">$crud->fieldType('gift_category', 'multiselect_searchable', [
    'baby' => 'Baby',
    'beauty' => 'Beauty',
    'stripbooks' => 'Books',
    'automotive' => 'Car & Motorbike',
    'popular' => 'CDs & Vinyl',
    'classical' => 'Classical Music',
    'clothing' => 'Clothing',
    'computers' => 'Computers & Accessories',
    'outdoor' => 'Garden & Outdoors',
    'gift-cards' => 'Gift Cards'
]);</code></pre>

<h3>relational_native</h3>
There are cases that people doesn't like or doesn't need to have a searchable setRelation. As by default however the selection is searchable (most common usage is with a search) we did create a different field type that we can easy switch the setRelation to a <a href="https://www.w3schools.com/tags/tag_select.asp" target="_blank" rel="noopener noreferrer">native select input</a>. With the below example things will be more clear:

<pre><code class="language-php">$crud->setRelation('officeCode', 'offices', 'city');
$crud->fieldType('officeCode', 'relational_native');</code></pre>

The above code will simply transform the select input to a native one.

<h2 id="demo">Full Example with Demo</h2>
You can find a full example below:

<pre><code class="language-php">$crud->setTable('orders');
$crud->setSubject('Order', 'Orders');
$crud->unsetAdd();

$crud->fieldType('orderDate', 'datetime');
$crud->fieldType('requiredDate', 'datetime');
$crud->fieldType('shippedDate', 'datetime');

$crud->setRelation('customerNumber','customers','contactLastName');

$output = $crud->render();</code></pre>

As you will also notice at the below example the fields: 'orderDate', 'requiredDate', 'shippedDate' are now a datetime field. GroceryCRUD is recognizing if the browser is supporting the datetime native input and if not it is falling back to a jQuery plugin (in our case this is the jQuery UI for datetime). You can see the difference by opening the page in chrome and the same page in firefox.

`embed:demo_field-type`




 