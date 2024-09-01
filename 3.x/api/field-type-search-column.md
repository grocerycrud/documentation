---
id: field-type-search-column
title: fieldTypeSearchColumn
description: The function fieldTypeSearchColumn is utilized to modify the field type specifically for the search column in the datagrid.
canonical: docs/field-type-search-column
previous: field-type-column
next: field-type-edit-form
---

# fieldTypeSearchColumn

<pre><code class="language-php">fieldTypeSearchColumn(string $columnName, string|ModelFieldType $fieldType[, array $permittedValues[, array $options]])</code></pre>
This function is designed for scenarios where you need to alter the field type exclusively for the search column. 
You can select any field type from the <a href="https://www.grocerycrud.com/enterprise/api-and-function-list/fieldType">list of field types</a>.

<h2>Example</h2>

A common scenario is when you want to use `callbackColumn` to customize the display of a column while setting the field type only for the search input.

To achieve this, you can use the following example:
<pre><code class="language-php">$crud-&gt;callbackColumn('search_datetime', function ($value, $row) {
    return date('d/m/Y', strtotime($value));
});
$crud-&gt;fieldTypeSearchColumn('search_datetime', GroceryCrud::FIELD_TYPE_DATE);</code></pre>

or:

<pre><code class="language-php">$crud-&gt;callbackColumn('search_datetime', function ($value, $row) {
    return date('d/m/Y', strtotime($value));
});
$crud-&gt;fieldTypeSearchColumn('search_datetime', 'date');</code></pre>

The above examples will customize the display of the `search_datetime` column and set its field type to date only for the search input.

## Example

<pre><code class="language-php">$crud->setTable('orders');
$crud->setSubject('Order', 'Orders');
$crud->unsetAdd();

$crud->fieldType('orderDate', 'datetime');
$crud->fieldType('requiredDate', 'datetime');
$crud->fieldType('shippedDate', 'datetime');

$crud->fieldTypeSearchColumn('orderDate', 'datetime');
$crud->fieldTypeSearchColumn('requiredDate', 'datetime');
$crud->fieldTypeSearchColumn('shippedDate', 'datetime');

$crud->setRelation('customerNumber', 'customers', 'contactLastName');

// Customizing the display of orderDate and setting its field type for the search input
$callbackColumn = function ($value, $row) {
    return date('d M Y', strtotime($value));
};

// Apply the callback function and set the field type for the search input
$crud->callbackColumn('orderDate', $callbackColumn);
$crud->callbackColumn('requiredDate', $callbackColumn);
$crud->callbackColumn('shippedDate', $callbackColumn);

$output = $crud->render();</code></pre>

`embed:demo_field-type-search-column`