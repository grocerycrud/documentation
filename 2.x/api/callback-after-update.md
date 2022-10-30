---
id: callback-after-update
title: callbackAfterUpdate
description: The callback that will be used right after the update of the data.
canonical: docs/callback-after-update
previous: unset-add-fields
next: callback-before-update
---

# callbackAfterUpdate

<pre><code class="language-php">callbackAfterUpdate(callable $callback)</code></pre>

The callback that will be used right after the update of the data. There are basically two types of values that the developer will receive from the callback:
<ol>
 	<li>The <code>primaryKeyValue</code>: This is the primary key value that the update took place.</li>
 	<li>The <code>data</code>: These are the <strong>filtered </strong>data from the update</li>
</ol>

More specifically, below you can see an example of the <code>$stateParameters</code> variable for the callbackAfterInsert:
<pre><code class="language-php">$stateParameters = (object)[
    'primaryKeyValue' => '1234', //primary key value
    'data' => [ // data to update
        'customerName' => 'John',
        'phone' => '1234567890',
        ...
    ]
];</code></pre>

A full example is also available for you to understand better:

<pre><code class="language-php">$crud->setTable('offices');
$crud->setSubject('Office', 'Offices');
$crud->columns(['city','country','phone','addressLine1','postalCode']);

$crud->callbackAfterUpdate(function ($stateParameters) use ($callbackAfterUpdateModel) {
    $callbackAfterUpdateModel->officesAfterUpdate($stateParameters->primaryKeyValue);

    return $stateParameters;
});</code></pre>

The result of the above code can be found here:

`embed:demo_callback-after-update`