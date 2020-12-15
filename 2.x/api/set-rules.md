---
id: set-rules
title: setRules
permalink: docs/set-rules
previous: set-rule
next: set-sequence-name
---

# setRules


<pre><code class="language-php">setRules(array $rules)</code></pre>
<code>setRules</code> method is to combine multiple <a href="/enterprise/api-and-function-list/setRule">setRule</a> methods into one. The syntax is simple. You just need to provide an array with the below form:
<pre><code class="language-php">[
    'fieldName' => 'fieldName',
    'rule' => 'rule',
    'parameters' => 'parameters'
]</code></pre>

For example:


<pre><code class="language-php">$crud->setRules(
    [
        [
            'fieldName' => 'creditLimit',
            'rule' => 'min',
            'parameters' => '100'
        ],
        [
            'fieldName' => 'postalCode',
            'rule' => 'lengthBetween',
            'parameters' => ['4','6']
        ],
    ]
);</code></pre>

The above code is equivalent to:

<pre><code class="language-php">$crud->setRule('creditLimit', 'min', '100');
$crud->setRule('postalCode', 'lengthBetween', ['4','6']);</code></pre>

For more information about the setRule please read the <a href="/enterprise/api-and-function-list/setRule">setRule</a> method

A full working example can be found below:
<pre><code class="language-php">
$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->setRules(
    [
        [
            'fieldName' => 'creditLimit',
            'rule' => 'min',
            'parameters' => '100'
        ],
        [
            'fieldName' => 'postalCode',
            'rule' => 'lengthBetween',
            'parameters' => ['4','6']
        ],
    ]
);

$output = $crud->render();</code></pre>

You can try the validation rules below. Try to add a creditLimit lower than 100 or try to add a postalCode that doesn’t have length between 4-6 digits. As you will also notice, empty values are acceptable. In case we need a validation of a field to be required although you can use the Valitron required, it is recommended to use the GroceryCRUD function <a href="/enterprise/api-and-function-list/requiredFields" target="_blank">requiredFields</a> instead of the rule.
`embed:demo_set-rules`