---
id: callback-insert
title: callbackInsert
permalink: docs/callback-insert
previous: callback-edit-form
next: callback-read-field
---

# callbackInsert

<pre><code class="language-php">callbackInsert(callback $callback)</code></pre>
The functionality of <code>callbackInsert</code> is used when we need to completely skip the default functionality of the insert of Grocery CRUD Enterprise. The only requirement at this method is to return an insertId as we need it for the <code>callbackAfterInsert</code> and also the API will break if there is not an insertId to return.

An example can be found here:
<pre><code class="language-php">$crud->callbackInsert(function ($stateParameters) {
    // Your custom insert goes here

    // Required
    $stateParameters->insertId = '1234';

    return $stateParameters;
});</code></pre>

## Example

Below we have a full example to understand it better. At the below example we are adding the date at the comments just for the proof that we are changing the data on insert. Please have in mind that the default insert is skipped, so that means that in case you don't do an actual insert then Grocery CRUD will not do it for you!

<pre><code class="language-php">$crud->setTable('orders');
$crud->setSubject('Order', 'Orders');
$crud->setRelation('customerNumber','customers','contactLastName');

$crud->callbackInsert(function ($stateParameters) use ($callbackInsertModel) {
    $stateParameters->data['comments'] = '[Insert date - ' .date('d M Y') . '] '. $stateParameters->data['comments'];

    // As we are skipping the actual insert we will need to insert by our own
    $insertId = $callbackInsertModel->insertOrder($stateParameters->data);

    // Required
    $stateParameters->insertId = $insertId;

    return $stateParameters;
});
$output =  $crud->render();</code></pre>

Try adding any order and write any comments. You will notice that your comment will be appended with the current date (of the server).
`embed:demo_callback-insert`

`$callbackInsertModel` is using Grocery CRUD [Custom Model](/docs/custom-model) but you can also use your own custom model.

For reference the code for `CallbackInsert` class can be found below:

<pre><code class="language-php">&lt;?php
namespace App\Models;
use GroceryCrud\Core\Exceptions\Exception;
use GroceryCrud\Core\Model;
use Zend\Db\Sql\Sql;

// This specific custom model example is for Grocery CRUD Enterprise edition
class CallbackInsert extends Model {
    public function insertOrder($data) {
        // Always make sure that we validate our data
        $fields = ['orderDate','requiredDate','shippedDate','status','comments','customerNumber'];

        // Make sure that the insert data has the exact numbers of inputs
        if (count($data) !== count($fields)) {
            throw new Exception("Wrong input");
        }

        // Make sure that we validate all of our inputs
        foreach ($data as $fieldName => $fieldValue) {
            if (!in_array($fieldName, $fields)) {
                throw new Exception("Wrong input");
            }
        }

        $sql = new Sql($this->adapter);
        $insert = $sql->insert('orders');
        $insert->values($data);

        $statement = $sql->prepareStatementForSqlObject($insert);

        $result = $statement->execute();

        // insertId value
        return $result->getGeneratedValue();
    }
}</code></pre>