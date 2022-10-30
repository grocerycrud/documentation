---
id: create-crud-codeigniter-tutorial
title: Your first Codeigniter CRUD
description: A codeigniter CRUD tutorial for newbies. Use grocery CRUD to do things faster.
canonical: docs/create-crud-codeigniter-tutorial
previous: 
next: 
---

# Your first Codeigniter CRUD

If you are totally new to the codeigniter experience and you can't still understand the way that you can create a CRUD, this codeigniter CRUD tutorial is just for you. Below you will see with steps how to make grocery CRUD work and how to install it to a new project. All the examples below are for codeigniter 2.x but the same exact implementation stands for version 3.X as well.

Step 1. First of all <a href="https://www.codeigniter.com/download" target="_blank">download codeigniter</a> and make sure that you project have  the welcome screen. So if your first screen of your project looks like the image below, you just installed codeigniter framework to your project.
<img src="https://d328ce9sgcu5lp.cloudfront.net/assets/themes/responsive/images/pages/codeigniter-welcome.png" alt="Welcome Page Codeigniter" />

2nd Step. Now we are ready to configure our database to our codeigniter project. The database connection for codeigniter can be configured at: your_project/application/config/database.php The file will look something like this:
<pre><code class="language-php">
&lt;?php  if ( ! defined('BASEPATH')) exit('No direct script access allowed');
/**
 * CodeIgniter
 *
 * An open source application development framework for PHP 5.1.6 or newer
... mpla mpla mpla
*/

$active_group = 'default';
$active_record = TRUE;

$db['default']['hostname'] = 'localhost';
$db['default']['username'] = '';
$db['default']['password'] = '';
$db['default']['database'] = '';
$db['default']['dbdriver'] = 'mysql';
$db['default']['dbprefix'] = '';
$db['default']['pconnect'] = TRUE;
$db['default']['db_debug'] = TRUE;
$db['default']['cache_on'] = FALSE;
$db['default']['cachedir'] = '';
$db['default']['char_set'] = 'utf8';
$db['default']['dbcollat'] = 'utf8_general_ci';
$db['default']['swap_pre'] = '';
$db['default']['autoinit'] = TRUE;
$db['default']['stricton'] = FALSE;
$db['default']['failover'] = array();

/* End of file database.php */
/* Location: ./application/config/database.php */
</code></pre>
So make sure that you have your database settings there. For example:
<pre><code class="language-php">
$db['default']['hostname'] = 'localhost';
$db['default']['username'] = 'root';
$db['default']['password'] = '1234'; //Pretty secure don't you think?
$db['default']['database'] = 'my_new_cms';
</code></pre>

3rd Step. Let's create our first controller. Let's name our first controller Main. So to do that, you will go to your_project/application /controllers/ and add the Main.php , that will look like this:
<pre><code class="language-php">
&lt;?php  if ( ! defined('BASEPATH')) exit('No direct script access allowed');

class Main extends CI_Controller {

    function __construct()
    {
        parent::__construct();

        $this->load->database();
  
    }

	public function index()
	{
		echo "&lt;h1&gt;Welcome to the world of Codeigniter&lt;/h1&gt;";//Just an example to ensure that we get into the function
		die();
	}
}

/* End of file Main.php */
/* Location: ./application/controllers/Main.php */
</code></pre>

To make sure that everything works fine, you have to go to http://localhost/your_project/index.php/main and see the message: Welcome to the world of Codeigniter. If you have an error like this:
<img src="https://d328ce9sgcu5lp.cloudfront.net/assets/themes/responsive/images/pages/database-error.png" alt="Codeigniter Database Error" />
Then something goes wrong with the database connection, check your password and the username and try again.
Step 4.Create your table in your database. Let's say we have the table with table name employees. The SQL code that you can insert is:
<pre><code class="language-php">
CREATE TABLE IF NOT EXISTS `employees` (
  `employeeNumber` int(11) NOT NULL AUTO_INCREMENT,
  `lastName` varchar(50) NOT NULL,
  `firstName` varchar(50) NOT NULL,
  `extension` varchar(10) NOT NULL,
  `email` varchar(100) NOT NULL,
  `officeCode` varchar(10) NOT NULL,
  `file_url` varchar(250) CHARACTER SET utf8 NOT NULL,
  `jobTitle` varchar(50) NOT NULL,
  PRIMARY KEY (`employeeNumber`)
) ENGINE=MyISAM  DEFAULT CHARSET=latin1 AUTO_INCREMENT=1703 ;


