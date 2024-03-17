---
id: set-model
title: setModel
description: Changing the default model with a custom one. 
canonical: docs/set-model
previous: set-dependent-relation
next: get-model
---

# setModel


<pre><code class="language-php">setModel(\GroceryCrud\Core\Model\ModelInterface $model);</code></pre>

By default GroceryCRUD is using a Model that already automated for you pretty much everything (check \GroceryCrud\Core\Model for more). However there are many cases that there are too complex queries that you need to have. In that case you can add a custom model to execute. The syntax is simple:

<pre><code class="language-php">$model = new customModel($db);
$crud->setModel($model);</code></pre>

## Example

A more specific example can be the below:

<pre><code class="language-php">$crud->setModel(new customModel($db));

$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName', 'country', 'state', 'addressLine1']);

$output = $crud->render();</code></pre>

where <code>$db</code> is the config variable for the database and where customModel is:

<pre><code class="language-php">&lt;?php 

use GroceryCrud\Core\Model;

class customModel extends Model {

    public function extraWhereStatements($select)
    {
        $select->where("customers.country = 'USA'");
        return $select;
    }
    
}</code></pre>

<strong>Note:</strong> There is a separate section that you can find at the Advanced Examples [How to create a custom model](/docs/custom-model) that 
is covering how to create your own unique models for advanced needs. 

This example is to help you understand only the basic usage

The result of the above code is:
`embed:demo_set-model`