---
id: set-relation
title: setRelation
description: This is the function that is used to connect two tables with a 1 to n (1:n) relation.
canonical: docs/set-relation
previous: set-primary-key
next: set-relation-n-to-n
---

# setRelation

<pre><code class="language-php">setRelation(string $fieldName , string $relatedTable, string $relatedTitleField)</code></pre>
A simple database relation between tables is very common. For example if we would like to set a relation for the below tables:

<img src="/uploads/documentation/relation-example.png" alt="Set Relation tables" />

The primary key of the basic table (employees) and the primary key of the relational table (offices) is recognised automatically . So you need to add only three strings.
<ol>
 	<li>The field name at our basic table that we need to related with the foreign key (in our example: officeCode)</li>
 	<li>The relation table (in our example: offices)</li>
 	<li>The field that it is recognisable as the title of the related table (in our example: city)</li>
</ol>
For example:
<pre><code class="language-php">$crud-&gt;setRelation('officeCode', 'offices', 'city')</code></pre>

<h2 id="more-than-one">Showing more than one fields</h2>

You can also use multiple fields from the relation table by adding brackets ( <code>{</code> and <code>}</code> ) . For example:

<pre><code class="language-php">$crud->setRelation('officeCode', 'offices', '{city} - {telephone}');</code></pre>

<h2 id="where-statement">Where statement at the setRelation function</h2>

You can also include a 4th parameter at the setRelation function with the same syntax that is used with [where](/docs/where) function. You can see some examples below:

<pre><code class="language-php">$crud-&gt;setRelation('officeCode', 'offices', 'city', ['is_deleted' => 'no'])</code></pre>

For more about how to use the 4th parameter of where you can also check the full documentation of [where](/docs/where) method.

## Example

A full working example can be found here:
<pre><code class="language-php">$crud-&gt;setTable('employees');
$crud-&gt;setSubject('Employee', 'Employees');
$crud-&gt;setRelation('officeCode','offices','city');
$crud-&gt;displayAs('officeCode','City');

$output = $crud-&gt;render();</code></pre>
You can see the result of the above code at the below datagrid. As you can see there is a dropdown list at the city (we did rename the officeCode as City to be more readable to the end user)

`embed:demo_set-relation`