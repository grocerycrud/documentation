---
id: unset-delete-multiple
title: unsetDeleteMultiple
description: 
permalink: docs/unset-delete-multiple
previous: unset-delete
next: unset-edit
---

# unsetDeleteMultiple


<pre><code class="language-php">unsetDelete(void)</code></pre>
The method <code>unsetDeleteMultiple</code> is removing completely the multiple Delete operation for the end-user. This is mainly a function that it is used when you don't want the user to have the ability to batch remove too many records at once. Have in mind that the user <strong>can</strong> remove rows one by one (even all of them!) but by removing this functionality it is just that you don't make it as easy to do and at the same time prevent them to do it.

More specifically:
<ol>
   <li>It is removing the button "Delete" when it comes to multiple deletion</li>
   <li>It is removing the button checkboxes at the left so the user will not be confused</li>
   <li>The user doesn't have the ability to Remove multiple data even if they try to do it by having the URL of the API (e.g. the permission is not allowed)</li>
</ol>

The syntax is simple. You can find an example below:
<pre><code class="language-php">$crud->unsetDeleteMultiple();</code></pre>

You can also see a full working example:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);
$crud->unsetDeleteMultiple();

$output = $crud->render();</code></pre>

You can see the results of the above example here. As you can see by your own, the operation multiple Delete is completely removed:

`embed:demo_unset-delete-multiple`