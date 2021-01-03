---
id: set-api-url-path
title: setApiUrlPath
permalink: docs/set-api-url-path
previous: set-add
next: set-clone
---

# setApiUrlPath


<pre><code class="language-php">setApiUrlPath(string $urlPath)</code></pre>
Grocery CRUD by default use the same URL that was initially called. As Grocery CRUD is actually an API at the backend, it is very common to want to change the URL path. For this the usage of <code>setApiUrlPath</code> is required. This functionality also give the opportunity to have the basic page as static and to have the Grocery CRUD Api to a completely different place.

As people may still be confused of what the <code>setApiUrlPath</code> is doing let's have an example.

The current page is loaded on the URL: <code>https://www.grocerycrud.com/docs/set-api-url-path</code>, however this page is cached and the routes are a bit more complicated than you may think! 

In fact our api is served to a different server so the function `setApiUrlPath` is crucial to see all the examples that we have on our website 😃

## Example

So for this page specifically we are using the below line:

<pre><code class="language-php">$crud->setApiUrlPath('https://demo.grocerycrud.com/set-api-url-path');</code></pre> 

You can see the full code below:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->fields(['customerName','phone','addressLine1','creditLimit']);

$crud->setApiUrlPath('https://demo.grocerycrud.com/set-api-url-path');

$output = $crud->render();</code></pre>

So all the ajax API requests are going to: <code>https://demo.grocerycrud.com/set-api-url-path</code> instead of <code>https://www.grocerycrud.com/docs/set-api-url-path</code> that would be the default one.

You can see the results of the above code here:

`embed:demo_set-api-url-path`