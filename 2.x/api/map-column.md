---
id: map-column
title: mapColumn
description: Map a column field name with another. Useful for field names that doesn't exist within the database.
permalink: docs/map-column
previous: callback-column
next: default-ordering
enterprise: 1
---

# mapColumn

<pre><code class="language-php">mapColumn(string $columnName, string $mapColumnName)</code></pre>

⚠️ Documentation in progress ⚠️

<pre><code class="language-php">$crud->mapColumn('customer_name', 'full_name');</code></pre>

The most common case to use the mapColumn is with the combination of callbackColumn when the field doesn't exist.

## Example

<pre><code class="language-php">$crud->columns(['full_name','phone','addressLine1','creditLimit']);
$crud->fieldTypeColumn('full_name', 'varchar');
$crud->mapColumn('customerName', 'full_name');
$crud->callbackColumn('full_name', function ($value, $row) {
    return "<div style='background:red'>$value</div>";
});

$output = $crud->render();</code></pre>
