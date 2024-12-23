---
id: group-fields
title: groupFields
description: Group fields to show them as tabs in the form.
canonical: docs/group-fields
previous: required-fields
next: unset-fields
---

# groupFields

<pre><code class="language-php">groupFields(string|array $displayAs[, array $fields])</code></pre>
Group fields to show them as tabs in the form. The display of the tabs will look similar to the below screenshot:

<picture>
  <source srcset="/uploads/documentation/api/group-fields-light.png" media="(prefers-color-scheme: light)"/>
  <source srcset="/uploads/documentation/api/group-fields-dark.png"  media="(prefers-color-scheme: dark)"/>
  <img src="/uploads/documentation/api/group-fields-light.png" alt="Group Fields Example Screenshot"/>
</picture>

For example:

<pre><code class="language-php">$crud->groupFields("PersonalInfo", ['first_name', 'last_name', 'email']);
$crud->groupFields("Address", ['address', 'city', 'state', 'zip_code']);
$crud->groupFields("Other", ['phone', 'notes']);
</code></pre>

or you can group them all at once:

<pre><code class="language-php">$crud->groupFields([
    'Personal Info' => ['first_name', 'last_name', 'email'],
    'Address' => ['address', 'city', 'state', 'zip_code'],
    'Other' => ['phone', 'notes']
]);</code></pre>

The keys of the array are displaying the tab names.
The values are arrays of field names that will be grouped under each tab.

<strong>Notice:</strong> Keep in mind that if you decide to group the fields in tabs, fields that are not in the list
they won't be displayed in the form. For example this is not combinable with `unsetFields` or `setFields` method.

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