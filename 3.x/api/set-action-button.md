---
id: set-action-button
title: setActionButton
description: setActionButton is used when we need to add extra action buttons to the rows of the datagrid.  
permalink: docs/set-action-button
previous: default-ordering
next: set-action-button-multiple
---

# setActionButton

<pre><code class="language-php">setActionButton(string $label, string $cssClassIcon,callable $urlCallback[, boolean $newTab])</code></pre>
<code>setActionButton</code> is used when we need to add extra action buttons to the rows of the datagrid. The functionality is simple and it takes the below arguments:
<ol>
	<li><code>label</code> is the label that the button will have. For example "Photos"</li>
	<li><code>cssClassIcon</code> is css that the icon at the left will have. You can use the default CSS from font-awesome but you can also use your own. For example "fa fa-image"</li>
	<li><code>urlCallback</code> is the callback that it will be called in every row so you can get the custom URL that the button will have. Have in mind that this will redirect you to another page</li>
	<li><code>newTab</code> is a boolean (true or false). The default value is false. This is used in case you need to open the link in new tab</li>
</ol>

You can see an example of the setActionButton below:

<pre><code class="language-php">$crud->setActionButton('Avatar', 'fa fa-user', function ($row) {
    return '/view_avatar/' . $row->url;
}, true);</code></pre>

A full working example can be found below:

<pre><code class="language-php">$crud->setTable('employees');
$crud->setSubject('Employee', 'Employees');
$crud->setRelation('officeCode','offices','city');
$crud->displayAs('officeCode','City');
$crud->unsetDelete();

$crud->setActionButton('Avatar', 'fa fa-user', function ($row) {
    return '#/avatar/' . $row->employeeNumber;
}, false);</code></pre>

You can see the result of the above code here. In order to see the functionality of the action buttons, press the More button in any of the rows.
`embed:demo_set-action-button`
