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

<h2>Example</h2>

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');

// Although there is no point to have that without the unsetList 
// This is an example of how unsetBackToList will look like.
$crud->unsetBackToList();

$output = $crud->render();</code></pre>

The result of the above example will show modal forms withou the "Back To List" buttons. 
You can see the results at the below demo: Try to open the modal form and press "Save", you will not be redirected back 
to the list view. The only way to return to the list will be to close the modal.

`embed:demo_unset-back-to-list`