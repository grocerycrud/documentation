---
id: callback-after-delete-multiple
title: callbackAfterDeleteMultiple
description: The callback that will be used right after the multiple delete functionality.
canonical: docs/callback-after-delete-multiple
previous: callback-after-delete
next: callback-before-delete
---

# callbackAfterDeleteMultiple


<pre><code class="language-php">callbackAfterDeleteMultiple(callable $callback)</code></pre>
The callback that will be used right after the <strong>multiple delete</strong> functionality. Multiple delete functionality is when you are choosing many rows from the checkboxes on the left. Please have in mind that you can always choose only one row and the callbackAfterDeleteMultiple (it is just that it will have an array with one id only).