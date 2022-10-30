---
id: callback-before-update
title: callbackBeforeUpdate
description: The callback is used in cases we need to add or change data before the update functionality.
canonical: docs/callback-before-update
previous: callback-after-update
next: callback-edit-field
---

# callbackBeforeUpdate

<pre><code class="language-php">callbackBeforeUpdate(callable $callback)</code></pre>

The callback is used in cases we need to add, change or filter data before the update functionality. There are basically two types of values that the developer will receive from the callback:
<ol>
    <li>The <code>primaryKeyValue</code>: This is the primary key value that the update will take place.</li>
    <li>The <code>data</code>: These are the <strong>filtered </strong>data from the update</li>
</ol>

More specifically, below you can see an example of the <code>$stateParameters</code> variable for the callbackBeforeInsert:
<pre><code class="language-php">$stateParameters = (object)[
    'primaryKeyValue' => '1234', //primary key value
    'data' => [ // data to update
        'customerName' => 'John',
        'phone' => '1234567890',
        ...
    ]
];</code></pre>

A full example is also available for you to understand better. At the below example we are changing the data to append the "[BEFORE UPDATE]" at the city name (just for demonstration really)

<pre><code class="language-php">$crud->setTable('offices');
$crud->setSubject('Office', 'Offices');
$crud->columns(['city','country','phone','addressLine1','postalCode']);

$crud->callbackBeforeUpdate(function ($stateParameters) {
    $city = $stateParameters->data['city'];

    if (!strstr($city, '[BEFORE UPDATE]')) {
        $stateParameters->data['city'] = '[BEFORE UPDATE] ' . $city;
    }

    return $stateParameters;
});</code></pre>

The result of the above code can be found here:

`embed:demo_callback-before-update`