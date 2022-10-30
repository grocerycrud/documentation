---
id: custom-error-messages
title: Custom Error Messages
description: Example for showing custom error messages to the end user.
canonical: docs/custom-error-messages
previous: 
next:
---

# Custom Error Messages

There are cases that especially for validation purposes we need a custom error message to the end user.

Fortunately this is possible when we are using callbacks with Grocery CRUD `ErrorMessage` class.

For example, let's say that we would like to provide an error message when the user adds the 'Rejected' 
status without a message. The callback will look like this:

<pre><code class="language-php">$crud->callbackBeforeInsert(function ($stateParameters) {
    if ($stateParameters->data['status'] === 'Rejected' && $stateParameters->data['message'] === '') {
        // The error message as a return parameter is only available at Enterprise version
        $errorMessage = new \GroceryCrud\Core\Error\ErrorMessage();
        return $errorMessage->setMessage("You can't add a Rejected status without a message\n");
    }

    return $stateParameters;
});
</code></pre>

As you can see from the above scenario we have two cases:

1. The first one (if statement is `false`) 
is simply returning `$stateParameters`. That means that we will continue the insert as expected.

2. The second one (if statement is `true`) we are returning an error message that will not continue to the 
insert and instead will show an error message.

The `ErrorMessage` class as a return value is available to the following functions: 

- `callbackBeforeInsert` 
- `callbackBeforeUpdate`
- `callbackBeforeDelete`
- `callbackBeforeUpload`
- `callbackInsert`
- `callbackUpdate`
- `callbackDelete`
- `callbackUpload` 
       
and also the functions: 
- `callbackAfterInsert`,
- `callbackAfterUpdate`
- `callbackAfterDelete`
- `callbackAfterUpload`  

However, you will need to be careful when using the  error messages on `after` callbacks as you will need to manually revert the change if you wish so.

## Example

<pre><code class="language-php">$crud->setTable('orders');
$crud->setSubject('Order', 'Orders');
$crud->setRelation('customerNumber','customers','contactLastName');

$callbackWithValidation = function ($stateParameters) {
    if ($stateParameters->data['status'] === 'On Hold' && empty($stateParameters->data['comments'])) {
        // The error message as a return parameter is only available at Enterprise version
        $errorMessage = new \GroceryCrud\Core\Error\ErrorMessage();
        return $errorMessage->setMessage("You can't add an \"On Hold\" status without a comment\n");
    }

    return $stateParameters;
};

$crud->callbackBeforeInsert($callbackWithValidation);
$crud->callbackBeforeUpdate($callbackWithValidation);

$output =  $crud->render();
</code></pre>

`embed:demo_custom-error-messages`

