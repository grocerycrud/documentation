---
id: getting-started
title: Getting Started
description: This page is an overview of Grocery CRUD documentation and related resources.
canonical: docs
previous: 
next: installation
---

# Getting started

Hiya 👋,

Welcome to Grocery CRUD version 3 documentation. Please keep in mind that we are still working on this documentation 
and it is not yet complete. The beta version is still not available for download but very soon it will be available for 
Enterprise users. For more about Grocery CRUD Enterprise version 3 please read the blog post: [Grocery CRUD v3](/blog/grocery-crud-v3)

## Example

Below you can take a taste of how the new version of Grocery CRUD looks like. Since this is still in a beta version, in
case you find any bugs please do let me know on [info@grocerycrud.com](mailto:info@grocerycrud.com)

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();
</code></pre>

You can get the below output:

`embed:demo_getting-started`

## API and function list

You can find the full list of all the functions that you can use from the [API documentation](/v3.x/docs/api-and-functions-list) link
