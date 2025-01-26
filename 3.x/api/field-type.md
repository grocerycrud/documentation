---
id: field-type
title: fieldType
description: Changing the default field type from the database to fit to our needs. 
canonical: docs/field-type
previous:
next: field-type-add-form
---

# fieldType

<pre><code class="language-php">fieldType(string $fieldName, string|ModelFieldType $fieldType[, array $permittedValues[, array $options]])</code></pre>

The are many cases that the default field type of the database is not the required or that the field type is a simple varchar although we need to have a specific type for add/edit/view. In that case you can use the function <code>fieldType</code> to force the field as that kind of type. Have in mind that this function was renamed from <code>changeFieldType </code>for simplicity.

Below you can see some examples of how you can use the <code>fieldType</code> function:

<strong>Example 1:</strong>
<pre><code class="language-php">$crud->fieldType('website_url', GroceryCrud::FIELD_TYPE_URL);</code></pre>

<strong>Example 2:</strong>
<pre><code class="language-php">$crud->fieldType('website_url', 'url');</code></pre>

<strong>Example 3:</strong> 
<pre><code class="language-php">
// At the beginning of the file
use GroceryCrud\Core\Model\ModelFieldType;
...
$myField = new ModelFieldType();
$myField->setDataType(GroceryCrud::FIELD_TYPE_NUMERIC);
$crud->fieldType('date_birth_year', $myField);</code></pre>

You can find all the types that exists from grocery crud by typing <code>GroceryCrud:FIELD_</code> if you are using an editor that it is recognizing the field types then you should see all the list of available fields. To make things more simple to you we have the full list (that will be always up to date) in case you need to copy-paste it really fast. Although it is strongly suggested to use the constants of GroceryCrud class for that:

<pre><code class="language-php">'boolean'
'color'
'date'
'datetime'
'dropdown'
'dropdown_search'
'email'
'enum'
'enum_searchable'
'float' 
'hidden'
'int'
'invisible'
'multiselect_native' 
'multiselect_searchable' 
'native_date'
'native_datetime'
'native_time' 
'numeric'
'password'
'password_toggle'
'relational_native'
'string'
'text' 
'timestamp'
'url'
</code></pre>

<h2>Examples</h2>

<div>

<h3 id="boolean">boolean</h3>

<p>Input type for boolean (0 or 1) values.</p>

<p>Code example:</p>

<pre class="language-php"><code class="language-php">$crud-&gt;fieldType('field_name', 'boolean');</code></pre>

<p>Preview:</p>

<!-- Code will be replaced by the actual demo preview -->
<div class="form-check form-switch">
    <input name="boolean" class="form-check-input" type="checkbox" role="switch" value="1" checked="">
</div>

<br/>

<h3 id="color">color</h3>

<p>Input type for HEX color values.</p>

<p>Code example:</p>

<pre class="language-php"><code class="language-php">$crud-&gt;fieldType('field_name', 'color');</code></pre>

<p>Preview:</p>

<!-- Code will be replaced by the actual demo preview -->
<input type="color" name="color" value="#ff0000">

<br/><br/>
<h3 id="enum">enum</h3>

<p>Input dropdown list with predefined options. The main difference with `dropdown` is that the values of the arrays are also the ones that will be used as keys into the dropdown list.</p>

<p>Code example:</p>

<pre class="language-php"><code class="language-php">$crud-&gt;fieldType('field_name', 'enum', ['Option 1', 'Option 2', 'Option 3', 'Option 4']);</code></pre>

<p>Preview:</p>

<!-- Code will be replaced by the actual demo preview -->
<select name="enum" class="form-control form-select">
    <option value="Option 1">Option 1</option>
    <option value="Option 2">Option 2</option>
    <option value="Option 3">Option 3</option>
    <option value="Option 4">Option 4</option>
</select>
<br/>
</div>

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




 