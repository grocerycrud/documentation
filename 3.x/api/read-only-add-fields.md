---
id: read-only-add-fields
title: readOnlyAddFields
description: There are cases, that we need some fields to be read only but only to the add form modal. 
permalink: docs/read-only-add-fields
previous: read-fields
next: read-only-clone-fields
---

# readOnlyAddFields

<pre><code class="language-php">readOnlyAddFields(array $fields)</code></pre>
There are cases, that we need some fields to be read only but only to the add form modal. In that case we can use the "Read Only Add Fields" method like this:

<pre><code class="language-php">$crud->readOnlyAddFields(['category_id', 'parent_id']);</code></pre>

In the above case the <code>category_id</code> and the <code>parent_id</code> will be shown but the user will not be able to change the default value.