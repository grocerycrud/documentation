---
id: getting-started
title: Getting Started
permalink: docs
previous: 
next: installation
---

# Getting started

This page is an overview of Grocery CRUD documentation and related resources.

Grocery CRUD is an open source library for Codeigniter 4 that auto generates a full CRUD system. 
The main unique feature of Grocery CRUD is that the CSS and the JavaScript used are production ready.

In simple terms with few PHP lines of codes:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();
</code></pre>

You can get the below output:

`embed:demo_getting-started`

Below you can find pretty much everything you need in order to get started with Grocery CRUD

## Installation
 
[Installation Guide](docs/installation)

[Why Grocery CRUD?](docs/why-grocery-crud)

## Examples

- [Basic Example](docs/basic-example)
- [Full Example](docs/full-example)

## API and function list

You can find the full list of all the functions that you can use from the [API documentation](api-and-functions-list) link
