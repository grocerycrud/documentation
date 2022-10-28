---
id: callback-column
title: callbackColumn
description: This callback runs on each datagrid column. It escapes the auto column value and runs the callback. 
permalink: docs/callback-column
previous: columns
next: default-ordering
---

# callbackColumn

<pre><code class="language-php">callbackColumn(string $columnName, callable $callback)</code></pre>
The method <code>callbackColumn</code> is the transformation of the data for a column at the datagrid. You will need to specify the column name and then the callback for that column name. The callback then will have two parameters:
<ol>
 	<li>The value of the column</li>
 	<li>The whole row as an object. In simple words you have access to any of the data at this row in case you need to combine other parameters at the same row.</li>
</ol>
<strong>Important warning:</strong> Please notice that this transformation is happenning <strong>after</strong> the render so you will need to be careful as the search for this column may not run as you are expecting. So avoid full transformation of the columns. In case you need to create a searchable column, you will need to do that with a <a href="/enterprise/api-and-function-list/setModel">setModel</a> instead.

You can find a simple example for the usage of the callback column:
<pre><code class="language-php">$crud-&gt;callbackColumn('menu_title', function ($value, $row) {
    return "&lt;a href='" . site_url('menu/' . $row-&gt;id) . "'&gt;$value&lt;/a&gt;";
});</code></pre>


## Invisible field

There are many cases that we would like to use a field from the `$row` object from a field that is not on the datagrid. 
On Grocery CRUD Enterprise edition for security and performance reasons we have removed any unused fields from the 
datagrid so if you would like to have an extra field value to use you should use the `invisible` fieldType. 
To make it even more specific you could specify that this field is invisible only on the datagrid column. 

So for example let's say that we would like to use the column `profile_url` although we don't want to show it to the end
user. In that case you should add it to the `columns` function but it will never be shown. With this way this will be 
used by the callback `callbackColumn`. Let's see a more specific example:

<pre><code class="language-php">$crud-&gt;setTable('customers');
$crud-&gt;setSubject('Customer', 'Customers');
$crud-&gt;columns(['customerName','phone','addressLine1','creditLimit', 'profile_url']);

// With the below line the `profile_url` is not visible at the datagrid from the end user
$crud->fieldTypeColumn('profile_url', 'invisible');

$crud-&gt;callbackColumn('customerName', function ($value, $row) {
    // $row-&gt;profile_url is now available as invisible field
    return "&lt;a href='" . site_url('menu/' . $row-&gt;profile_url) . "'&gt;$value&lt;/a&gt;";
});

$output = $crud-&gt;render();</code></pre>

## Example
A full example of a standard implementation is also available below:
<pre><code class="language-php">$crud-&gt;setTable('customers');
$crud-&gt;setSubject('Customer', 'Customers');
$crud-&gt;columns(['customerName','phone','addressLine1','creditLimit']);

$crud-&gt;callbackColumn('customerName', function ($value, $row) {
    if (!empty($value)) {
        return "&lt;a href='/demo_view_customer/" . $row-&gt;customerNumber."' target='blank'&gt;$value&lt;/a&gt;";
    } else {
        // Make sure that you return white space or else the cell may break on print layout
        return '&amp;nbsp;';
    }
});

$output = $crud-&gt;render();</code></pre>
As you will notice the data for the column <code>customerName</code> are links to a profile page that opens in new tab. The search is working as expected as the actual value is not changing.

`embed:demo_callback-column`