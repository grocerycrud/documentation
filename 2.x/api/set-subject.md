---
id: set-subject
title: setSubject
description: Set a subject title for all the CRUD operations for this object.
permalink: docs/set-subject
previous: set-table
next: display-as
---

# setSubject

<pre><code class="language-php">setSubject(string $subject [, string $subject_plural])</code></pre>
Set a subject title for all the CRUD operations for this object.

This method is really useful when you want to specify what is the actual subject of your table CRUD. Moreover you don't have to add every time all the strings that the user will see as they are very similar. The default value is "Item" and it is also translatable. It is very easy to set a subject and then this string is reused in almost every message or operation.

For example if we insert as a subject the string "Employee" it will be:
    - instead of "New item" we will have "New employee"
    - instead of "Edit item" we will have "Edit employee"

A good way to add a subject is to add it as a non plural subject. For example: Employee and not Employees, City and not Cities and so on...

Example usage:

<pre><code class="language-php">$crud->setSubject('Film', 'Films');</code></pre>

The subject plural is not required so you can also have something like this:

<pre><code class="language-php">$crud->setSubject('Film');</code></pre>

However it is highly recommended to add the plural of your subject as it may be a good indicator in some cases for your end-user.

## Example

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$output = $crud->render();</code></pre>

with a result:

`embed:demo_set-subject`