---
id: set-primary-key
title: setPrimaryKey
description: Set manually the primary key for a database table.
canonical: docs/set-primary-key
previous: set-model
next: set-relation
---

# setPrimaryKey

<pre><code class="language-php">setPrimaryKey(string $primaryKey, string $tableName)</code></pre>

Set a custom primary key for a table. The common usage for this function is:
<ol>
	<li>When you need to change the default value of a primary key (e.g. to point to a different field for a join)</li>
        <li>To optimize your queries and to not have an extra query just for the primary key</li>
</ol>

For example, let's say that we have the below tables <strong>orders</strong> and <strong>products</strong> below:
<pre><code>`orders` (
  `id`,
  `user_id`,
  `product_reference_id`,
  `order_date`
)</code></pre>

<pre><code>`products` (
  `id`,
  `reference_id`,
  `name`,
  `description`
)</code></pre>

These two tables has the <em>`id`</em> as a PRIMARY KEY. As you can guess though from the tables, the orders table is linked with products table by the reference_id and not by the product it. In that case if you use the setRelation with the above line of code:

<pre><code class="language-php">$crud->setRelation('product_reference_id', 'products', 'name');</code></pre>

This will join by default with the <em>`products`.`id`</em> rather than the <em>`products`.`reference_id`</em> as by default the primary key of the products table is the <em>`id`</em>. In that case in order to achieve the expected behaviour, you should write the extra line:

<pre><code class="language-php">$crud->setPrimaryKey('reference_id', 'products');
$crud->setRelation('product_reference_id', 'products', 'name');
</code></pre>

