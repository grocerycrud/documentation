---
id: set-relation
title: setRelation
permalink: docs/set-relation
previous: set-read
next: set-relation-nto-n
---

# setRelation


<pre><code class="php">setRelation(string $fieldName , string $relatedTable, string $relatedTitleField)</code></pre>
A simple database relation between tables is very common. For example if we would like to set a relation for the below tables:

<img src="/assets/uploads/general/relation-example.png" alt="Set Relation tables" />

The primary key of the basic table (employees) and the primary key of the relational table (offices) is recognised automatically . So you need to add only three strings.
<ol>
 	<li>The field name at our basic table that we need to related with the foreign key (in our example: officeCode)</li>
 	<li>The relation table (in our example: offices)</li>
 	<li>The field that it is recognisable as the title of the related table (in our example: city)</li>
</ol>
For example:
<pre><code class="php">$crud-&gt;setRelation('officeCode', 'offices', 'city')</code></pre>

<h2 id="more-than-one">Showing more than one fields</h2>

You can also use multiple fields from the relation table by adding brackets ( <code>{</code> and <code>}</code> ) . For example:

<pre><code class="php">$crud->setRelation('officeCode', 'offices', '{city} - {telephone}');</code></pre>

<h2 id="where-statement">Where statement at the setRelation function</h2>

You can also include a 4th parameter at the setRelation function with the same syntax that is used with <a href="https://www.grocerycrud.com/enterprise/api-and-function-list/where-3"  target="_blank" rel="noopener noreferrer">where</a> function. You can see some examples below:

<pre><code class="php">$crud-&gt;setRelation('officeCode', 'offices', 'city', ['is_deleted' => 'no'])</code></pre>

For more about how to use the 4th parameter of where you can also check the full documentation of <a href="https://www.grocerycrud.com/enterprise/api-and-function-list/where-3" target="_blank" rel="noopener noreferrer">where</a> method.

<h2>Full Example</h2>
A full working example can be found here:
<pre><code class="php">$crud-&gt;setTable('employees');
$crud-&gt;setSubject('Employee', 'Employees');
$crud-&gt;setRelation('officeCode','offices','city');
$crud-&gt;displayAs('officeCode','City');

$output = $crud-&gt;render();</code></pre>
You can see the result of the above code at the below datagrid. As you can see there is a dropdown list at the city (we did rename the officeCode as City to be more readable to the end user)

[demo]demo_set_relation[/demo]