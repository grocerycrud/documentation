---
id: callback-delete-multiple
title: callbackDeleteMultiple
permalink: docs/callback-delete-multiple
previous: callback-delete
next: callback-edit-field
---

# callbackDeleteMultiple


<pre><code class="language-php">callbackDeleteMultiple(callable $callback)</code></pre>
Replaces the default multiple delete functionality with the callback specified.

<p class="bg-warning" style="padding:10px;"><strong><span class="fa fa-exclamation-triangle"></span> Warning!</strong> Please be aware that you should also add a callback into the <code>callbackDelete</code> in order to make sure that the callback is always triggered. For more also check: <a href="https://www.grocerycrud.com/enterprise/api-and-function-list/callbackDelete">callbackDelete</a> documentation</p>

The <code>callbackDeleteMultiple</code> is getting as a parameter a callback. This callback has as parameter the below:
– primaryKeys

For example:

<pre><code class="language-php">$crud->callbackDelete(function ($stateParameters) {
    
    print_r($stateParameters); // An example for debugging purposes!
    /** This will export something like this: 
        stdClass Object
        (
            [primaryKeys] => Array
                (
                    [0] => 198
                    [1] => 204
                )

        )
    **/

    return $stateParameters;
});</code></pre>

You can also see a full example below. Try to remove by clicking the checkboxes and then click the Delete button. You will notice that the field with name <code>extension</code> will take the value <code>[DELETED]</code> instead of getting deleted:

<pre><code class="language-php">$crud->setTable('employees');
$crud->setSubject('Employee', 'Employees');
$crud->setRelation('officeCode','offices','city');
$crud->displayAs('officeCode','City');

// Also consider to add a $crud->callbackDelete callback here

$crud->callbackDeleteMultiple(function ($stateParameters) {

    $primaryKeys = [];
    foreach ($stateParameters->primaryKeys as $primaryKey) {
        // For security reasons check if the primary key is numeric
        if (is_numeric($primaryKey)) { 
            $primaryKeys[] = $primaryKey;
        }
    }


    if (!empty($primaryKeys)) {
        $this->db->update(
            'employees',
            ['extension' => '[DELETED]'], 
            'employeeNumber IN (' . implode(',', $primaryKeys) . ')'
         );
    } else {
        return false;
    }

    return $stateParameters;
});

$output = $crud->render();
</code></pre>

The above example will render the following result:

`embed:demo_callback-delete-multiple`