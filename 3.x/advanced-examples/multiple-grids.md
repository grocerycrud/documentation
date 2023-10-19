---
id: multiple-grids
title: Multiple Grids
description: Documentation for multiple CRUD into one page.
canonical: docs/multiple-grids
previous: 
next:
---

# Multiple grids

In order to have multiple grids into one page, you will need to consider two things:
<ol>
 	<li>The first thing is that the output is nothing more than the initial data and the url path. All the rest you can implement it at the specified URL</li>
 	<li>The JavaScript and the CSS is common. This means that you will need to load the JavaScript and the CSS only once</li>
</ol>
With those two in mind, we can give you a simple example of how the files will look like with a simple native php example:
<pre><code class="language-php">&lt;?php
// both.php
include("vendor/autoload.php");

use GroceryCrud\Core\GroceryCrud;

$database = include('database.php');
$config = include('config.php');

$crud = new GroceryCrud($config, $database);

$crud-&gt;setApiUrlPath('/films.php');

$output = $crud-&gt;render();

$js_files = $output-&gt;js_files;

$output = $output-&gt;output;

$crud2 = new GroceryCrud($config, $database);
$crud2-&gt;setApiUrlPath('/customers.php');

$output2 = $crud2-&gt;render();

$output .= '&lt;br/&gt;' . $output2-&gt;output;

include('view.php');</code></pre>
Let's go and explain line by line what the above code is doing.
The code:
<pre><code class="language-php">include("vendor/autoload.php");

use GroceryCrud\Core\GroceryCrud;

$database = include('database.php');
$config = include('config.php');

$crud = new GroceryCrud($config, $database);</code></pre>
Is initialising our first CRUD as we already know.

The code:
<pre><code class="language-php">$crud-&gt;setApiUrlPath('/films.php');</code></pre>
Is simply telling to Grocery CRUD that it will not use the default path (that in our case is /both.php) but instead it will use the path: <code>/films.php</code>

Then the below lines:
<pre><code class="language-php">$output = $crud-&gt;render();

$js_files = $output-&gt;js_files;

$output = $output-&gt;output;</code></pre>
will collect the output, the CSS files and the JS to be rendered. As we are always doing.

The below code:
<pre><code class="language-php">$crud2 = new GroceryCrud($config, $database);
$crud2-&gt;setApiUrlPath('/customers.php');

$output2 = $crud2-&gt;render();

$output .= '&lt;br/&gt;' . $output2-&gt;output;</code></pre>
Is initialising a <strong>second</strong> crud and at the render we are just append it to the other CRUD. Of course the <code>$output2-&gt;output</code> can be used for your own purposes in a completely different way. We are using a simply <code>&lt;br/&gt;</code> for the simplicity of the example. As you can see the JavaScript and the CSS files are not getting collected again as they are common with the first CRUD. And then lastly the code:
<pre><code class="language-php">include('view.php');</code></pre>
is simply rendering the JS, CSS and output files.

Where view.php is the below code:
<pre><code class="language-php">&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta charset="utf-8" /&gt;
    &lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;

&lt;/head&gt;
&lt;body&gt;
&lt;div style="padding: 20px 10px;"&gt;
    &lt;?php echo $output; ?&gt;
&lt;/div&gt;
&lt;?php foreach($js_files as $file): ?&gt;
    &lt;script src="&lt;?php echo $file; ?&gt;"&gt;&lt;/script&gt;
&lt;?php endforeach; ?&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>
<code>films.php</code> :
<pre><code class="language-php">&lt;?php
// films.php
include("vendor/autoload.php");

use GroceryCrud\Core\GroceryCrud;

$database = include('database.php');
$config = include('config.php');

$crud = new GroceryCrud($config, $database);

$crud-&gt;setTable('film');
$crud-&gt;setSubject('Film', 'Films');
$crud-&gt;setRead();
$crud-&gt;setRelationNtoN('actors', 'film_actor', 'actor', 'film_id', 'actor_id', 'fullname');
$crud-&gt;setRelationNtoN('categories', 'film_category', 'category', 'film_id', 'category_id', 'name');

$output = $crud-&gt;render();

if ($output-&gt;isJSONResponse) {
    header('Content-Type: application/json; charset=utf-8');
    echo $output-&gt;output;
    exit;
} else {
    throw new \Exception('Wrong data');
}
</code></pre>
and <code>customers.php</code> :
<pre><code class="language-php">&lt;?php
// customers.php
include("vendor/autoload.php");

use GroceryCrud\Core\GroceryCrud;

$database = include('database.php');
$config = include('config.php');

$crud = new GroceryCrud($config, $database);

$crud-&gt;setTable('customers');
$crud-&gt;setSubject('Customer', 'Customers');
$crud-&gt;setRead();

$output = $crud-&gt;render();

if ($output-&gt;isJSONResponse) {
    header('Content-Type: application/json; charset=utf-8');
    echo $output-&gt;output;
    exit;
} else {
    throw new \Exception('Wrong data');
}</code></pre>
All the above example can of course be written with a much smarter and optimised way, especially when you are using multiple grids all the time and you also hate copy-pasting the same code again and again (I do!)

## Working Example

So let's have a real example at this page. As you've already have guessed this website is using Codeigniter framework. And hence we have a simpler code to have multiple grids in one page. The code is as follows:
<pre><code class="language-php">protected function _getGroceryCrudEnterprise() {
    $db = include('path/to/database.php');
    $config = include('path/to/config.php');

    $groceryCrud = new GroceryCrud($config, $db);

    return $groceryCrud;
}

public function demo_multigrid() {
    $crud = $this-&gt;_getGroceryCrudEnterprise();

    $crud-&gt;setApiUrlPath('/demo_example_films');
    $output = $crud-&gt;render();

    $crud2 = $this-&gt;_getGroceryCrudEnterprise();

    $crud2-&gt;setApiUrlPath('/demo_example_customers');
    $output2 = $crud2-&gt;render();

    $output-&gt;output .= '&lt;br/&gt;' . $output2-&gt;output;

    return $this-&gt;_example_output($output);
}

public function demo_example_films() {
    $crud = $this-&gt;_getGroceryCrudEnterprise();

    $crud-&gt;setTable('film');
    $crud-&gt;setSubject('Film', 'Films');
    $crud-&gt;setRead();
    $crud-&gt;setRelationNtoN('actors', 'film_actor', 'actor', 'film_id', 'actor_id', 'fullname');
    $crud-&gt;setRelationNtoN('categories', 'film_category', 'category', 'film_id', 'category_id', 'name');

    $output = $crud-&gt;render();
    
    return $this-&gt;_example_output($output);
}

public function demo_example_customers() {
    $crud = $this-&gt;_getGroceryCrudEnterprise();

    $crud-&gt;setTable('customers');
    $crud-&gt;setSubject('Customer', 'Customers');
    $crud-&gt;setRead();

    $output = $crud-&gt;render();
 
    return $this-&gt;_example_output($output);
}

public function _example_output($output = null) {
   if (isset($output-&gt;isJSONResponse) &amp;&amp; $output-&gt;isJSONResponse) {
      header('Content-Type: application/json; charset=utf-8');
      echo $output-&gt;output;
      exit;
    }

   $this-&gt;load-&gt;view('example.php', $output); 
}
</code></pre>

And the result of the above code is the below. Feel free to click page source to see the source of the multigrid to understand better the code example: