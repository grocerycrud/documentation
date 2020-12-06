---
id: read-only-fields
title: readOnlyFields
permalink: docs/read-only-fields
previous: read-only-edit-fields
next: render
---

# readOnlyFields


<pre><code class="language-php">readOnlyFields(array $fields)</code></pre>
Specifying the fields that can't be edited and will only be viewed. The rule will be the same for the insert and update operations. 

Example:
<pre><code class="language-php">$crud->readOnlyFields(['referenceId', 'insertDate']);</code></pre>

[demo]demo_readonly_fields[/demo]