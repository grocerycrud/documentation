---
id: callback-update
title: callbackUpdate
description: The callback is used when we need to replace the default update functionality.
canonical: docs/callback-update
previous: callback-edit-form
next: edit-fields
---

# callbackUpdate

<pre><code class="language-php">callbackUpdate(callable $callback)</code></pre>
The function <code>callbackUpdate</code> is used when we need to completely skip the default update functionality of Grocery CRUD Enterprise. The usage is simple, for example:

<pre><code class="language-php">$crud->callbackUpdate(function ($stateParameters) {
    // Your code goes here

    return $stateParameters;
});</code></pre>

You can see a full working example below:

<pre><code class="language-php">$crud->setTable('orders');
$crud->setSubject('Order', 'Orders');
$crud->setRelation('customerNumber','customers','contactLastName');

$crud->callbackUpdate(function ($stateParameters) use ($callbackUpdateModel) {
    $updateString = '[Update - ' .date('d M Y') . '] ';

    if (!strstr($stateParameters->data['comments'], $updateString)) {
        $stateParameters->data['comments'] = $updateString . $stateParameters->data['comments'];
    }

    // As we are skipping the actual update we will also need to update the data as well
    $callbackUpdateModel->updateOrder($stateParameters->data, $stateParameters->primaryKeyValue);

    return $stateParameters;
});</code></pre>

With the below live example you can see that when we are updating any row then the text "[Update - day Month]" is prepend at the beginning of the field comments.

`embed:demo_callback-update`

`$callbackUpdateModel` is using Grocery CRUD [Custom Model](/docs/custom-model) but you can also use your own custom model.

For reference the code for `CallbackUpdate` class can be found below:

<pre><code class="language-php">&lt;?php
namespace App\Models;
use GroceryCrud\Core\Exceptions\Exception;
use GroceryCrud\Core\Model;
use Zend\Db\Sql\Sql;

class CallbackUpdate extends Model {
    public function updateOrder($data, $primaryKeyValue) {
        // Always make sure that we validate our data
        $fields = ['orderDate','requiredDate','shippedDate','status','comments','customerNumber'];

        // Make sure that the update data has the exact numbers of inputs
        if (count($data) !== count($fields)) {
            throw new Exception("Wrong input");
        }

        // Make sure that we validate all of our inputs
        foreach ($data as $fieldName => $fieldValue) {
            if (!in_array($fieldName, $fields)) {
                throw new Exception("Wrong input");
            }
        }

        // And lastly also validating the $primaryKeyValue
        if (!is_numeric($primaryKeyValue)) {
            throw new Exception("Wrong input");
        }

        $sql = new Sql($this->adapter);
        $update = $sql->update('orders');
        $update->where([
            'orderNumber = ?' => $primaryKeyValue
        ]);

        $update->set($data);

        $statement = $sql->prepareStatementForSqlObject($update);

        return $statement->execute();
    }
}</code></pre>