---
id: field-options
title: fieldOptions
description:  Customize the visual appearance of a field. For example hint_text will add a text as a placeholder text.
canonical: docs/field-options
previous: fields
next: required-fields
---

# fieldOptions

<pre><code class="language-php">fieldOptions(string $fieldName, array $fieldOptions);</code></pre>

Customize the visual appearance of a field. 
For example `hint_text` will add a text as a placeholder text when the field is empty.

Example:

<pre><code class="language-php">$crud->fieldOptions('customer_name', [ 'hint_text' => 'Please enter your full name' ]);</code></pre>

You can see a full working example below.

<pre><code class="language-php">$crud->setTable('employees');
$crud->setSubject('Employee', 'Employees');
$crud->setRelation('officeCode','offices','city');

$crud->displayAs('firstName','First Name');
$crud->displayAs('lastName','Last Name');
$crud->displayAs('jobTitle','Job Title');
$crud->displayAs('officeCode','City');

$crud->fieldOptions('firstName', [ 'hint_text' => 'First name of the employee' ]);
$crud->fieldOptions('lastName', [ 'hint_text' => 'Last name of the employee' ]);
$crud->fieldOptions('extension', [ 'hint_text' => 'Internal phone extension' ]);
$crud->fieldOptions('email', [ 'hint_text' => 'Email address of the employee' ]);
$crud->fieldOptions('jobTitle', [ 'hint_text' => 'Job title of the employee' ]);
$crud->fieldOptions('officeCode', [ 'hint_text' => 'City of the office' ]);

$output = $crud->render();</code></pre>

This will output the below results. Try to click on the "Add Employee" button 
so you can see the placeholders for the `hint_text`.

`embed:demo_field-options`