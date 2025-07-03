---
id: set-default-state
title: setDefaultState
description:  Sets a custom initial page for CRUD. Replace the default Datagrid page with an edit or view form.
canonical: docs/set-default-state
previous: set-database-schema
next: set-model
---

# setDefaultState

<pre><code class="language-php">setDefaultState(string $stateName[, object $stateParameters])</code></pre>

Sets a custom initial page for our CRUD. This function replaces the default Datagrid page with an edit,add, clone or 
view form. This function is normally used when you want to use Grocery CRUD as a standalone form.

## Available State Names

The `$stateName` parameter accepts the following values:

| State Name | Description                                                                                   |
|------------|-----------------------------------------------------------------------------------------------|
| EditForm   | Opens the edit form for modifying an existing record.                                         |
| ReadForm   | Opens the read-only view form.                                                                |
| CloneForm  | As a standalone form, this is creating a standalone add form with some already existing data. |
| AddForm    | Opens the add form for creating new records.                                                  |


## State Parameters

The `$stateParameters` parameter is required for specific states and should be an object with the following structure:

Properties for `EditForm`, `ReadForm`, and `CloneForm` states:
- `primaryKeyValue` (string): The primary key value of the record to edit, view, or clone

For the AddForm state, you don't need to pass any parameters.

<h2>Example usage:</h2>

<pre><code class="language-php">$crud->setDefaultState('EditForm', (object)[
    'primaryKeyValue' => '216'
]);</code></pre>

and for the AddForm state, you can simply use:

<pre><code class="language-php">$crud->setDefaultState('AddForm');</code></pre>

In order to have a complete standalone form, it is suggested to combine it with
the configuration of `open_in_modal` to be `false` (default is `true`).

<h2>Example:</h2>

See a full working example below with `open_in_modal` set to `false`:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');

$crud->unsetBackToList();
$crud->unsetList();
$crud->setDefaultState('EditForm', (object)[
    'primaryKeyValue' => '175'
]);

$output = $crud->render();</code></pre>

You can see the results of the above example here. As you can see by your own, the operation List is completely removed:

`embed:demo_unset-list`