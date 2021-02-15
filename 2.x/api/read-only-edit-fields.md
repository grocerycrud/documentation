---
id: read-only-edit-fields
title: readOnlyEditFields
description: 
permalink: docs/read-only-edit-fields
previous: read-only-clone-fields
next: read-only-fields
---

# readOnlyEditFields


<pre><code class="language-php">readOnlyEditFields(array $fields)</code></pre>
There are cases, that we need some fields to be read only but only to the edit form modal. In that case we can use the “Read Only Edit Fields” method like this:

<pre><code class="language-php">$crud->readOnlyEditFields(['reference_id', 'email']);</code></pre>

In the above case the <code>reference_id</code> and the <code>email</code> field will be shown but the user will not be able to change the default value.