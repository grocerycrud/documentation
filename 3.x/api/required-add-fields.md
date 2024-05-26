---
id: required-add-fields
title: requiredAddFields
description: A validation specific to the insert form, ensuring that the user-provided field for our CRUD is not empty.
canonical: docs/required-add-fields
previous: required-fields
next: set-add
---

# requiredAddFields

<pre><code class="language-php">requiredAddFields(array $fields)</code></pre>
The `requiredAddFields` method is a specialized version of the `requiredFields` method, designed specifically for the 
insert form. It checks whether the user has provided values for certain fields during the insert operation.

By using `requiredAddFields`, you can specify fields that are mandatory only when adding new entries. 
This method offers the following features:

1. An asterisk is displayed next to the field name, indicating that it is required when adding a new entry.
2. Client-side validation is performed, alerting the user to fill in the required field before the data is sent to the server.
3. Server-side validation is also in place, serving as a fallback if the client-side validation is bypassed for any reason.

The usage is straightforward. Simply pass an array of the database field names that are required for the insert form. For instance:

<pre><code class="language-php">$crud->requiredAddFields(['first_name', 'last_name'])</code></pre>

Here's a complete example:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->requiredAddFields(['customerName', 'contactLastName', 'contactFirstName']);

$output = $crud->render();</code></pre>

In this example, if you attempt to add a new customer without providing values for 'customerName', 'contactLastName', 
or 'contactFirstName', the form will prompt you to fill in these fields.

`embed:demo_required-add-fields`