---
id: callback-clone-field
title: callbackCloneField
permalink: docs/callback-clone-field
previous: callback-before-upload
next: callback-column
---

# callbackCloneField


<pre><code class="php">callbackCloneField(string $fieldName, callable $callback)</code></pre>
Create a custom field with a callback for clone form. The main callback get as parameters: 

<ol>
	<li>The value of the field from the database for that row</li>
	<li>The primary key value of the row in case you need to use it for an extra manual query</li>
</ol>

For example:
<pre><code class="php">$crud->callbackCloneField('telephone_number', function ($fieldValue, $primaryKeyValue, $rowData) {
    return '+30 &lt;input name="telephone_number" value="' . $fieldValue . '"  /&gt;';
});</code></pre>