---
id: callback-update
title: callbackUpdate
permalink: docs/callback-update
previous: callback-read-form
next: callback-upload
---

# callbackUpdate


<pre><code class="language-php">callbackUpdate(callable $callback)</code></pre>
The function <code>callbackUpdate</code> is used when we need to completely skip the default update functionality of Grocery CRUD Enterprise. The usage is simple, for example:

<pre><code class="language-php">$crud->callbackUpdate(function ($stateParameters) {
    // Your code goes here

    return $stateParameters;
});</code></pre>

You can see a full working example below:

<pre><code class="language-php">$crud->setTable('orders');
$crud->setSubject('Order', 'Orders');
$crud->setRelation('customerNumber','customers','contactLastName');

$crud->callbackUpdate(function ($stateParameters) {
    // As we are skipping the actual update and
    // we will need to update by our own
    $stateParameters->data['comments'] = '[Update - ' .date('d M') . ']'. $stateParameters->data['comments'];
    $this->db->update('orders', $stateParameters->data, ['orderNumber' => $stateParameters->primaryKeyValue]);

    return $stateParameters;
});

$output = $crud->render();</code></pre>

Notice: The <code>$this->db</code> is from Codeigniter as this example is installed in a Codeigniter project. You can of course use your own database calls from your framework instead.

With the below live example you can see that when we are updating any row then the text "[Update - day Month]" is prepend at the beginning of the field comments.

`embed:demo_callback-update`