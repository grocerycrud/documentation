---
id: clone-fields
title: cloneFields
permalink: docs/gcc/2.x/clone-fields
previous: add-fields
next: replace-state
---

# cloneFields

    cloneFields(array $cloneFields)

The fields that will be visible to the end user for Clone form. For example:

    $crud->cloneFields(['first_name', 'last_name', 'fullname', 'address']);

## Full Example

    $crud->setTable('customers');
    $crud->setSubject('Customer', 'Customers');
    
    $crud->setClone();
    $crud->cloneFields(['customerName','phone','addressLine1','creditLimit']);
    
    $output = $crud->render();

You can see the result of the above code below.The main difference that you will notice is that when you will press the "Clone customer" button at any row. The fields are less when you clone one (these are the fields that was specified at the cloneFields functions). You can simply compare the differences by also trying to press the "Add customer" button and see all the existing fields.

`embed:demo_clone_fields`