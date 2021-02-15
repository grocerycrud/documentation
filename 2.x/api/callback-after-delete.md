---
id: callback-after-delete
title: callbackAfterDelete
description: 
permalink: docs/callback-after-delete
previous: callback-add-form
next: callback-after-delete-multiple
---

# callbackAfterDelete


<pre><code class="language-php">callbackAfterDelete(callable $callback)</code></pre>
The callback that will be used right after the delete. The only parameter that the state will have is the primary key value. 

<code>Important:</code> It is important to mention here that the callbackAfterDelete is called only for the Delete button of the row. The callback <strong>will not</strong> be called for the multiple delete functionality. If you need to use a callback for multiple delete rows, you should use <a href="/enterprise/api-and-function-list/callbackAfterDeleteMultiple">callbackAfterDeleteMultiple</a> instead and keep the callbackAfterDelete for the one-row delete button.
<code>Notice:</code> Have in mind that if you haven't replaced the actual delete functionality (e.g. with a callback), it will be impossible to retrieve the data of the deleted row. If the last phrase doesn't make much sense to you we have an example below to understand exactly what we mean.

Example:
<pre><code class="language-php">$crud->callbackAfterDelete(function ($stateParameters) {
    // Your code here    

    return $stateParameters;
});</code></pre>

The <code>$stateParameters</code> variable is at the below form:

<pre><code class="language-php">$callbackAfterDelete = (object)[
    'primaryKeyValue' => '1234'
];</code></pre>

## Example

Below there is a working example of the <code>callbackAfterDelete</code> method. As we also wanted to skip the delete so we can update the record, we are also using the <code>callbackDelete</code> at the example just for the demonstration to skip the delete.

<pre><code class="language-php">$crud->setTable('employees');
$crud->setSubject('Employee', 'Employees');
$crud->setRelation('officeCode','offices','city');
$crud->displayAs('officeCode','City');
// Unsetting the multiple delete for this example. If we need it we also need to
// consider to add a $crud->callbackDeleteMultiple callback as well
$crud->unsetDeleteMultiple();

$crud->callbackDelete(function ($stateParameters) {
    // Making sure that we skip the delete functionality first!
    return $stateParameters;
});

$crud->callbackAfterDelete(function ($stateParameters) use ($callbackDeleteModel) {
    $callbackDeleteModel->deleteEmployee($stateParameters->primaryKeyValue);

    return $stateParameters;
});

$output = $crud->render();
</code></pre>

`embed:demo_callback-after-delete`

`$callbackDeleteModel` is using Grocery CRUD [Custom Model](/docs/custom-model) but you are not limited on that. On callbacks you can use any custom libraries.

For reference the code for `CallbackDelete` class can be found below:

<pre><code class="language-php">&lt;?php
namespace App\Models;
use GroceryCrud\Core\Exceptions\Exception;
use GroceryCrud\Core\Model;
use Zend\Db\Sql\Sql;

class CallbackDelete extends Model {
    public function deleteEmployee($employeeNumber) {
        // Validating our data
        if (!is_numeric($employeeNumber)) {
            throw new Exception("Wrong input");
        }

        $sql = new Sql($this->adapter);
        $select = $sql->select();
        $select->from('employees');
        $select->where(['employeeNumber = ?' => $employeeNumber]);

        $employee = $this->getRowFromSelect($select, $sql);

        // More validations
        if (!empty($employee) && is_array($employee) && count($employee) === 1) {
            $employeeLastName = $employee[0]['lastName'];

            if (!strstr($employeeLastName, '[DELETED] ')) {
                $update = $sql->update('employees');
                $update->where(['employeeNumber = ?' => $employeeNumber]);

                $update->set(['lastName' => '[DELETED] ' . $employeeLastName]);

                $statement = $sql->prepareStatementForSqlObject($update);
                return $statement->execute();
            }
        }

        return false;
    }
}</code></pre>