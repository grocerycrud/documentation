---
id: callback-delete
title: callbackDelete
permalink: docs/callback-delete
previous: callback-column
next: callback-delete-multiple
---

# callbackDelete


<pre><code class="language-php">callbackDelete(callable $callback)</code></pre>
The basic usage of <code>callbackDelete</code> is when you want to skip the delete functionality. If the <code>callbackDelete</code> is called then that means that the actual default delete functionality of Grocery CRUD Enterprise will not triggered.

<p class="bg-warning" style="padding:10px;"><strong><span class="fa fa-exclamation-triangle"></span> Warning!</strong> Please be aware that you should also add a callback into the callbackDeleteMultiple in order to make sure that the callback is always triggered. For more also check: <a href="https://www.grocerycrud.com/enterprise/api-and-function-list/callbackDeleteMultiple">callbackDeleteMultiple</a> documentation</p>

The callbackDelete is getting as a parameter a callback. This callback has as parameter the below:
- primaryKeyValue 

For example:

<pre><code class="language-php">$crud->callbackDelete(function ($stateParameters) {
    // Your code will run here
    return $stateParameters;
});</code></pre>

## Example

Below you can see a full example. At the below example we are skipping completely the delete functionality and instead we are updating the row by adding at the title the word "[DELETED]"

<pre><code class="language-php">$crud->setTable('employees');
$crud->setSubject('Employee', 'Employees');
$crud->setRelation('officeCode','offices','city');
$crud->displayAs('officeCode','City');

// Unsetting the multiple delete for this example. If we need it we also need to
// consider to add a $crud->callbackDeleteMultiple callback
$crud->unsetDeleteMultiple();

$crud->callbackDelete(function ($stateParameters) use ($callbackDeleteModel) {
    $callbackDeleteModel->deleteEmployee($stateParameters->primaryKeyValue);

    return $stateParameters;
});

$output = $crud->render();</code></pre>

Try to remove one row at the below example to see exactly the functionality of the above example:
`embed:demo_callback-delete`

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