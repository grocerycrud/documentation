---
id: callback-edit-field
title: callbackEditField
description: A callback that is used in case you need to create a custom field for the edit/update form.
canonical: docs/callback-edit-field
previous: callback-before-update
next: callback-edit-form
---

# callbackEditField

<pre><code class="language-php">callbackEditField(string $fieldName, callable $callback)</code></pre>
Create a custom field with a callback for edit/update form. As parameters we are getting two parameters:

<ol>
	<li>The value of the field from the database for that row</li>
	<li>The primary key value of the row in case you need to use it for an extra manual query</li>
</ol>

For example:
<pre><code class="language-php">$crud->callbackEditField('telephone_number', function ($fieldValue, $primaryKeyValue, $rowData) {
    return '+30 &lt;input name="telephone_number" value="' . $fieldValue . '"  /&gt;';
});</code></pre>

Have in mind that from PHP 5.4 and later there is an extra functionality with keywork <code>use</code>, so that means that you can pass any extra parameters at the callback from outside the callback if you wish it. For example:

<pre><code class="language-php">
$username = 'john';
$crud->callbackEditField('telephone_number', function ($fieldValue, $primaryKeyValue, $rowData) use ($username) {
     // You have access now at the extra custom variable $username
    return '+30 &lt;input name="telephone_number" value="' . $fieldValue . '"  /&gt; for: ' . $username ;
});</code></pre>

<strong>Notice:</strong> Grocery CRUD Enterprise is all about security so we are obliged to inform you that the callbackEditField is using the: <a href="https://facebook.github.io/react/docs/dom-elements.html#dangerouslysetinnerhtml" target="_blank">dangerouslySetInnerHTML</a> function of reactJS. As you can understand from the name, this may be very dangerous if it is not used properly. We are suggesting to use it mainly in admin environments and make sure that you are always filtering your data at the callback. This was the only way that we could enable the functionality of callbackEditField and you have to be aware of this warning before using it.