---
id: get-model
title: getModel
description: Use the model that is used for the CRUD for database operations for your own code.
canonical: docs/get-model
previous: set-model
next: set-primary-key
---

# getModel

<pre><code class="language-php">GroceryCrud\Core\Model\ModelInterface getModel()</code></pre>

You can get the model that is used for the CRUD. The model is getting created on the constructor of `GroceryCrud` 
instance. This is useful if you want to use the model to use it in your own code for database operations.
The functions that getModel returns are not all documented here, but you can see the full list of functions 
in the `ModelInterface` class. A very useful function that you can use is the `getRelationData` function which can be
used on callbacks.

## Example

Below is an example of how you can use the `getModel` function to get the relational data of a field in 
the datagrid state. The below example is using the `getRelationData` function to use it with the `callbackColumn`
function in order to get a URL to the city for Google Maps.

<pre><code class="language-php">$crud->setTable('employees');
$crud->setSubject('Employee', 'Employees');
$crud->setRelation('officeCode','offices','city');
$crud->displayAs('officeCode','City');
$crud->columns(['firstName','lastName','officeCode']);

$offices = [];

// Making sure that we are getting the relational data only when we are 
// at the datagrid state in order to avoid unnecessary queries.
if ($crud->getState() === 'Datagrid') {
    $officesRelationalData = $crud->getModel()->getRelationData('offices', 'city');

    foreach ($officesRelationalData as $office) {
        $offices[$office->id] = $office->title;
    }
}

$crud->callbackColumn('officeCode', function ($value) use ($offices) {
    $city = array_key_exists($value, $offices) ? $offices[$value] : "";

    
    if (empty($city)) {
        return '';
    }
    
    return "&lt;a href='https://www.google.com/maps/place/" . urlencode($city) . "'
         target='_blank' title='Open in Google Maps' rel='noopener noreferrer'&gt;{$city}&lt;/a&gt;";
});

$output = $crud->render();</code></pre>

`embed:demo_get-model`