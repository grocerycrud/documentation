---
id: full-page-redirection
title: Full Page Redirection
description: 
permalink: docs/full-page-redirection
previous: 
next:
---

# Full Page Redirection

There are cases that we would like a full URL redirect right after an operation.

A very common example is when we would like to refresh our datagrid after an edit operation. 

Fortunately this is possible when we are using callbacks with Grocery CRUD `RedirectResponse` class.

For example let's say that we would like to redirect with a full page redirect after the insert.
In order to do that you can use the following:

<pre><code class="language-php">$crud->callbackAfterInsert(function ($stateParameters) {
    $redirectResponse = new \GroceryCrud\Core\Redirect\RedirectResponse();
    return $redirectResponse->setUrl('http://localhost/examples/customers.php#/edit/' . $stateParameters->insertId);
});
</code></pre>

As you can also see from the above example we return the `RedirectResponse` as a return value. 
With this, you are forcing your CRUD to have a full redirection of the page with the specified 
URL that you set with `setUrl`.

The `RedirectResponse` class as a return value is available to the following functions:

- `callbackAfterInsert`
- `callbackAfterUpdate`
- `callbackAfterDelete`
- `callbackAfterUpload`
- `callbackInsert`
- `callbackUpdate`
- `callbackDelete`
- `callbackUpload`
- `callbackBeforeInsert`
- `callbackBeforeUpdate`
- `callbackBeforeDelete`
- `callbackBeforeUpload`

We strongly recommend to use `RedirectResponse` only the `after` callbacks to make sure that the 
operation has been completed first.





