---
id: set-database-relation
title: Set database relation
permalink: docs/set-database-relation
previous: set-validation-rules
next: 
---

# Set database relation

One of the most common database scenario is when a field is related with another table. For example a <code>product_id</code> that is related with a table <code>products</code>. As in real life this is not enough we also need to specify a title or a name for the related database. So basically there are 3 fields that we need to add:


<ol>
	<li>The fieldName of the basic table (for example the field name <code>product_id</code>)</li>
	<li>The table name of the relation (for example <code>products</code>)</li>
	<li>The related table title or name (for example the field name <code>product_name</code>)</li>
</ol>

You can find more about setting a relation from the documentation of <a href="https://www.grocerycrud.com/enterprise/api-and-function-list/setRelation">setRelation</a>.

Now as you probably mentioned, we didn't add any primary key of the related table and this is because Grocery CRUD is doing it automatically for you. If you need to add a different primary key you should use the <a href="/enterprise/api-and-function-list/setPrimaryKey">setPrimaryKey</a> function as well. 

You can see a full working example below:
<pre><code class="language-php">$crud->setTable('employees');
$crud->setSubject('Employee', 'Employees');
$crud->setRelation('officeCode','offices','city');
$crud->displayAs('officeCode','City');

$output = $crud->render();</code></pre>

`embed:demo_set_database_relation`