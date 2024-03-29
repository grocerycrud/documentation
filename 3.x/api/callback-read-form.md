---
id: callback-read-form
title: callbackReadForm
description: A callback to change the read data that will display at the read/view modal.
canonical: docs/callback-read-form
previous: callback-read-field
next: read-fields
---

# callbackReadForm

<pre><code class="language-php">callbackReadForm(callable $callback)</code></pre>
This callback is used in case you need to change the representation of the value on view form.

At the below example, the url always need to start with http:// or https://. In case that the url starts does not start with http:// or https:// then we are adding it at the beginning of the string. The implementation of the example is as follows:
<pre><code class="language-php">$crud->callbackReadForm(function ($data) {
    if (substr($data['url'], 0, 7) !== 'http://' && substr($data['url'], 0, 8) !== 'https://') {
        $data['url'] = 'http://' . $data['url'];
    }

    return $data;
});</code></pre>