---
id: unset-list
title: unsetList
description: Removing the List functionality for the current CRUD. 
canonical: docs/unset-list
previous: unset-search-columns
next: unset-List-pdf
---

# unsetList

<pre><code class="language-php">unsetList(void)</code></pre>
The method <code>unsetList</code> is completely removing the list operation for the end-user. 
This is useful when you want to use standalone forms for your CRUD. The method will also remove the access to the list
operation from the API, meaning that if the user tries to access the list operation, they will not be able to do so.

The syntax is straightforward. You can find an example below:
<pre><code class="language-php">$crud->unsetList();</code></pre>

This function is usually combines with the function `unsetBackToList` to remove the back to list button from the form
operations (such as create or update form).

You can also see a full working example:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');

$crud->unsetBackToList();
$crud->unsetList();

$output = $crud->render();</code></pre>

You can see the results of the above example here. As you can see by your own, the operation List is completely removed:

`embed:demo_unset-List`
