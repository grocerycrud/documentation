---
id: set-config
title: setConfig
permalink: docs/set-config
previous: set-clone
next: set-csrf-token-name
---

# setConfig


<pre><code class="php">setConfig(string $configName, mixed $configValue)</code></pre>
Quickly set a configuration name that will be specific for your CRUD. Really useful for some CRUD that have slightly different configurations than the generic configurations.

<h2>Example:</h2>

<pre><code class="php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');

// Example: Disable backend cache only for customers CRUD as 
// we are still not sure which structure the database will have
$crud->setConfig('backend_cache', false);

$output = $crud->render();</code></pre>
