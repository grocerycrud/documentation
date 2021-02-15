---
id: set-unique-id
title: setUniqueId
description: 
permalink: docs/set-unique-id
previous: set-theme-path
next: unique-fields
---

# setUniqueId


<pre><code class="language-php">setUniqueId(string $uniqueId)</code></pre>
The <code>setUniqueId</code> method is a useful tool to know for client side caching. This is the unique id that you give in order to cache some preferences such as per-page, ordering,... e.t.c. when the user refreshes the page or come back in after a while.

The syntax is simple, you just need to add a unique value (unique to the other tables)

<pre><code class="language-php">$crud->setUniqueId('customers_1234');</code></pre>

By default the uniqueId is auto set by the hash of the URL so you don't have to. However there are cases that the URL is changing although we are referring to the same CRUD. In that case it is suggested to use the <code>setUniqueId</code> method.

Below you can find a full example:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','country','state','addressLine1']);

$crud->setUniqueId('customers_1234');

return $crud->render();</code></pre>

There is not much to see at the bottom example, however you can check your localStorage and see the value of the 'customers_1234'. More specifically, if you are on chrome:
<ol>
        <li>At the example below press the header 'customerName' so you will order by name (and the cache will remember it!)</li> 
	<li>Press right click anywhere at the page and press "Inspect"</li>
        <li>Now that the developers tools are open go to the tab "Application"</li>
        <li>At the left menu press localStorage and search for the website www.grocerycrud.com</li>
        <li>Now you can see that there is a value named <code>'gcrudInitialData_customers_1234'</code> </li>
        <li>Now refresh the page and you will see that the browser "remembers" your last sorting</li>
</ol>
`embed:demo_set-unique-id`