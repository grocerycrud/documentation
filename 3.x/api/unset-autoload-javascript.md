---
id: unset-autoload-javascript
title: unsetAutoloadJavaScript
description: 
canonical: docs/unset-autoload-javascript
previous: unset-add-fields
next: custom-model
---

# unsetAutoloadJavaScript

<pre><code class="language-php">unsetAutoloadJavaScript(void)</code></pre>
Unset the initial load of the GroceryCRUD so we can load it dynamically. That simply means that the Grocery CRUD will NOT load if we will not call it manually from the JavaScript code.

> Important note: To enable JavaScript events, please be aware that you need to set the configuration value
> "publish_events" to `true`. If this value is left as the default `false`, the events will not be triggered,
> so make sure to update it accordingly.

## Example

For example the below code:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->unsetAutoloadJavaScript();

$output = $crud->render();

// Add a custom JavaScript file to load Grocery CRUD
$output->js_files[] = '/assets/js/custom-gc-load.js'; 
</code></pre>

will output everything that it is necessary for Grocery CRUD but without the initial load. The initial call will need to be manually triggered through the code:

(JavaScript)
<pre><code class="language-javascript">groceryCrudLoader(document.querySelectorAll(".grocery-crud")[0]);</code></pre>

So if in our example we create a button like this:

(JavaScript)
<pre><code class="language-javascript">// custom-gc-load.js
$(document).ready(function () {
    $('.load-grocery-crud-button').click(function () {
        groceryCrudLoader(document.querySelectorAll(".grocery-crud")[0]);
	    $('.load-grocery-crud-button').fadeOut();
    });
});</code></pre>

(HTML)
<pre><code class="language-html">&lt;button class="load-grocery-crud-button"&gt;Press Button to load GroceryCRUD&lt;/button&gt;
</code></pre>


A full example will be:

<pre><code class="language-javascript">$(document).ready(function () {

	groceryCrudLoader(document.querySelectorAll(".grocery-crud")[0], {
		callbackBeforeInsert: function (currentForm) {
		    console.log('callback that is called right before the insert');
		},
		callbackBeforeUpdate: function (currentForm) {
		    console.log('callback that is called right before the update');
		},
		callbackAfterInsert: function (currentForm) {
		    console.log('callback that is called right after a successful insert');
		},
		callbackAfterUpdate: function (currentForm) {
		    console.log('callback that is called right after a successful update');
		},
		callbackBeforeDelete: function(itemIds) {  // itemIds variable is always an array
		    console.log('callback that is called right before the confirmation of the delete is pressed');
		},
		callbackAfterDelete: function(itemIds) { // itemIds variable is always an array
		    console.log('callback that is called right after a successful delete operation');
		},
		onRowUpdate: function (primaryKeyField) { // When the row is getting updated (e.g. it is not re-rendered)
		    console.log('row updated for:' + primaryKeyField);
		},
		onRowUnmount: function (primaryKeyField) { // When the row is getting removed (e.g. to destroy an instance)
		    console.log('row was unmounted for:' + primaryKeyField);
		},      
		actionButtons: [{
		 iconCssClass: 'fa fa-smile-o',
		 label: 'Smiley',
		 onClick: function (primaryKeyValue) {
		     console.log('Smiley is clicked with primary key:' + primaryKeyValue);
		 }
		}],
		// addFields, editFields, cloneFields and readFields works only
		// with the combination of: 
		// callbackAddField for addFields
		// callbackEditField for editFields... e.t.c.
		addFields: [ // works with $crud->callbackAddField
		    {
		        fieldName: 'contact_last_name',
		        onMount: function onMount() {
		            console.log('on mount!!');
		        },
		        onUnmount: function onUnmount() {
		            console.log('hmmm unmount');
		        }
		    }
		],
		editFields: [ // works with $crud->callbackEditField
		    {
		        fieldName: 'contact_last_name',
		        onMount: function onMount() {
		            console.log('on mount!!');
		        },
		        onUnmount: function onUnmount() {
		            console.log('hmmm unmount');
		        }
		    }
		],
		cloneFields: [ // works with $crud->callbackCloneField
		    {
		        fieldName: 'contact_last_name',
		        onMount: function onMount() {
		            console.log('clone on mount!!');
		        },
		        onUnmount: function onUnmount() {
		            console.log('clone on unmount');
		        }
		    }
		],
		readFields: [ // works with $crud->callbackReadField
		    {
		        fieldName: 'contact_last_name',
		        onMount: function onMount() {
		            console.log('read on mount!!');
		        },
		        onUnmount: function onUnmount() {
		            console.log('read on unmount');
		        }
		    }
		]
	});
});</code></pre>




