---
id: required-edit-fields
title: requiredEditFields
description: A validation specific to the update form, ensuring that the user-provided field for our CRUD is not empty during the update operation.
canonical: docs/required-edit-fields
previous: required-add-fields
next: set-edit
---

# requiredEditFields

<pre><code class="language-php">requiredEditFields(array $fields)</code></pre>
The `requiredEditFields` method is an extension of the `requiredFields` method, tailored for the update form. It verifies that the user has filled in certain fields during the update operation.

`requiredEditFields` allows you to designate fields that are obligatory only when modifying existing entries. This method provides the following benefits:

1. A star is shown next to the field name, signifying that it is mandatory when updating an entry.
2. Client-side validation is conducted, prompting the user to complete the required field before the data is transmitted to the server.
3. Server-side validation is also available, acting as a safety net if the client-side validation is circumvented for any reason.

Its usage is simple. Just pass an array of the database field names that are required for the update form. For example:

<pre><code class="language-php">$crud->requiredEditFields(['first_name', 'last_name'])</code></pre>

Here's a comprehensive example:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);
$crud->displayAs('customerName', 'Name');
$crud->displayAs('contactLastName', 'Last Name');

$crud->requiredEditFields(['customerName', 'contactLastName', 'contactFirstName']);

$output = $crud->render();</code></pre>

In this example, if you try to update a customer without providing values for 'customerName', 'contactLastName', or 'contactFirstName', the form will alert you to fill in these fields.

`embed:demo_required-edit-fields`