---
id: unset-delete
title: unsetDelete
permalink: docs/unset-delete
previous: unset-columns
next: unset-delete-multiple
---

# unsetDelete


<pre><code class="php">unsetDelete(void)</code></pre>
The method <code>unsetDelete</code> is removing completely the Delete operation for the end-user. More specifically:
<ol>
   <li>It is removing the button "Delete"</li>
   <li>The user doesn't have the ability to Remove any data even if they try to do it by having the URL of the API (e.g. the permission is not allowed)</li>
</ol>

The syntax is simple. You can find an example below:
<pre><code class="php">$crud->unsetDelete();</code></pre>

You can also see a full working example:

<pre><code class="php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);
$crud->unsetDelete();

$output = $crud->render();</code></pre>

You can see the results of the above example here. As you can see by your own, the operation Delete is completely removed:

[demo]demo_unset_delete[/demo]