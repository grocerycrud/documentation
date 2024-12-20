---
id: group-fields
title: groupFields
description: Group fields to show them as tabs in the form.
canonical: docs/group-fields
previous: required-fields
next: unset-fields
---

# groupFields

<pre><code class="language-php">groupFields(array $groups)</code></pre>
Group fields to show them as tabs in the form.

For example:
<pre><code class="language-php">$crud->groupFields([
    'Personal Info' => ['first_name', 'last_name', 'email'],
    'Address' => ['address', 'city', 'state', 'zip_code'],
    'Other' => ['phone', 'notes']
]);</code></pre>

<strong>Note:</strong> The keys of the array represent the tab names, and the values are arrays of field names that will be grouped under each tab.

You can find a fully working example below:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->setRead();
$crud->groupFields([
    'Personal Info' => ['customerName', 'contactLastName', 'contactFirstName'],
    'Address' => ['addressLine1', 'addressLine2', 'city', 'state', 'postalCode', 'country'],
    'Other' => ['salesRepEmployeeNumber', 'creditLimit']
]);

$output = $crud->render();</code></pre>

As you will see, when you open an add/edit or read form the fields are grouped into tabs named "Personal Info", "Address", and "Other" in the form.
`embed:demo_group-fields`