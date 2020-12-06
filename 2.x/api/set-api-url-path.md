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

The current page is loaded on the URL: <code>www.grocerycrud.com/enterprise/api-and-function-list/setApiUrlPath</code>, however this page is cached and the routes are a bit more complicated than you think. So for this page in order to show the below example, we are using the function <code>setApiUrlPath</code> like this:

<code>$crud-&gt;setApiUrlPath('/demo_set_api_url_path');</code> more specifically the full code is the below:
<pre><code class="language-php">$crud-&gt;setApiUrlPath('/demo_set_api_url_path');
$crud-&gt;setTable('customers');
$crud-&gt;setSubject('Customer', 'Customers');
$crud-&gt;fields(['customerName','phone','addressLine1','creditLimit']);

$output = $crud-&gt;render();</code></pre>
And this is simply giving the below result. So all the ajax requests are going to: <code>/demo_set_api_url_path</code> instead of <code>/enterprise/api-and-function-list/setApiUrlPath</code>. You can see by your own at the live example:

[demo]demo_set_api_url_path[/demo]