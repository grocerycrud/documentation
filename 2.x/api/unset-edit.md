---
id: unset-edit
title: unsetEdit
permalink: docs/unset-edit
previous: unset-delete-multiple
next: unset-edit-fields
---

# unsetEdit


<pre><code class="language-php">unsetEdit(void)</code></pre>
The method <code>unsetEdit</code> is removing completely the Edit operation for the end-user. More specifically:
<ol>
   <li>It is removing the button "Edit"</li>
   <li>The user doesn't have the ability to Update any data even if they try to do it by having the URL of the API (e.g. the permission is not allowed)</li>
</ol>

The syntax is simple. You can find an example below:
<pre><code class="language-php">$crud->unsetEdit();</code></pre>

You can also see a full working example:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);
$crud->unsetEdit();

$output = $crud->render();</code></pre>

You can see the results of the above example here. As you can see by your own, the operation Edit is completely removed:

`embed:demo_unset-edit`