---
id: unset-read
title: unsetRead
description: 
permalink: docs/unset-read
previous: unset-react
next: unset-read-fields
---

# unsetRead


<pre><code class="language-php">unsetRead(void)</code></pre>
The method <code>unsetRead</code> is removing completely the Read operation for the end-user. More specifically:
<ol>
   <li>It is removing the button "View"</li>
   <li>The user doesn't have the ability to read data in a form even if they try to do it by having the URL of the API (e.g. the permission is not allowed)</li>
</ol>

The syntax is simple. You can find an example below:
<pre><code class="language-php">$crud->unsetRead();</code></pre>

<strong>Important notice:</strong> As you probably already noticed, the operation read is removed by <strong>default</strong>. So this function is probably more rare to be used. However a usage of the unsetRead is in case you need to have role based data in your admin. For example:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);
$crud->setRead();

// This will probably be in a different method but for now we are
// keeping it simple to understand the example
if (user_not_allowed_for_read()) {
    $crud->unsetRead();
}

$output = $crud->render();</code></pre>

Below we have an example of setting and then right after unsetting the read just to see that it will work:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

// Yeah, I know! It doesn't make much sense to do that but hey!
$crud->setRead();
$crud->unsetRead();

$output = $crud->render();</code></pre>

The result of the above code can be found here:

`embed:demo_unset-read`