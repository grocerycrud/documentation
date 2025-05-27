---
id: unset-back-to-list
title: unsetBackToList
description: Remove the "Back to List" button from form operations.
canonical: docs/unset-back-to-list
previous: unset-action-button
next: unset-list
---

# unsetBackToList

<pre><code class="language-php">unsetBackToList(void)</code></pre>
The method <code>unsetBackToList</code> removes the "Back to List" button from form operations such as "Close" or 
"Close modal on save" options. This is useful when you want to create standalone forms or when you want to restrict 
navigation back to the list view.

The syntax is simple:
<pre><code class="language-php">$crud->unsetBackToList();</code></pre>

This function is often used in combination with `unsetList()` when you want to create forms that don't provide access to the datagrid view.

<h2>Full example with standalone form</h2>

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');

// Create a standalone form by removing list operations
$crud->unsetBackToList();
$crud->unsetList();

$output = $crud->render();</code></pre>

The result is a form that operates independently without any connection to a datagrid view.

`embed:demo_unset-back-to-list`