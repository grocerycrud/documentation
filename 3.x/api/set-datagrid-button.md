---
id: set-datagrid-button
title: setDatagridButton
description: setDatagridButton is used when we need to add extra action buttons on top or bottom of the datagrid.
canonical: v3.x/docs/set-datagrid-button
previous:
next:
---

# setDatagridButton

<pre><code class="language-php">setDatagridButton(string $label, string $iconName, string $url[, boolean $newTab = false[, string $position = 'top-left']])</code></pre>
<code>setDatagridButton</code> is used to add a button to the datagrid. The button can be positioned on the top or on the bottom of the datagrid. 
The function has the below arguments:
<ol>
	<li><code>label</code> is the label that the button will have. For example "Export to CSV"</li>
	<li><code>iconName</code> is the name of the icon that the button will have. We are using the icons font-awesome from
font awesome v5. For example "file-csv"</li>
	<li><code>url</code> is the URL that the button will redirect to when clicked. Keep in mind that this URL is static.</li>
	<li><code>newTab</code> is a boolean (true or false). The default value is false. This is used in case you need to open the link in a new tab</li>
	<li><code>position</code> is the position of the button in the datagrid. The default value is 'top-left'. You can set this to 'top-right', 'bottom-left', or 'bottom-right' depending on where you want the button to appear.</li>
</ol>

You can see an example of the setDatagridButton below:

<pre><code class="language-php">$crud->setDatagridButton('Add Customer', 'plus', 'https://example.com', false, 'top-right');</code></pre>

A full working example can be found below:

<pre><code class="language-php">$crud->setTable('employees');
$crud->setSubject('Employee', 'Employees');
$crud->setRelation('officeCode','offices','city');
$crud->displayAs('officeCode','City');

// The below code is just to show you how to use the datagrid button at the demo page. 
$crud->setDatagridButton('Add Office', 'plus', '#add-office-mock');

// A better real-world example would be the below line:
// $crud->setDatagridButton('Add Office', 'external-link-alt', 'https://example.com', true);
</code></pre>

You can see the result of the above code at the below datagrid. In order to see the functionality of the datagrid button, 
click the button in the top-left corner of the datagrid. You will notice that the button "Add office" will not work 
because it is just a mock button. You can see though that the button has added the #add-office-mock 
at the top of this page. Of course using this function will redirect you to the URL that you have set at a normal usage.
`embed:demo_set-datagrid-button`
