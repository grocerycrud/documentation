---
id: callback-column
title: callbackColumn
description: This callback runs on each datagrid column. It escapes the auto column value and runs the callback. 
permalink: docs/callback-column
previous: callback-clone-field
next: callback-delete
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
A full example is also available below:
<pre><code class="language-php">$crud-&gt;setTable('customers');
$crud-&gt;setSubject('Customer', 'Customers');
$crud-&gt;columns(['customerName','phone','addressLine1','creditLimit']);

$crud-&gt;callbackColumn('customerName', function ($value, $row) {
     return "&lt;a href='/demo_view_customer/" . $row-&gt;customerNumber."' target='blank'&gt;$value&lt;/a&gt;";
});

$output = $crud-&gt;render();</code></pre>
As you will notice the data for the column <code>customerName</code> are links to a profile page that opens in new tab. The search is working as expected as the actual value is not changing.

`embed:demo_callback-column`