---
id: set-database-schema
title: setDatabaseSchema
description: Set database schema for PostgresSQL databases.
canonical: docs/set-database-schema
previous: set-csrf-token-value
next: set-dependent-relation
---

# setDatabaseSchema

<pre><code class="language-php">setDatabaseSchema(string $databaseSchema)</code></pre>
Set database schema for PostgresSQL databases.

<pre><code class="language-php">$crud->setDatabaseSchema('example_schema');</code></pre>

Example:

<pre><code class="language-php">$crud->setDatabaseSchema('example_schema');
$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);</code></pre>