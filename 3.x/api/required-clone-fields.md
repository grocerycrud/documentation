---
id: required-clone-fields
title: requiredCloneFields
description: A validation specific to the clone form, ensuring that the user-provided field for our CRUD is not empty during the cloning operation.
canonical: docs/required-clone-fields
previous: required-edit-fields
next: set-clone
---

# requiredCloneFields

<pre><code class="language-php">requiredCloneFields(array $fields)</code></pre>
The `requiredCloneFields` method is a variant of the `requiredFields` method, adapted for the clone form. 
It confirms that the user has populated certain fields during the cloning operation.

`requiredCloneFields` enables you to define fields that are required only when duplicating existing entries. 
This method will show a star next to the field name, indicating that it is obligatory when cloning an entry.

The usage is as simple as passing an array of the database field names that are required for the clone form. For example:

<pre><code class="language-php">$crud->requiredCloneFields(['first_name', 'last_name'])</code></pre>

⚠️ Important: When using `requiredCloneFields`, it's crucial to also use `requiredAddFields` or else server-side 
validation will not work . This is because the clone form, upon pressing the "Save changes" button, performs an 
"Insert" operation. Therefore, to ensure proper validation for clone fields (which are later used to insert data), 
`requiredAddFields` must be used. 

Here's a detailed example:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->displayAs('customerName', 'Name');
$crud->displayAs('contactLastName', 'Last Name');
$crud->setClone();
$crud->unsetDelete();

// In order to make the clone form fields required, we need to use requiredCloneFields and requiredAddFields
$crud->requiredCloneFields(['customerName', 'contactLastName', 'contactFirstName']);
$crud->requiredAddFields(['customerName', 'contactLastName', 'contactFirstName']);

$output = $crud->render();</code></pre>

In this example, if you try to clone a customer without providing values for 'customerName', 'contactLastName', or 'contactFirstName', the form will alert you to fill in these fields.

`embed:demo_required-clone-fields`