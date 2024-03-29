---
id: callback-edit-form
title: callbackEditForm
description: This callback is used in case we need to append, filter or change the data that are going to appear on the edit form.
canonical: docs/callback-edit-form
previous: callback-edit-field
next: callback-update
---

# callbackEditForm

<pre><code class="language-php">callbackEditForm(callable $callback)</code></pre>

This callback is used in case we need to append, filter or change the data that are going to appear on the edit form.

## Example

<pre><code class="language-php">$crud->callbackEditForm(function ($data) {
    // The reference id always starts with 0098_ and 
    // hence in case it doesn't start with this number, we
    // are adding it at the beginning of the string
    if (substr($data['reference_id'], 0, 5) !== '0098_') {
        $data['reference_id'] = '0098_' . $data['reference_id'];
    }

    return $data;
});</code></pre>