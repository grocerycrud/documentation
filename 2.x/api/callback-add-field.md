---
id: callback-add-field
title: callbackAddField
permalink: docs/callback-add-field
previous: 
next: callback-add-form
---

# callbackAddField

<pre><code class="php">callbackAddField(string $fieldName, callable $callback)</code></pre>
Create a custom field with a callback for add form. As this is add form, there is not any parameters added to the callback. You can return any custom HTML you wish. 

## Full Example
<pre><code class="php">$crud->callbackAddField('contact_last_name', function ($fieldType, $fieldName) {
    /** $fieldType will look like this:
     GroceryCrud\Core\Model\ModelFieldType Object
    (
        [isNullable] => 
        [dataType] => varchar
        [defaultValue] => 
        [permittedValues] => 
        [options] => stdClass Object
            (
                [maxLength] => 50
            )
        [isRequired] => 
        [isReadOnly] => 
        [isSearchable] => 1
    )*/

    return '&lt;input class="form-control" name="' . $fieldName . '" type="text" value=""&gt;';
});</code></pre>

Have in mind that from PHP 5.4 and later there is an extra functionality with keywork <code>use</code>, so that means that you can pass any extra parameters at the callback from outside the callback if you wish it. For example:

<pre><code class="php">
$username = 'john';
$crud->callbackAddField('contact_telephone_number', function () use ($username) {
     // You have access now at the extra custom variable $username
    return '+30 &lt;input name="telephone_number"  /&gt; for: ' . $username ;
});</code></pre>

<strong>Notice 1:</strong> Grocery CRUD Enterprise is all about performance and hence we are caching at the first call the callback add field. That means, that you can't change the callaback add field without a refresh. An example in order to understand what we mean is if you use the below callback:

<pre><code class="php">
$crud->callbackAddField('contact_telephone_number', function () {
    // Warning: Do NOT use this code
    return time();
});</code></pre>
you will see the current time at the field only at the first time that you are pressing the button "Add". If you press the button again then the time will not change as this is cached at the browser for better performance.
 
<strong>Notice 2:</strong> Grocery CRUD Enterprise is also all about security so we are obliged to inform you that the callbackAddField is using the: <a href="https://facebook.github.io/react/docs/dom-elements.html#dangerouslysetinnerhtml" target="_blank" rel="noopener noreferrer">dangerouslySetInnerHTML</a> function of reactJS. As you can understand from the name, this may be very dangerous if it is not used properly. We are suggesting to use it mainly in admin environments and make sure that you are always filtering your data at the callback. This was the only way that we could enable the functionality of callbackAddField and you have to be aware of this warning before using it.