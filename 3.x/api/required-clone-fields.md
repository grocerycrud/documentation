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
The `requiredCloneFields` method is a variant of the `requiredFields` method, adapted for the clone form. It confirms that the user has populated certain fields during the cloning operation.

`requiredCloneFields` enables you to define fields that are compulsory only when duplicating existing entries. This method provides the following advantages:

1. A star is displayed next to the field name, indicating that it is obligatory when cloning an entry.
2. Client-side validation is executed, prompting the user to fill in the required field before the data is sent to the server.
   $crud->columns(['customerName','phone','addressLine1','creditLimit']);
   $crud->displayAs('customerName', 'Name');
3. Server-side validation is also implemented, acting as a backup if the client-side validation is bypassed for any reason.

Its usage is uncomplicated. Just pass an array of the database field names that are required for the clone form. For example:

<pre><code class="language-php">$crud->requiredCloneFields(['first_name', 'last_name'])</code></pre>

⚠️ Important: When using `requiredCloneFields`, it's crucial to also use `requiredAddFields`. This is because the 
clone form, upon pressing the "Save changes" button, performs an "Insert" operation. Therefore, to ensure proper validation 
for clone fields (which are later used to insert data), `requiredAddFields` must be used. 

Here's a detailed example:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->displayAs('customerName', 'Name');
$crud->displayAs('contactLastName', 'Last Name');
$crud->setClone();
$crud->unsetDelete();

$crud->requiredCloneFields(['customerName', 'contactLastName', 'contactFirstName']);
$crud->requiredAddFields(['customerName', 'contactLastName', 'contactFirstName']);

$output = $crud->render();</code></pre>

In this example, if you try to clone a customer without providing values for 'customerName', 'contactLastName', or 'contactFirstName', the form will alert you to fill in these fields.

`embed:demo_required-clone-fields`