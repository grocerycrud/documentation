---
id: set-rule
title: setRule
description: The setRule is the validation rule that you add for the insert/update form.
canonical: docs/set-rule
previous: set-relation-nto-n
next: set-rules
---

# setRule

The <code>setRule</code> is the validation rule that you add for the insert/update form.

<pre><code class="language-php">setRule(string $fieldName, string $rule[, array $parameters])</code></pre>

We wanted to use a very simple to use library and we chose 
<a href="https://github.com/vlucas/valitron" target="_blank" rel="noopener noreferrer">Valitron</a>. 
You can see all parameters that you can add for valitron for the <code>rule</code> method 
at: <a href="https://github.com/vlucas/valitron" target="_blank" rel="noopener noreferrer">https://github.com/vlucas/valitron</a>. Have in mind that the fieldName however comes <strong>first</strong> and the rules as a <strong>second</strong> parameter. We did that on purpose in order to have consistency with all the GroceryCRUD functions.

## Examples

<pre><code class="language-php">$crud-&gt;setRule('nickname', 'slug')</code></pre>
<strong>Important notice:</strong> The <strong>only</strong> difference that the GroceryCrud <code>setRule</code> is 
having by the <code>rule</code> of Valitron is that if you need a 4rd parameter then you will need to add it as an array. 
This was the only proper way that grocery CRUD could handle it. Valitron is using <code>func_get_args()</code> and 
GroceryCRUD enterprise is avoiding using that as it is easy to lose control of the parameters 
(a lesson well learned from grocery CRUD Free edition).

So for example instead of the Valitron rule:
<pre><code class="language-php">rule('fieldName', 'lengthBetween', '4','6');</code></pre>
you should write it instead:
<pre><code class="language-php">$crud-&gt;setRule('fieldName', 'lengthBetween', ['4', '6'])</code></pre>
If you don't need a 4rd parameter then you can keep using it as the Valitron is. For example:
<pre><code class="language-php">$crud-&gt;setRule('credit_card', 'creditCard', ['visa', 'mastercard'])</code></pre>


## Create custom rule
Valitron as library is very simplistic and powerful at the same time. You can create your own custom rules with an easy way. So for example if you need to create a custom rule you can easily do it with the below steps:

<strong>Step1.</strong> Create the custom rule in your function. In our example let's say that we want to have a custom validation that a phone is acceptable only if it will start with +30. In our case we will add this before the <code>$crud->render()</code> is called. We are suggesting to add it at the beginning of your function. So in our example we will have:

<pre><code class="language-php">\Valitron\Validator::addRule('checkGreekPhoneNumber', function($field, $value, array $params, array $fields) {

	if (strstr($value, '+30')) {
		return true;
	}

    return false;
}, 'must start with +30');</code></pre>

Have in mind that as Grocery CRUD is automatically adding the label, you don't need to add the name of the field name.

<strong>Step2.</strong> Add the extra rule for the field that you need. For example in our case:

<pre><code class="language-php">$crud->setRule('mobile_phone', 'checkGreekPhoneNumber');
$crud->setRule('home_phone', 'checkGreekPhoneNumber');</code></pre>

At the above example the way that this will work is that when a field is inserted or updated then the custom set rule will take place. Just to make it more full as an example this is how your code will look like:

<pre><code class="language-php">\Valitron\Validator::addRule('checkGreekPhoneNumber', function($field, $value, array $params, array $fields) {

	if (strstr($value, '+30')) {
		return true;
	}

    return false;
}, 'must start with +30');
...

$crud->setTable('customers');
...
$crud->displayAs('mobile_phone', 'Mobile');
$crud->displayAs('home_phone', 'Home Number');
...
$crud->setRule('mobile_phone', 'checkGreekPhoneNumber');
$crud->setRule('home_phone', 'checkGreekPhoneNumber');
...
$output = $crud->render();
</code></pre>

So at the above example if the mobile_phone for example will not start with the string <code>'+30'</code> (or in other words the validation will return false) then an error will be displayed at the screen with the message: <code>"Mobile must start with +30"</code>

## Full example

The rules are very simple to use. You can see a full example below:
<pre><code class="language-php">$crud-&gt;setTable('customers');
$crud-&gt;setSubject('Customer', 'Customers');
$crud-&gt;columns(['customerName','phone','addressLine1','creditLimit']);

$crud-&gt;setRule('creditLimit', 'min', '100');
$crud-&gt;setRule('postalCode', 'lengthBetween', ['4','6']);

$output = $crud-&gt;render();</code></pre>
You can try the validation rules below. Try to add a creditLimit lower than 100 or try to add a postalCode that doesn't have length between 4-6 digits. As you will also notice, empty values <strong>are</strong> acceptable. In case we need a validation of a field to be required although you can use the Valitron required, it is recommended to use the GroceryCRUD function <a href="/enterprise/api-and-function-list/requiredFields">requiredFields</a> instead of the rule.
`embed:demo_set-rule`