INSERT INTO `employees` (`employeeNumber`, `lastName`, `firstName`, `extension`, `email`, `officeCode`, `file_url`, `jobTitle`) VALUES
(1002, 'Murphy', 'Diane', 'x5800', 'dmurphy@classicmodelcars.com', '1', '', 'President'),
(1056, 'Patterson', 'Mary', 'x4611', 'mpatterso@classicmodelcars.com', '1', '', 'VP Sales'),
(1076, 'Firrelli', 'Jeff', 'x9273', 'jfirrelli@classicmodelcars.com', '1', '', 'VP Marketing'),
(1088, 'Patterson', 'William', 'x4871', 'wpatterson@classicmodelcars.com', '6', '', 'Sales Manager (APAC)'),
(1102, 'Bondur', 'Gerard', 'x5408', 'gbondur@classicmodelcars.com', '4', 'pdftest.pdf', 'Sale Manager (EMEA)'),
(1143, 'Bow', 'Anthony', 'x5428', 'abow@classicmodelcars.com', '1', '', 'Sales Manager (NA)'),
(1165, 'Jennings', 'Leslie', 'x3291', 'ljennings@classicmodelcars.com', '1', '', 'Sales Rep'),
(1166, 'Thompson', 'Leslie', 'x4065', 'lthompson@classicmodelcars.com', '1', '', 'Sales Rep'),
(1188, 'Firrelli', 'Julie', 'x2173', 'jfirrelli@classicmodelcars.com', '2', 'test-2.pdf', 'Sales Rep'),
(1216, 'Patterson', 'Steve', 'x4334', 'spatterson@classicmodelcars.com', '2', '', 'Sales Rep'),
(1286, 'Tseng', 'Foon Yue', 'x2248', 'ftseng@classicmodelcars.com', '3', '', 'Sales Rep'),
(1323, 'Vanauf', 'George', 'x4102', 'gvanauf@classicmodelcars.com', '3', '', 'Sales Rep'),
(1337, 'Bondur', 'Loui', 'x6493', 'lbondur@classicmodelcars.com', '4', '', 'Sales Rep'),
(1370, 'Hernandez', 'Gerard', 'x2028', 'ghernande@classicmodelcars.com', '4', '', 'Sales Rep'),
(1401, 'Castillo', 'Pamela', 'x2759', 'pcastillo@classicmodelcars.com', '4', '', 'Sales Rep'),
(1501, 'Bott', 'Larry', 'x2311', 'lbott@classicmodelcars.com', '7', '', 'Sales Rep'),
(1504, 'Jones', 'Barry', 'x102', 'bjones@classicmodelcars.com', '7', '', 'Sales Rep'),
(1611, 'Fixter', 'Andy', 'x101', 'afixter@classicmodelcars.com', '6', '', 'Sales Rep'),
(1612, 'Marsh', 'Peter', 'x102', 'pmarsh@classicmodelcars.com', '6', '', 'Sales Rep'),
(1619, 'King', 'Tom', 'x103', 'tking@classicmodelcars.com', '6', '', 'Sales Rep'),
(1621, 'Nishi', 'Mami', 'x101', 'mnishi@classicmodelcars.com', '5', '', 'Sales Rep'),
(1625, 'Kato', 'Yoshimi', 'x102', 'ykato@classicmodelcars.com', '5', '', 'Sales Rep'),
(1702, 'Gerard', 'Martin', 'x2312', 'mgerard@classicmodelcars.com', '4', '', 'Sales Rep');
</code></pre>
Now that you inserted the table without any errors. Let's go to the next step.
Step 5. Make sure that you have installed grocery CRUD correctly at your project by adding all the files and folders to your project. After the end of your installation, your project will have to look similar to this structure:

