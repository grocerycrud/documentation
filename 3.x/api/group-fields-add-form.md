---
id: group-fields-add-form
title: groupFields for Add Form
description: Group fields as tabs in the add form only.
canonical: docs/group-fields-add-form
previous: required-fields
next: unset-fields
---

# groupFieldsAddForm

<pre><code class="language-php">groupFieldsAddForm(string|array $displayAs[, array $fields])</code></pre>

 Same as [group-fields](/docs/group-fields) but for the add form only.

Example:

<pre><code class="language-php">$crud->groupFieldsAddForm("PersonalInfo", ['first_name', 'last_name', 'email']);
$crud->groupFieldsAddForm("Address", ['address', 'city', 'state', 'zip_code']);
$crud->groupFieldsAddForm("Other", ['phone', 'notes']);
</code></pre>

or you can group them all at once:

<pre><code class="language-php">$crud->groupFieldsAddForm([
    'Personal Info' => ['first_name', 'last_name', 'email'],
    'Address' => ['address', 'city', 'state', 'zip_code'],
    'Other' => ['phone', 'notes']
]);</code></pre>

You can find a fully working example below:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->setRead();

$crud->groupFieldsEditForm([
    'Personal Info' => ['customerName', 'contactLastName', 'contactFirstName'],
    'Address' => ['addressLine1', 'addressLine2', 'city', 'state', 'postalCode', 'country'],
]);
// The add form now have one tab more with more fields
$crud->groupFieldsAddForm([
    'Personal Info' => ['customerName', 'contactLastName', 'contactFirstName'],
    'Address' => ['addressLine1', 'addressLine2', 'city', 'state', 'postalCode', 'country'],
    'Other' => ['salesRepEmployeeNumber', 'creditLimit']
]);

$output = $crud->render();</code></pre>