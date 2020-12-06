---
id: callback-delete
title: callbackDelete
permalink: docs/callback-delete
previous: callback-column
next: callback-delete-multiple
---

# callbackDelete


<pre><code class="php">callbackDelete(callable $callback)</code></pre>
The basic usage of <code>callbackDelete</code> is when you want to skip the delete functionality. If the <code>callbackDelete</code> is called then that means that the actual default delete functionality of Grocery CRUD Enterprise will not triggered.

<p class="bg-warning" style="padding:10px;"><strong><span class="fa fa-exclamation-triangle"></span> Warning!</strong> Please be aware that you should also add a callback into the callbackDeleteMultiple in order to make sure that the callback is always triggered. For more also check: <a href="https://www.grocerycrud.com/enterprise/api-and-function-list/callbackDeleteMultiple">callbackDeleteMultiple</a> documentation</p>

The callbackDelete is getting as a parameter a callback. This callback has as parameter the below:
- primaryKeyValue 

For example:

<pre><code class="php">$crud->callbackDelete(function ($stateParameters) {
    // Your code will run here
    return $stateParameters;
});</code></pre>

Below you can see a full example. At the below example we are skipping completely the delete functionality and instead we are updating the row by adding at the title the word "[DELETED]"

<pre><code class="php">$crud->setTable('employees');
$crud->setSubject('Employee', 'Employees');
$crud->setRelation('officeCode','offices','city');
$crud->displayAs('officeCode','City');

// Also consider to add a $crud->callbackDeleteMultiple callback here

$crud->callbackDelete(function ($stateParameters) {
    $this->db->where('employeeNumber', $stateParameters->primaryKeyValue);
    $customer = $this->db->get('employees')->row();

    if (!empty($customer)) {
        $this->db->update('employees',
            ['lastName' => '[DELETED] ' . $customer->lastName],
            ['employeeNumber' => $stateParameters->primaryKeyValue]);
    }

    return $stateParameters;
});

$output = $crud->render();</code></pre>

Try to remove one row at the below example to see exactly the functionality of the above example:
[demo]demo_callback_delete[/demo]