<div class='code'>
website_folder/
<br/>–––– application/
<br/>–––––––– config/
<br/>–––––––––––– autoload.php
<br/>–––––––––––– ...
<br/>–––––––––––– doctypes.php
<br/>–––––––––––– foreign_chars.php
<br/>–––––––––––– grocery_crud.php
<br/>–––––––––––– ...
<br/>–––––––– controllers/
<br/>–––––––––––– examples.php
<br/>–––––––––––– index.html
<br/>–––––––––––– welcome.php
<br/>–––––––– libraries/
<br/>–––––––––––– grocery_crud.php
<br/>–––––––––––– index.html
<br/>–––––––– models/
<br/>–––––––––––– grocery_crud_model.php
<br/>–––––––––––– index.html
<br/>–––––––– views/
<br/>–––––––––––– example.php
<br/>–––––––––––– index.html
<br/>–––––––––––– welcome_message.php
<br/>–––– assets/
<br/>–––––––– grocery_crud/
<br/>–––––––––––– css/
<br/>–––––––––––– js/
<br/>–––––––––––– texteditor/
<br/>–––––––––––– themes/
<br/>–––––––– uploads/
<br/>–––––––– index.html
<br/>–––– system/
<br/>–––– user_guide/
<br/>–––– change_log.txt
<br/>–––– example_database.sql
<br/>–––– index.php
<br/>–––– licence-grocery-crud.txt
<br/>–––– license.txt
&lt;/div&gt;
For more you can also see at <a href="/documentation/codeigniter_installation">grocery CRUD installation</a>.

Step 6.Let's go to our controller and add some stuff to make grocery CRUD work. Add the method employees like the below example:
<pre><code class="language-php">
&lt;?php  if ( ! defined('BASEPATH')) exit('No direct script access allowed');

class Main extends CI_Controller {

    function __construct()
    {
        parent::__construct();

        /* Standard Libraries of codeigniter are required */
        $this->load->database();
        $this->load->helper('url');
        /* ------------------ */ 

        $this->load->library('grocery_CRUD');
  
    }

	public function index()
	{
		echo "&lt;h1&gt;Welcome to the world of Codeigniter&lt;/h1&gt;";//Just an example to ensure that we get into the function
		die();
	}

	public function employees()
	{
		$crud = new grocery_CRUD();
		$crud->set_table('employees');
		$output = $this->grocery_crud->render();

		echo "<pre>";
		print_r($output);
		echo "</pre>";
		die();
	}
}

/* End of file Main.php */
/* Location: ./application/controllers/Main.php */
</code></pre>
If everything goes well and you don't have any errors or exceptions you will go to: http://localhost/your_project/index.php/main/employees and see the below result, then everything works correctly :
<pre><code class="language-php">
stdClass Object
(
    [output] => Your output will appear here....
    [js_files] => Array
        (
            [763b4d272e158bdb8ed5a12a1824c94f494954bd] => http://grocery_crud/public/grocery_crud/themes/datatables/js/jquery-1.6.2.min.js
            [0b677f3fc6fb25b4baf39eb144222116c5b60254] => http://grocery_crud/public/grocery_crud/themes/flexigrid/js/cookies.js
            [ec3ae62b8d5838972e858fe54447bd4bd8d79f88] => http://grocery_crud/public/grocery_crud/themes/flexigrid/js/flexigrid.js
            [2c0ff56d0cbc6f80a5ef9c770d478f0e00c3170d] => http://grocery_crud/public/grocery_crud/themes/flexigrid/js/jquery.form.js
            [474495ff1e895eab81fb8afba4db9b06c15b19af] => http://grocery_crud/public/grocery_crud/themes/flexigrid/js/jquery.numeric.js
        )

    [css_files] => Array
        (
            [732b03aa54d124f062757b71e5560acdc5632ba6] => http://grocery_crud/public/grocery_crud/themes/flexigrid/css/flexigrid.css
        )

)
</code></pre>
Important Note: Please make sure that you don't have grocery CRUD to the index function of your controller as it is a known issue that it will not work on index. Just move it to another method. For example "employees" or something else except index.
Step 7. Now let's create our view. The results that we have seen we can use them to have grocery CRUD to our project. We just need a view to do it. So a view will look like this:
<pre><code class="language-php">&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
    &lt;meta charset="utf-8" />

