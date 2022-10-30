---
id: field-type-form-fields
title: fieldTypeFormFields
description: The function fieldTypeFormFields is a facade function to call all the functions of field-types for the form data.
canonical: docs/field-type-form-fields
previous: field-type-edit-form
next: field-type-read-form
---

# fieldTypeFormFields

<pre><code class="language-php">fieldTypeFormFields(string $fieldName, string|ModelFieldType $fieldType)</code></pre>
This function is really just a facade function to call all the 4 functions at once:
<ol>
	<li>fieldTypeAddForm</li>
	<li>fieldTypeEditForm</li>
	<li>fieldTypeReadForm</li>
        <li>fieldTypeCloneForm</li>
</ol>

<h2>Example</h2>
For example the below code:

<pre><code class="language-php">$crud->fieldTypeFormFields('date_birth_year', 'numeric');</code></pre>

is exactly the same as:
<pre><code class="language-php">$crud->fieldTypeAddForm('date_birth_year', 'numeric');
$crud->fieldTypeEditForm('date_birth_year', 'numeric');
$crud->fieldTypeReadForm('date_birth_year', 'numeric');
$crud->fieldTypeCloneForm('date_birth_year', 'numeric');
</code></pre>
