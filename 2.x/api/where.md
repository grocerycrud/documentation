---
id: where
title: where
permalink: docs/where
previous: columns
next: 
---

# where

<pre><code class="language-php">where(array|string $where)</code></pre>
A quick way to add an extra where statement to your datagrid queries and for any other operators for security.

The syntax may vary depends of what you need to do. The suggested syntax is the below:

<pre><code class="language-php">$crud->where([
    'customers.country' => 'USA'
]);</code></pre>

The above is the suggested way as:
<ol>
        <li>You prevent sql injections as the second parameter is being filtered by zend framework</li>	
        <li>When someone will see an array then they can straight forward understand that he/she can add more where statements to the array</li>
	<li>The table is specified. This is in case you have ambitious field name (for example with the setRelation field)</li>
	<li>With this syntax everyone can understand that where statement is clearly <code>"customers.country = 'USA'"</code></li>

</ol>

Other suggested syntax to use it is the below:

<pre><code class="language-php">$crud->where([
    'customers.country = ?' => 'USA'
]);</code></pre>

With the above syntax you can add any of the below implementations:

<pre><code class="language-php">$crud->where([
    'customers.country > ?' => 'USA'
]);
$crud->where([
    'customers.country >= ?' => 'USA'
]);
$crud->where([
    'customers.country < ?' => 'USA'
]);
$crud->where([
    'customers.country <= ?' => 'USA'
]);
$crud->where([
    'customers.country LIKE ?' => '%USA%'
]);
</code></pre>

The developer can also add as many where statements are required. For example:

<pre><code class="language-php">$crud->where([
    'customers.country = ?' => 'USA',
    'contact_last_name LIKE ?' => '%Tse%'
]);</code></pre>

<strong>Notices:</strong>
1. You should already notice that you can also have a string input at where statement. Please have in mind that this <strong>is not a suggested way</strong> as it is easier to have SQL injections in case that the field is dynamic. If you need to use the string, please make sure that you are already filtering any dynamic input or you are using a non-dynamic string. Please be careful when you are using a full string for where as <code>where</code> statement is added in all the operations. The syntax is as follows:
<pre><code class="language-php">$crud->where("customers.country = 'USA'")</code></pre>

2. Please notice that <code>where</code> statements are also added at all the operations except the insert for security reasons.
   Also have in mind that for the update functionality, you should also use callbackBeforeUpdate in case the field is visible to the user. If the field is not visible to the user then you don't really need to do anything. As this is a bit complicated to understand, we did create two examples to completely understand the two different concepts that I am describing.

So let's assume that the user has access only to the customers that are located in USA.

The below example does <strong>not</strong> need any callbackBeforeUpdate for the security of the field country as the field is not visible (and hence not accessible) for the user.

<pre><code class="language-php">$crud->setSubject('Customer', 'Customers');
$crud->setTable('customers');

$crud->where(['customers.country' => 'USA']);

$crud->unsetAdd();
$crud->setRead();
$crud->columns(['customerName', 'contactLastName', 'phone', 'city', 'country']);
$crud->fields(['customerName', 'contactLastName', 'phone', 'city']);
$crud->displayAs('customerName', 'Name');
$crud->displayAs('contactLastName', 'Last Name');

$output = $crud->render();</code></pre>

[demo]demo_where_example_1[/demo]

The above example will never have a scenario to update the country as the user does not have access to change country. Even if a user try to hijack the AJAX call and send a country field, Grocery CRUD will protect that.

On the other hand, if the country is a dynamic field (a field that the user can also change), the only way to protect your data on the update is with a callbackBeforeUpdate. You can see a full example below:

<pre><code class="language-php">$crud->setSubject('Customer', 'Customers');
$crud->setTable('customers');

$crud->where(['customers.country' => 'USA']);

$crud->unsetAdd();
$crud->setRead();
$crud->columns(['customerName', 'contactLastName', 'phone', 'city', 'country']);
$crud->fields(['customerName', 'contactLastName', 'phone', 'city', 'country']);

$crud->callbackBeforeUpdate(function ($stateParameters) {
    if ($stateParameters->data['country'] !== 'USA') {
        $callback = new \GroceryCrud\Core\Error\ErrorMessage();
        $callback->setMessage('We are sorry but you are not allowed to change the country');
        return $callback;
    }

    return $stateParameters;
});

$crud->displayAs('customerName', 'Name');
$crud->displayAs('contactLastName', 'Last Name');

return $crud->render();</code></pre>

[demo]demo_where_example_2[/demo]





