---
id: set-action-button-multiple
title: setActionButtonMultiple
description: Action button for multiple selections with checkboxes.
canonical: docs/set-action-button-multiple
previous: set-action-button
next: set-export
enterprise: 1
version: 2.8.12
---

# setActionButtonMultiple

<pre><code class="language-php">setActionButtonMultiple(string $label, string $cssClassIcon, string $url[, boolean $newTab[, string $idFieldQueryName[, string $querySeparator]]])</code></pre>
<code>setActionButtonMultiple</code> is used when we need to add extra action buttons for multiple selections on the datagrid. 
The functionality is simple, and it takes the below arguments:
<ol>
	<li><code>label</code> is the label that the button will have. For example "Photos"</li>
	<li><code>cssClassIcon</code> is css that the icon at the left will have. You can use the default CSS from font-awesome but you can also use your own. For example "fa fa-image"</li>
    <li><code>$url</code> is the URL that is used for the batch action. Please keep in mind that we also send the ids as a query parameter array (e.g. ?id[]=2&id[]=5)</li>
    <li><code>$newTab</code>: if the URL will open in a new tab. Default: <code>false</code></li>
    <li><code>$idFieldQueryName</code> is used when we would like to change the name of the on the query parameters. Default: <code>id</code></li>
    <li><code>$querySeparator</code> is used when we would like to change the query separator. It is most commonly used when we already have a URL parameter in our URL.</li>
</ol>

You can see a basic example of the setActionButtonMultiple below:

<pre><code class="language-php">$url = 'https://example.com/view_avatar';
$crud->setActionButtonMultiple('Avatar', 'fa fa-user', $url, true);</code></pre>

A full working example can be found below:

<pre><code class="language-php">$crud->setTable('employees');
$crud->setSubject('Employee', 'Employees');
$crud->setRelation('officeCode','offices','city');
$crud->displayAs('officeCode','City');
$crud->unsetEdit();

// For demo purposes we are using the # so we will not have a new URL redirection
$crud->setActionButtonMultiple('Avatar', 'fa fa-user', '#/avatar/');

// Although this is not required, it is better for a usability perspective to 
// also include the button for a single use
$crud->setActionButton('Avatar', 'fa fa-user', function ($row) {
    return '#/avatar/' . $row->employeeNumber;
}, false);
</code></pre>

You can see the result of the above code here. In order to check the functionality you will need to select any number
of rows from the checkboxes on the left
`embed:demo_set-action-button-multiple`
