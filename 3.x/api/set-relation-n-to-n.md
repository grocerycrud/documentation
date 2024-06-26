---
id: set-relation-n-to-n
title: setRelationNtoN
description: A connection for 3 tables with n-n relation (also known as n:n or m:n).
canonical: docs/set-relation-n-to-n
previous: set-relation
next: set-sequence-name
---

# setRelationNtoN

<pre><code class="language-php">setRelationNtoN(
        string $fieldName,
        string $junctionTable,
        string $referrerTable,
        string  $primaryKeyJunctionToCurrent, 
        string $primaryKeyToReferrerTable, 
        string $referrerTitleField
        [, string $sortingFieldName [, array|string $where, [, string $orderingFieldName]]]
)</code></pre>
At relational databases it is very common to have many to many relationship (also known as n:n or m:n). Grocery CRUD is doing it easy for you to connect 3 tables and also use it in your datagrid and forms. The syntax is easy and you just need to add the tables and the relations. All the primary keys are automatically added so you will not need to. 

<img src="/uploads/documentation/set-relation-n-to-n.png" alt="Set Relation N to N tables" />

For example:

<pre><code class="language-php">$crud->setRelationNtoN('actors', 'film_actor', 'actor', 'film_id', 'actor_id', 'fullname');
$crud->setRelationNtoN('categories', 'film_category', 'category', 'film_id', 'category_id', 'name');</code></pre>

<h2>$referrerTitleField</h2>

The variable <code>$referrerTitleField</code> can also be written with brackets. With this way you can achieve a result to get more than one fields from the title table or create your own type of title. An example in order to understand it better is as follows:

<pre><code class="language-php">$crud->setRelationNtoN('actors', 'film_actor', 'actor', 'film_id', 'actor_id', '{reference_id} - {first_name} {last_name}');</code></pre>

The above example will output strings that will take the fields from <code>actor.reference_id</code>, <code>actor.first_name</code> and <code>actor.last_name</code> . The final output will look like this <code>"345 - John Smith"</code>, <code>"367 - George Brown"</code>,... e.t.c. 

<h2>$where</h2>
The where statement will take the exact same format as <a href="https://www.grocerycrud.com/enterprise/api-and-function-list/where-3" target="_blank">where</a> function of grocery CRUD Enterprise. 

For example a common usage will look like this:

<pre><code class="language-php">$crud->setRelationNtoN('actors', 'film_actor', 'actor', 'film_id', 'actor_id', 'fullname', null, [
     'actor.state' => 'public'
]);</code></pre>

<h2>$sortingFieldName</h2>
The sorting field name is the field that you want to sort the results if you have a field in the database at the 
juction table. You can drag and drop the sorting field in order to sort the results.

For example:

<pre><code class="language-php">$crud->setRelationNtoN(
    'actors', 'film_actor', 
    'actor', 'film_id', 
    'actor_id', 'fullname', 
    null, null, 'priority'
);</code></pre>

## Full example

A full working example can be found below:
<pre><code class="language-php">$crud->setTable('film');
$crud->setSubject('Film', 'Films');

// With the ability to order the results
$crud->setRelationNtoN(
    'actors', 'film_actor',
    'actor', 'film_id',
    'actor_id', 'fullname',
    null, null, 'priority'
);

// Without the ability to order the results
$crud->setRelationNtoN(
    'categories', 'film_category',
    'category', 'film_id',
    'category_id', 'name'
);


$output = $crud->render();</code></pre>

The result of the above code is here. As you can see we now have two new fields (actors and categories) with multiple select functionality.
`embed:demo_set-relation-n-to-n`