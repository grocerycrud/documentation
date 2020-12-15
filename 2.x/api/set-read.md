---
id: set-read
title: setRead
permalink: docs/set-read
previous: set-print
next: set-relation
---

# setRead


<pre><code class="language-php">setRead(void)</code></pre>
The view of the form (read only) is false by default. In order to enable the "View" button at your grid you will need to use the function <code>setRead</code>. 

The usage is simple:
<pre><code class="language-php">$crud->setRead()</code></pre>

You can see a simple and fully working example below:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);
$crud->setRead();

$output = $crud->render();</code></pre>

The result of the above code can be found below. As you can also see in order to have more space the grid is creating the "More" button in order to fit efficiently the "View" Button.

`embed:demo_set-read`