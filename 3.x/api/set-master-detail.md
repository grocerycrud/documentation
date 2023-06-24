---
id: set-master-detail
title: setMasterDetail
description: Create a master detail grid for your CRUD. 
canonical: docs/set-master-detail
previous: set-csrf-token-value
next: get-state
---

# setMasterDetail

<pre><code class="language-php">setMasterDetail(string $apiUrl)</code></pre>

## Example

Customers CRUD:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');

$crud->setMasterDetail("https://full/url/path/to/orders.php");

$crud->setRead();
$crud->setClone();

$output = $crud->render();</code></pre>

Orders CRUD:

<pre><code class="language-php">$crud->setTable('orders');
$crud->unsetDatagridTitle();
$crud->unsetTools();
$crud->unsetOperations();
$crud->unsetSearchColumns(['orderNumber', 'orderDate', 'requiredDate', 'shippedDate', 'status', 'comments', 'customerNumber']);

if (!empty($_POST['master_id'])) {
    if (is_numeric($_POST['master_id'])) {
        $crud->where(['customerNumber' => $_POST['master_id']]);
    } else {
        throw new InvalidArgumentException("Invalid argument for the field 'master_id'");
    }
}

$output = $crud->render();</code></pre>

`embed:set-master-detail`