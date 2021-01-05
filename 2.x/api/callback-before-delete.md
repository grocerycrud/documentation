---
id: callback-before-delete
title: callbackBeforeDelete
permalink: docs/callback-before-delete
previous: callback-after-upload
next: callback-before-delete-multiple
---

# callbackBeforeDelete


<pre><code class="language-php">callbackBeforeDelete(callable $callback)</code></pre>
The callback that will be used right before the delete. The only parameter that the state will have is the primary key value. 

Example:
<pre><code class="language-php">$crud->callbackBeforeDelete(function ($stateParameters) {
    // Your code here    

    return $stateParameters;
});</code></pre>

The <code>$stateParameters</code> variable is at the below form:

<pre><code class="language-php">$stateParameters = (object)[
    'primaryKeyValue' => '1234'
];</code></pre>

## Example

Below there is a working example of the <code>callbackBeforeDelete</code> method.

<pre><code class="language-php">$crud->setTable('offices');
$crud->setSubject('Office', 'Offices');
$crud->columns(['city','country','phone','addressLine1','postalCode']);

$crud->callbackBeforeDelete(function ($stateParameters) {
  // Custom error messages are only available on Grocery CRUD Enterprise
  $errorMessage = new \GroceryCrud\Core\Error\ErrorMessage();
  return $errorMessage->setMessage("You don't have permissions to delete this office\n");
});

$output = $crud->render();
</code></pre>

`embed:demo_callback-before-delete`