&lt;?php 
foreach($css_files as $file): ?>
    <link type="text/css" rel="stylesheet" href="&lt;?php echo $file; ?>" />

&lt;?php endforeach; ?>
&lt;?php foreach($js_files as $file): ?>

    <script src="&lt;?php echo $file; ?>"></script>
&lt;?php endforeach; ?>

&lt;style type='text/css'&gt;
body
{
    font-family: Arial;
    font-size: 14px;
}
&lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
<!-- Beginning header -->
&lt;div&gt;
    <a href='&lt;?php echo site_url('examples/offices_management')?>'>Offices</a> | 
    <a href='&lt;?php echo site_url('examples/employees_management')?>'>Employees</a> |
    <a href='&lt;?php echo site_url('examples/customers_management')?>'>Customers</a> |
    <a href='&lt;?php echo site_url('examples/orders_management')?>'>Orders</a> |
    <a href='&lt;?php echo site_url('examples/products_management')?>'>Products</a> | 
    <a href='&lt;?php echo site_url('examples/film_management')?>'>Films</a>

&lt;/div&gt;
<!-- End of header-->
<div style='height:20px;'>&lt;/div&gt;  
&lt;div&gt;
    &lt;?php echo $output; ?>

&lt;/div&gt;
<!-- Beginning footer -->
&lt;div&gt;Footer&lt;/div&gt;
<!-- End of Footer -->
&lt;/body&gt;
&lt;/html&gt;
</code></pre>

So let's save this file into: your_project/application/views/our_template.php and go to our controller and add some more stuff.

<pre><code class="language-php">&lt;?php  if ( ! defined('BASEPATH')) exit('No direct script access allowed');

class Main extends CI_Controller {

    function __construct()
    {
        parent::__construct();

        /* Standard Libraries of codeigniter are required */
        $this->load->database();
        $this->load->helper('url');
        /* ------------------ */ 

        $this->load->library('grocery_CRUD');
  
    }

	public function index()
	{
		echo "&lt;h1&gt;Welcome to the world of Codeigniter&lt;/h1&gt;";//Just an example to ensure that we get into the function
                die();
	}

	public function employees()
	{
		$crud = new grocery_CRUD();
		$crud->set_table('employees');
		$output = $crud->render();

		$this->_example_output($output);		
	}

    function _example_output($output = null)
    {
        $this->load->view('our_template.php',$output);    
    }
}

/* End of file Main.php */
/* Location: ./application/controllers/Main.php */
</code></pre>

Now go to http://localhost/your_project/index.php/main/employees and you will see a result like this:
<a href="https://d328ce9sgcu5lp.cloudfront.net/assets/themes/responsive/images/pages/employees-example.png" target="_blank"><img src="https://d328ce9sgcu5lp.cloudfront.net/assets/themes/responsive/images/pages/employees-example.png" width="550" alt="Employees example"/></a>
	
That's it! Now go to the kitchen and grab a coffee or a beer (depends on the time really!). Lay back and enjoy the power of grocery CRUD in your project :)
Continue with <a href='/documentation/tutorial_basic_methods'>tutorial and Basic Methods</a> or go straight ahead to the 
<a href='/documentation/options_functions'>methods/functions</a> for the full documentation of each function/method with at least one example for each .
	
Note: This tutorial is only to show how to install grocery CRUD to your project. If you have any questions about codeigniter issues , for example how to use views or controllers, please go to the <a target="_blank" href="http://codeigniter.com/user_guide/">user guide of codeigniter</a> or post your question at the <a href="/forums/forum/10-general/">general forum</a> 

	
<span style='color:red'>grocery CRUD, doesn't work?</span>. You can see the <a href='/crud/view/known-issues'>known issues</a> or you can see the video <a href="https://youtu.be/X0gnDD0qTS8" target="_blank">common mistakes when we install Grocery CRUD (part 1)</a> or find the answer at <a href="http://www.grocerycrud.com/forums/">grocery CRUD forums</a>. 

<span style='color:red'>Still you can't install it?</span> Ask your specific question to our <a href="http://www.grocerycrud.com/forums/">really friendly community</a> or send us a message at the <a href='/crud/view/support'>support form</a> and we will answer you as soon as possible.
	