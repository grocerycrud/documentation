---
id: get-state
title: getState
description: 
permalink: docs/get-state
previous: field-type-read-form
next: get-state-info
---

# getState


<pre><code class="language-php">string getState()</code></pre>
Simply get the state as a string. This is useful when you need to add a very specific implementation that it is outside of grocery CRUD Enterprise. A common usage to use the <code>getState</code> method is mainly if you need to have some permissions checks. Of course as this is something custom, you can specify the usage for <code>getState</code> for your own needs.

## Example
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');

if ($crud->getState() === 'EditForm') {
    // Mocking a minimal response of GroceryCRUD with an error message
    // Custom error and json response with an error message is only available on Enterprise version
    $output = (object)[
        'isJSONResponse' => true,
        'output' => json_encode(
            (object)[
                'message' => 'It seems that you don\'t have access to edit this customer.',
                'status' => 'failure'
            ]
        )
    ];
} else {
    $output = $crud->render();
}</code></pre>

You can check the result of the above code below. Simply try to edit any customer. The above code is just an example, 
and we also agree that if this was a production code it would be a bad UX experience 😃

`embed:demo_get-state`