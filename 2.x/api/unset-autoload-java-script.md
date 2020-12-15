---
id: unset-autoload-java-script
title: unsetAutoloadJavaScript
permalink: docs/unset-autoload-java-script
previous: unset-add-fields
next: unset-bootstrap
---

# unsetAutoloadJavaScript


<pre><code class="language-php">unsetAutoloadJavaScript(void)</code></pre>
Unset the initial load of the GroceryCRUD so we can load it dynamically. That simply means that the Grocery CRUD will NOT load if we will not call it manually from the JavaScript code.

For example the below code:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->unsetAutoloadJavaScript();

$output = $crud->render();

// Add a custom JavaScript file to load Grocery CRUD
$output->js_files[] = base_url() . 'assets/custom/js/custom-gc-load.js'; 
</code></pre>

will output everything that it is necessary for Grocery CRUD but without the initial load. The initial call will need to be manually triggered through the code:

(JavaScript)
<pre><code class="javascript">$('.gc-container').groceryCrud();</code></pre>

So if in our example we create a button like this:

(JavaScript)
<pre><code class="javascript">// custom-gc-load.js
$(document).ready(function () {
    $('.load-grocery-crud-button').click(function () {
         $('.gc-container').groceryCrud({
            openInModal: false,
            hashEvents: false,
         });
	 $('.load-grocery-crud-button').fadeOut();
    });
});</code></pre>

(HTML)
<pre><code class="html">&lt;button class="load-grocery-crud-button btn btn-default"&gt;Press Button to load GroceryCRUD&lt;/button&gt;</code></pre>


It will output the below result:

`embed:demo_unset-autoload-javascript`

So far we have two options that you can add at the groceryCRUD JavaScript function:
<ol>
	<li>The option: <code>openInModal</code> that will enable or disable (default is enabled) the form to open in modal. Instead it will run at it's own page.</li>
	<li>The option: <code>hashEvents</code> that will enable or disable the hashtag from the URLs (really useful if other applications are also using the hashtag at the URL and you have conflicts</li>

	<li>The option: <code>actionButtons</code> that it is an array with three options: 
              	<ul>
			<li>iconCssClass</li>
			<li>label</li>
			<li>actionCallback</li>
		</ul>
   </li>
</ol> 

An example will be:

<script src="https://gist.github.com/scoumbourdis/3e0f8d775452e1a96c9fd4f23291a16e.js"></script>




