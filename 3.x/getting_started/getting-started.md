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

Welcome to Grocery CRUD version 3 documentation. Please keep in mind that we are still working on this documentation, 
and it is not yet complete. The beta version is now available to be downloaded for Enterprise users and the instructions
of how to install it are available in the [Installation](/v3.x/docs/grocery-crud-enterprise-installation) page.

For more about Grocery CRUD Enterprise version 3 please read the blog post:

<div class="blog-posts">
    <div class="blog-post">
                    <div class="blog-post-image-container">
                        <a href="/blog/grocery-crud-version-3-stable" title="Grocery CRUD version 3 stable">
                                                            <div class="blog-post__image" style="background-image: url('/uploads/blog/thumb_zachary-nelson-98Elr-LIvD8-unsplash.png');"></div>
                                                    </a>
                    </div>
                    <div class="blog-post-description-container">
                        <a href="/blog/grocery-crud-version-3-stable">
                            <h2>Grocery CRUD version 3 stable</h2>
                        </a>
                        <p>We are glad to announce you that the Grocery CRUD version 3 is now stable! This is a major release with a lot of new UI improvements and a better installation process.</p>
                        <p>Mar 25, 2023 by <a href="/credits">John Skoubourdis</a></p>
                    </div>
    </div>
</div>

<div id="example"><h2><a href="#example">Example</a></h2></div>

Below you can take a taste of how the new version of Grocery CRUD looks like. Since this is still in a beta version, in
case you find any bugs please do let me know on [info@grocerycrud.com](mailto:info@grocerycrud.com)

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();
</code></pre>

`embed:demo_getting-started`

## API and function list

You can find the full list of all the functions that you can use from the [API documentation](/v3.x/docs/api-and-functions-list) link
