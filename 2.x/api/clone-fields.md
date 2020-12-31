---
id: clone-fields
title: cloneFields
permalink: docs/gcc/2.x/clone-fields
previous: callback-clone-field
next: set-clone
---

# cloneFields
<pre><code class="language-php">cloneFields(array $cloneFields)</code></pre>
The fields that will be visible to the end user for Clone form. For example:
<pre><code class="language-php">$crud-&gt;cloneFields(['first_name', 'last_name', 'fullname', 'address'])</code></pre>
You can see a full working example below:
<pre><code class="language-php">$crud-&gt;setTable('customers');
$crud-&gt;setSubject('Customer', 'Customers');

$crud-&gt;setClone();
$crud-&gt;cloneFields(['customerName','phone','addressLine1','creditLimit']);

$output = $crud-&gt;render();</code></pre>
You can see the result of the above code below.The main difference that you will notice is that when you will press the "Clone customer" button at any row. The fields are less when you clone one (these are the fields that was specified at the cloneFields functions). You can simply compare the differences by also trying to press the "Add customer" button and see all the existing fields.

`embed:demo_clone-fields`