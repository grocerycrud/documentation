---
id: set-relation-1-to-1
title: setRelation1to1
description: Method to connect two tables with a 1 to 1 (1:1) relation.
canonical: docs/set-relation-1-to-1
previous: set-primary-key
next: set-relation
---

# setRelation1to1

<pre><code class="language-php">setRelation1to1(string $relationFieldName, string $relatedTable, array $relatedTableFields)</code></pre>

At relational databases it is very common to have 1 to 1 relationship (also known as 1:1). 
Grocery CRUD is doing it easy for you to connect 2 tables and also use 
it in your datagrid and forms. 
The syntax is easy, and you just need to add the tables and the relations. 
All the primary keys are automatically added so you will not need to add them.

<div style="text-align: center">
    <img src="/uploads/documentation/set-relation-1-to-1.png" alt="Set Database Relation 1 to 1" />
</div>

For example:

<pre><code class="language-php">$crud->setRelation1to1('address_id', 'address', [
    'address', 'address2','district', 'city_id','postal_code', 'phone'
]);</code></pre>

Full working example can be found below:

<pre><code class="language-php">$crud->setSubject('Employee', 'Employees');
$crud->setTable('employees');

$crud->setRelation1to1('address_id', 'employees_addresses', [
    'address_line_1','city','address_line_2','postal_code','country'
]);

$crud->fields([
     'lastName', 'firstName', 'extension',
    'country', 'city',  'address_line_1', 'address_line_2', 'postal_code',
    'email', 'officeCode',
    'file_url', 'jobTitle'
]);

$crud->columns([
    'employeeNumber', 'lastName', 'firstName', 'extension',
    'country', 'city',  'address_line_1', 'address_line_2', 'postal_code',
    'email', 'officeCode',
    'file_url', 'jobTitle'
]);

$crud->setClone();
$crud->groupFields('Basic Information', ['employeeNumber', 'lastName', 'firstName', 'extension', 'email', 'officeCode', 'jobTitle', 'file_url']);
$crud->groupFields('Address', ['country', 'city', 'address_line_1', 'address_line_2', 'postal_code']);

$crud->setRelation('country', 'countries', 'nicename');

$output = $crud->render();</code></pre>