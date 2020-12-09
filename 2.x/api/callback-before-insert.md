---
id: callback-before-insert
title: callbackBeforeInsert
permalink: docs/callback-before-insert
previous: callback-before-delete-multiple
next: callback-before-update
---

# callbackBeforeInsert

<pre><code class="language-php">callbackBeforeInsert(callable $callback)</code></pre>
The function callbackBeforeInsert is used in cases we need to add or change something before the insert functionality of Grocery CRUD Enterprise. For example a common usage is when we need to add more fields to the insert that will need to be done from the server (e.g. the user is not allowed to add this).

The usage is simple:
<pre><code class="language-php">$crud->callbackBeforeInsert(function ($stateParameters) {
    // Your code here

    return $stateParameters;
});</code></pre>

You can also provide a custom error like this:

<pre><code class="language-php">$crud->callbackBeforeInsert(function ($stateParameters) {
    if ($stateParameters->data['status'] === 'Rejected' && $stateParameters->data['message'] === '') {
          $errorMessage = new \GroceryCrud\Core\Error\ErrorMessage();
          return $errorMessage->setMessage("You can't add a Rejected status without a message\n");
    }

    return $stateParameters;
});</code></pre>

<h2>Full example</h2>

For example, let's say that we need to force in every insert of an order to have the status as "Disputed". In that case we could have the below code:

<pre><code class="language-php">$crud->setTable('orders');
$crud->setSubject('Order', 'Orders');
$crud->unsetAddField(['status']);
$crud->setRelation('customerNumber','customers','contactLastName');

$crud->callbackBeforeInsert(function ($stateParameters) {
    $stateParameters->data['status'] = 'Disputed';

    return $stateParameters;
});

$output =  $crud->render();</code></pre>

Try to add any order and you will see that without adding the information of the status, the status will always automatically going to be "Disputed"

`embed:demo_callback_before_insert`