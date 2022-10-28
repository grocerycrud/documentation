---
id: unset-settings
title: unsetSettings
description: The method unsetSettings is removing the "Settings" button from the datagrid. 
permalink: docs/unset-settings
previous: unset-filters
next: add-fields
---

# unsetSettings

<pre><code class="language-php">unsetSettings(void)</code></pre>

The method `unsetSettings` is removing the "Settings" button from the datagrid.

## Example

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);
$crud->unsetSettings();

$output = $crud->render();</code></pre>

`embed:demo_unset-settings`
