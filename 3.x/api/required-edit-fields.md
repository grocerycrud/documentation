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
The `requiredEditFields` method is a specialized version of the `requiredFields` method, designed specifically for the update form. It checks whether the user has provided values for certain fields during the update operation.

By using `requiredEditFields`, you can specify fields that are mandatory only when updating existing entries. This method offers the following features:

1. An asterisk is displayed next to the field name, indicating that it is required when updating an entry.
2. Client-side validation is performed, alerting the user to fill in the required field before the data is sent to the server.
3. Server-side validation is also in place, serving as a fallback if the client-side validation is bypassed for any reason.

The usage is straightforward. Simply pass an array of the database field names that are required for the update form. For instance:

<pre><code class="language-php">$crud->requiredEditFields(['first_name', 'last_name'])</code></pre>

Here's a complete example:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);
$crud->displayAs('customerName', 'Name');
$crud->displayAs('contactLastName', 'Last Name');

$crud->requiredEditFields(['customerName', 'contactLastName', 'contactFirstName']);

$output = $crud->render();</code></pre>

In this example, if you attempt to update a customer without providing values for 'customerName', 'contactLastName', or 'contactFirstName', the form will prompt you to fill in these fields.

`embed:demo_required-edit-fields`