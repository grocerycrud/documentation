---
id: unset-clone
title: unsetClone
permalink: docs/unset-clone
previous: unset-bootstrap
next: unset-clone-fields
---

# unsetClone


<pre><code class="language-php">unsetClone(void)</code></pre>
The method <code>unsetClone</code> is removing completely the Clone operation for the end-user. More specifically:
<ol>
   <li>It is removing the button "Clone" from the datagrid</li>
   <li>The user doesn't have the ability to Clone any data even if they try to do it by having the URL of the API (e.g. the permission is not allowed)</li>
</ol>

The syntax is simple. You can find an example below:
<pre><code class="language-php">$crud->unsetClone();</code></pre>

<strong>Important notice:</strong> As you probably already noticed, the operation clone is removed by <strong>default</strong>. So this function is probably more rare to be used. However a usage of the unsetClone is in case you need to have role based data in your admin. For example:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);
$crud->setClone();

// This will probably be in a different method but for now we are
// keeping it simple to understand the example
if (user_not_allowed_for_clone()) {
    $crud->unsetClone();
}

$output = $crud->render();</code></pre>

## Example

Below we have an example of setting and then right after unsetting the clone just to see that it will work:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

// It doesn't make much sense to do that but for the sake of the example...
$crud->setClone();
$crud->unsetClone();

$output = $crud->render();</code></pre>

Below you can see the results of the above code:
`embed:demo_unset-clone`

