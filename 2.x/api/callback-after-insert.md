---
id: callback-after-insert
title: callbackAfterInsert
permalink: docs/callback-after-insert
previous: callback-after-delete-multiple
next: callback-after-update
---

# callbackAfterInsert

<pre><code class="language-php">callbackAfterInsert(callable $callback)</code></pre>
The callback that will be used right after the insert of the data. There are basically two types of values that the developer will have available for the callback:
<ol>
 	<li>The <code>insertId</code>: This is the primary key field id. After the insert this is available to use it</li>
 	<li>The <code>data</code>: These are the <strong>filtered </strong>data from the insert</li>
</ol>

More specifically, below you can see an example of the <code>$stateParameters</code> variable for the callbackAfterInsert:
<pre><code class="language-php">$stateParameters = (object)[
    'insertId' => '1234', //primary key value after insert
    'data' => [ // data to insert
        'customerName' => 'John',
        'phone' => '1234567890',
        ...
    ]
];</code></pre>

## Example

A full example is also available for you to understand better. 
At the below example we are updating the customer name after the insert and we are adding 
the string "[NEW] " at the beginning of the name.
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->callbackAfterInsert(function ($stateParameters) use ($addFieldsModel) {
    $addFieldsModel->updateCustomerName($stateParameters->insertId);

    return $stateParameters;
});</code></pre>

The above code will give you the below results:

`embed:demo_callback_after_insert`

`$addFieldsModel` is using Grocery CRUD [Custom Model](/docs/custom-model) but you can also use your own custom model.

For reference the code for `AddFields` class can be found below:

<pre><code class="language-php">&lt;?php
namespace App\Models;
use GroceryCrud\Core\Model;
use Zend\Db\Sql\Sql;

class AddFields extends Model {
    public function updateCustomerName($customerId) {

        if (!is_numeric($customerId)) {
            return false;
        }

        $sql = new Sql($this->adapter);
        $select = $sql->select();
        $select->where(['customerNumber = ?' => $customerId]);
        $select->from('customers');

        $row = $this->getRowFromSelect($select, $sql);

        if ($row === null) {
            return false;
        }

        $sql = new Sql($this->adapter);
        $update = $sql->update('customers');
        $update->where(['customerNumber = ?' => $customerId]);

        $update->set([
            'customerName' => ('[NEW] ' . $row[0]['customerName'])
        ]);

        $statement = $sql->prepareStatementForSqlObject($update);
        return $statement->execute();
    }
}</code></pre>