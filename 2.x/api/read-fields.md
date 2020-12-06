---
id: read-fields
title: readFields
permalink: docs/read-fields
previous: get-state-info
next: read-only-add-fields
---

# readFields


<pre><code class="php">readFields(array $readFields)</code></pre>
The fields that will be visible when the end-user navigates to the view form.

For example:
<pre><code class="php">$crud->readFields(['first_name', 'last_name', 'fullname', 'address'])</code></pre>

<strong>Note:</strong> It is important to know that by default the read/view button is hidden. This is mainly for the reason that it is not commonly used. If you want to enable it you will need to simply add the code: <code>$crud->setRead();</code>.

You can find a fully working example below:
<pre><code class="php">$crud->setTable('customers');
$crud->setRead();
$crud->setSubject('Customer', 'Customers');
$crud->readFields(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();</code></pre>

As you will see, only when the button view is pressed (go to any row and press "More" -> "View") the fields are less than when we press "Add" or "Edit". When the View form is opened then only the fields that are mentioned at the readFields function are visible.
[demo]demo_read_fields[/demo]