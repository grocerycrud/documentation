---
id: installation-guide
title: Installation guide
permalink: docs/gcc/2.x/getting-started/installation-guide
next: default-routes
---

# Installation guide

The installation is really easy. You just copy all the files to your project and you are ready to use grocery CRUD!

By the end of the installation, your folder structure should look similar to this: (new folders/files are with bold)

<pre>├── app
│   ├── Common.php
│   ├── Config
│   │   ├── App.php
│   │   ├── Autoload.php
│   │   ├── ...
│   │   ├── Format.php
│   │   ├── <strong>GroceryCrud.php</strong>
│   │   ├── Honeypot.php
│   │   ├── ...
│   │   └── View.php
│   ├── Controllers
│   │   ├── BaseController.php
│   │   ├── <strong>Examples.php</strong>
│   │   └── Home.php
│   ├── Database
│   ├── ...
│   ├── Libraries
│   │   └── <strong>GroceryCrud.php</strong>
│   ├── Models
│   │   └── <strong>GroceryCrudModel.php</strong>
│   ├── ThirdParty
│   ├── Views
│   │   ├── errors
│   │   ├── <strong>example.php</strong>
│   │   └── welcome_message.php
│   └── index.html
├── public
│   ├── <strong>assets</strong>
│   │   ├── <strong>grocery_crud</strong>
│   │   ├── <strong>index.html</strong>
│   │   └── <strong>uploads</strong>
│   ├── favicon.ico
│   ├── index.php
│   └── robots.txt
├── spark
├── system
└── writable</pre>

The app/Controllers/Examples.php will look like this:

	<?php namespace App\Controllers;

	use App\Libraries\GroceryCrud;

	class Examples extends BaseController
	{
        public function customers_management()
	    {
	        $crud = new GroceryCrud();

            $crud->setTable('customers');

            $output = $crud->render();

            return $this->_exampleOutput($output);
	    }

	    private function _exampleOutput($output = null) {
	        return view('example', (array)$output);
	    }
	}

The only required configurations is to add your database credentials into a .env file  if you haven't already done that.

In order to access the URL file for customers_management your URL will look something like this:

http://www.example.com/index.php/examples/customers_management

or:

http://www.example.com/examples/customers_management

The variable $output is an object that always includes the following properties - output, js_files, css_files. 
Below you see an example of a print_r of a variable `$output` :

    stdClass Object
    (
        [output] => Your output will appear here....
        [js_files] => Array
            (
                [32fd432b4478200b5aacd62b65d5bdc269337910] => http://localhost/grocery-crud-codeigniter-4/public/assets/grocery_crud/js/jquery-1.11.1.min.js
                [d04ba7f0d55dda1d4ba9b6532414c653c58b0318] => http://localhost/grocery-crud-codeigniter-4/public/assets/grocery_crud/js/common/list.js
                [2d2b031fb606852768dc4c9a3c457545558cc924] => http://localhost/grocery-crud-codeigniter-4/public/assets/grocery_crud/themes/flexigrid/js/cookies.js
                [6629a324ade6d489aff77292cb02e31d9188a6bb] => http://localhost/grocery-crud-codeigniter-4/public/assets/grocery_crud/themes/flexigrid/js/flexigrid.js
                [5238a822ff2c6cced38a61590ac6debcc847bc0b] => http://localhost/grocery-crud-codeigniter-4/public/assets/grocery_crud/js/jquery_plugins/jquery.form.min.js
                [41101518af3f8fb416f60152aa019d963ae9293b] => http://localhost/grocery-crud-codeigniter-4/public/assets/grocery_crud/js/jquery_plugins/jquery.numeric.min.js
                [8823261dedf8eda49cfa2a7a528b5182350a90ae] => http://localhost/grocery-crud-codeigniter-4/public/assets/grocery_crud/themes/flexigrid/js/jquery.printElement.min.js
                [2ea588263ae884c476a96f40dc6cedd5316bbd57] => http://localhost/grocery-crud-codeigniter-4/public/assets/grocery_crud/js/jquery_plugins/ui/jquery-ui-1.10.3.custom.min.js
            )
        [css_files] => Array
            (
                [f1731e27afe02ab899b16daf8ae4a5ac8ac05d4e] => http://localhost/grocery-crud-codeigniter-4/public/assets/grocery_crud/themes/flexigrid/css/flexigrid.css
                [3e3f44ffabdcdd9017fa9db5262ce0465dde1322] => http://localhost/grocery-crud-codeigniter-4/public/assets/grocery_crud/css/ui/simple/jquery-ui-1.10.1.custom.min.css
            )
    )
    
The view at `app/Views/example.php` is a simple Codeigniter view file and includes the below code:

	<!DOCTYPE html>
	<html>
	<head>
        <meta charset="utf-8" />
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
	<?php 
	foreach($css_files as $file): ?>
		<link type="text/css" rel="stylesheet" href="<?php echo $file; ?>" />
	<?php endforeach; ?>
	</head>
	<body>
		<div>
		    <a href='<?php echo site_url('examples/customers_management')?>'>Customers</a> |
		    <a href='<?php echo site_url('examples/orders_management')?>'>Orders</a> |
		    <a href='<?php echo site_url('examples/products_management')?>'>Products</a> |
		    <a href='<?php echo site_url('examples/offices_management')?>'>Offices</a> | 
		    <a href='<?php echo site_url('examples/employees_management')?>'>Employees</a> |		 
		    <a href='<?php echo site_url('examples/film_management')?>'>Films</a>
		</div>
		<div style='height:20px;'></div>  
	    <div style="padding: 10px">
			<?php echo $output; ?>
	    </div>
	    <?php foreach($js_files as $file): ?>
	        <script src="<?php echo $file; ?>"></script>
	    <?php endforeach; ?>
	</body>
	</html>

    