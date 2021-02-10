---
id: read-only-clone-fields
title: readOnlyCloneFields
permalink: docs/read-only-clone-fields
previous: read-only-add-fields
next: read-only-edit-fields
---

# readOnlyCloneFields


<pre><code class="language-php">readOnlyCloneFields(array $fields)</code></pre>
There are cases, that we need some fields to be read only but only to the clone form modal. In that case we can use the “Read Only Clone Fields” method like this:

<pre><code class="language-php">$crud->readOnlyCloneFields(['reference_id', 'email']);</code></pre>

In the above case the <code>reference_id</code> and the <code>email</code> field will be shown but the user will not be able to change the default value.