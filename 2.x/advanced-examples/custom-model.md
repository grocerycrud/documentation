---
id: custom-model
title: Custom Model
permalink: docs/custom-model
previous: 
next:
---

# How to create a custom model

There are many cases that we need to use Grocery CRUD with a custom query. The most common scenario is when we have complicated queries with multiple joins in the database. With the functionality of setModel you are able to create your own custom model for custom queries.

By using custom models we can have the below benefits:
<ol>
 	<li>Control all of your queries. By simply putting it, any new request (new queries... e.t.c.) that you are getting from your business is achievable.</li>
 	<li>Organising your code better. Sometimes it is better to create a file for a custom query, just in case at the future the query will get more complicated. With that good practice in mind you can easily have the freedom to create some custom queries, without having in mind the complexity of the query.</li>
 	<li>It is more understandable from new users that this is the model that is used for your CRUD.</li>
</ol>
With the above benefits in mind, let's see first of all how we can create a custom model. All the documentation for custom model, can also be found at [setModel](/docs/set-model) documentation.

## A full example in Codeigniter 3 Framework

The below example is with Codeigniter framework but of course as different frameworks has different queries, you can use your own one. So first of all we are creating a file with name: CustomersModel.php. We did create the code based on <a href="https://gist.github.com/scoumbourdis/2b75b1910b343ea00ce1fb310fffe02c" target="_blank">this generic model</a> that you can copy in order to start with.

<pre><code class="language-php">&lt;?php
//CustomersModel.php

use GroceryCrud\Core\Model;
use GroceryCrud\Core\Model\ModelFieldType;

class CustomersModel extends Model {

    protected $ci;
    protected $db;

    function __construct($databaseConfig) {
        $this->setDatabaseConnection($databaseConfig);

        $this->ci = & get_instance();
        $this->db = $this->ci->db;
    }

    public function getFieldTypes($tableName)
    {
        $fieldTypes = parent::getFieldTypes($tableName);

        $fullNameFieldType = new ModelFieldType();
        $fullNameFieldType->dataType = 'varchar';

        $countOrdersFieldType = new ModelFieldType();
        $countOrdersFieldType->dataType = 'varchar';

        $fieldTypes['fullname'] = $fullNameFieldType;
        $fieldTypes['count_orders'] = $countOrdersFieldType;

        return $fieldTypes;
    }

    public function getOne($id)
    {
        $customer = parent::getOne($id);

        $this->db->select('COUNT(*) as count_orders');
        $this->db->where('customerNumber', $id);
        $customer['count_orders'] = $this->db->get('orders')->row()->count_orders;

        return $customer;
    }

    protected function _getQueryModelObject() {
        $order_by = $this->orderBy;
        $sorting = $this->sorting;

        // All the custom stuff here
        $this->db->select('customers.customerNumber, CONCAT(customerName, \' \' ,contactLastName) as fullname, phone, city, country, COUNT(*) as count_orders', false);
        $this->db->join('orders', 'orders.customerNumber = customers.customerNumber', 'left');
        $this->db->group_by('customers.customerNumber');

        if ($order_by !== null) {
            $this->db->order_by($order_by. " " . $sorting);
        }

        if (!empty($this->_filters)) {
            foreach ($this->_filters as $filter_name => $filter_value) {
                if ($filter_name !== 'fullname') {
                    if (is_array($filter_value)) {
                        foreach ($filter_value as $value) {
                            $this->db->like($filter_name, $value);    
                        }
                    } else {
                        $this->db->like($filter_name, $filter_value);
                    }                    
                } else {
                    if (is_array($filter_value)) {
                        foreach ($filter_value as $value) {
                            $this->db->like('CONCAT(customerName, \' \' ,contactLastName)', $value);
                        }
                    } else {
                        $this->db->like('CONCAT(customerName, \' \' ,contactLastName)', $filter_value);
                    }   
                }
            }
        }

        if (!empty($this->_filters_or)) {
            foreach ($this->_filters_or as $filter_name => $filter_value) {
                $this->db->or_like($filter_name, $filter_value);
            }
        }

        $this->db->limit($this->limit, ($this->limit * ($this->page - 1)));
        return $this->db->get($this->tableName);
    }

    public function getList() {
        return $this->_getQueryModelObject()->result_array();
    }

    public function getTotalItems()
    {
        if (!empty($this->_filters)) {
            return $this->_getQueryModelObject()->num_rows();
        }

        // If we don't have any filtering it is faster to have the default total items
        // In case this is more complicated you can add your own code here
        return parent::getTotalItems();
    }
}</code></pre>

<strong>Please notice:</strong>
As in Codeigniter 3 we are not using any namespaces, we did simplify the process and added the model into the folder: <code>application/models/</code>. But as Codeigniter doesn't have autoload either, the simplest way to call the <code>CustomersModel.php</code> is by using our good old <code>include</code> function. So for example if your controller is looking like that:

<pre><code class="language-php">class Admin extends CI_Controller { 
        ...

	public function customers() {
             
        }

        ...
}</code></pre>

You should do something like that:

<pre><code class="language-php">class Admin extends CI_Controller { 
        ...

	public function customers() {
            $crud = $this->_getGroceryCrudEnterprise();

            $crud->setTable('customers');

            // Please notice that the APPPATH is used only in Codeigniter Framework
            include(APPPATH . 'models/CustomersModel.php');
            $db = $this->_getDbData();
            // If we are not using namespaces, we need to make sure that we are starting with "\" as
            // this way we can guarantee that it will not fail in case we will use namespaces at the future
            $model = new \CustomersModel($db);
            $crud->setModel($model);

            $crud->setSubject('Customer', 'Customers');
            $crud->columns(['customerName','contactLastName','phone','city','country','salesRepEmployeeNumber','creditLimit']);
            $crud->displayAs('salesRepEmployeeNumber','from Employeer')
                 ->displayAs('customerName','Name')
                 ->displayAs('contactLastName','Last Name');
             $crud->setRelation('salesRepEmployeeNumber','employees','lastName');

             $output = $crud->render();

             $this->_example_output($output);
        }

        ...
}</code></pre>


As you can also see from the code we did add two extra columns:
<ol>
 	<li><code>fullname</code> that it is the concatenation with the first/last name</li>
 	<li><code>count_orders</code> that the result is coming from a join of the table orders</li>
</ol>
To implement the above file, then you will simply need the below 2 lines of code:
<pre><code class="language-php">$model = new \CustomersModel($db);
$crud-&gt;setModel($model);</code></pre>
And that's basically it! No more complicated than that. You can see a full example of a custom query below:
<pre><code class="language-php">$crud-&gt;setTable('customers');

$model = new \CustomersModel($db);
$crud-&gt;setModel($model);

$crud-&gt;unsetAdd();
$crud-&gt;setSubject('Customer', 'Customers');
$crud-&gt;columns(['fullname', 'phone', 'country', 'count_orders']);
$crud-&gt;fields(['customerName', 'contactLastName', 'phone', 'country', 'count_orders']);
$crud-&gt;readOnlyFields(['count_orders']);
$crud-&gt;displayAs('count_orders','Orders');

$output = $crud-&gt;render();</code></pre>