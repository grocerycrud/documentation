---
id: get-state-info
title: getStateInfo
permalink: docs/get-state-info
previous: get-state
next: read-fields
---

# getStateInfo


<pre><code class="language-php">getStateInfo()</code></pre>
Get all the information about the state, inlcuding:
<ol>
	<li>The state as string</li>
	<li>All the state parameters</li>
</ol>

For example if you have an insert state then the state parameters are all the data for insert.

## Example

The below example:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');

if ($crud->getState() === 'EditForm') {
    $stateInfo = $crud->getStateInfo();

    $customerId = $stateInfo->primaryKeyValue;

    // Mocking a minimal response of GroceryCRUD with an error message
    // Custom error and json response with an error message is only available on Enterprise version
    $output = (object)[
        'isJSONResponse' => true,
        'output' => json_encode(
            (object)[
                'message' => 
                    'You don\'t have permissions to edit the customer with ID: ' . $customerId,
                'status' => 'failure'
            ]
        )
    ];
} else {
    $output = $crud->render();
}</code></pre>

Will have as an output the below result:

`embed: demo_get-state-info`