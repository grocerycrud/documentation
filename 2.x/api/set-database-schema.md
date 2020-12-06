---
id: set-database-schema
title: setDatabaseSchema
permalink: docs/set-database-schema
previous: set-csrf-token-value
next: set-delete
---

# setDatabaseSchema


<pre><code class="php">setDatabaseSchema(string $databaseSchema)</code></pre>
Set the database schema (currently only tested on PostgresSQL databases)

<pre><code class="php">$crud->setDatabaseSchema('example_schema');</code></pre>

Example:

<pre><code class="php">$crud->setDatabaseSchema('example_schema');
$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);</code></pre>