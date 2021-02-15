---
id: callback-delete-multiple
title: callbackDeleteMultiple
description: 
permalink: docs/callback-delete-multiple
previous: callback-delete
next: set-delete
---

# callbackDeleteMultiple


<pre><code class="language-php">callbackDeleteMultiple(callable $callback)</code></pre>
Replaces the default multiple delete functionality with the callback specified.

<p class="bg-warning" style="padding:10px;"><strong><span class="fa fa-exclamation-triangle"></span> Warning!</strong> Please be aware that you should also add a callback into the <code>callbackDelete</code> in order to make sure that the callback is always triggered. For more also check: <a href="https://www.grocerycrud.com/enterprise/api-and-function-list/callbackDelete">callbackDelete</a> documentation</p>

The <code>callbackDeleteMultiple</code> is getting as a parameter a callback. This callback has as parameter the below:
– primaryKeys

For example:

<pre><code class="language-php">$crud->callbackDeleteMultiple(function ($stateParameters) {
    
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

## Example

You can also see a full example below.

<pre><code class="language-php">$crud->setTable('employees');
$crud->setSubject('Employee', 'Employees');
$crud->setRelation('officeCode','offices','city');
$crud->displayAs('officeCode','City');

$crud->callbackDelete(function ($stateParameters) use ($callbackDeleteModel) {
    $callbackDeleteModel->deleteEmployee($stateParameters->primaryKeyValue);

    return $stateParameters;
});

$crud->callbackDeleteMultiple(function ($stateParameters) use ($callbackDeleteModel) {

    $primaryKeys = [];
    foreach ($stateParameters->primaryKeys as $primaryKey) {
        // For security reasons check if the primary key is numeric
        if (is_numeric($primaryKey)) {
            $primaryKeys[] = $primaryKey;
        }
    }

    if (count($primaryKeys) > 10) {
        // Custom error messages are only available on Grocery CRUD Enterprise
        $errorMessage = new \GroceryCrud\Core\Error\ErrorMessage();
        return $errorMessage->setMessage("For demo purposes you can only delete maximum 10 employees at a time\n");
    }

    if (!empty($primaryKeys)) {
        $callbackDeleteModel->deleteMultipleEmployees($primaryKeys);
    } else {
        return false;
    }

    return $stateParameters;
});

$output = $crud->render();
</code></pre>

The result of the above code can be found here:

`embed:demo_callback-delete-multiple`

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

    public function deleteMultipleEmployees($ids) {
        $sql = new Sql($this->adapter);

        foreach ($ids as $employeeNumber) {
            $update = $sql->update('employees');
            $update->where(['employeeNumber = ?' => $employeeNumber]);

            $update->set(['extension' => '[DELETED]']);

            $statement = $sql->prepareStatementForSqlObject($update);
            $statement->execute();
        }

        return true;
    }
}</code></pre>