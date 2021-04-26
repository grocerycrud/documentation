---
id: grocery-crud-enterprise-installation
title: Installation Guide
description: Step by Step installation of Grocery CRUD Enterprise with or without composer.
permalink: docs/grocery-crud-enterprise-installation
previous: api-and-functions-list
next: basic-example
---

# Installation Guide

There are 2 ways to install grocery CRUD Enterprise to your project:

- <a href="#without-composer">Without Composer</a> (recommended for people that are not using PHP frameworks and/or composer)
- <a href="#with-composer">Composer</a> (recommended for PHP frameworks like Laravel,... e.t.c.)

If you are looking for more specific installation guidance, you can also check the below tutorials:
- <a href="/docs/grocery-crud-enterprise-codeigniter-3">Installation in Codeigniter v3</a>
- <a href="/docs/grocery-crud-enterprise-codeigniter-4">Installation in Codeigniter v4</a>
- <a href="/docs/grocery-crud-enterprise-laravel-8-installation">Laravel v8 installation</a>

<div id="without-composer"></div>
<h1>Installation</h1>
<h2>1. Without Composer</h2>
For many people composer seems too complicated and they prefer the old fashioned copy-paste way. 
Also if you are using a framework that it is not requiring composer or you are using native PHP then the installation without composer is the best choice. 
There is nothing bad with the installation without composer, it is just that on updates it will require more manual work.

In case you prefer a video tutorial, we did create the below steps into a video see: <a href="https://www.youtube.com/watch?v=JPJPvGKWxtk">Grocery CRUD Enterprise - Installation without composer</a>

<strong>Step 1.</strong>

Download the zip file for installation without composer. You can also download the newest zip file from: https://www.grocerycrud.com/users . 
In order to have a more specific example from now on we will use the name:  <code>grocery-crud-enterprise-v2.8.7-without-composer.zip</code> as the zip file

<strong>Step2.</strong>

Unzip the file and you will find a file structure like that:
<pre>├── examples
│   ├── config.php
│   ├── database.php
│   ├── example.php
│   └── view.php
├── libraries
│   ├── autoload.php
│   ├── bin
│   ├── composer
│   ├── ...
│   ├── phpunit
│   ├── symfony
│   └── zendframework
└── public
    └── grocery-crud
        ├── css
        ├── fonts
        ├── images
        └── js
</pre>
The folders have the following files:
1. <code>examples</code> folder has a very basic example so you can simply copy the files and see it working on native PHP.
2. <code>libraries</code> folder has all the PHP libraries that are required in order groceryCRUD to run. This is basically the folder <code>vendor</code> from composer just renamed to not have conflicts in case you want to use composer on other purposes
3. <code>public</code> folder is the one that has all the JS,CSS, fonts and images that are required in order to show it on a webpage. The name is public as these files are the one that will be visible from a web browser

Before going to the next step there are 2 config files that you are <strong>required </strong>to configure. The first one is the database connection credentials. A simple database file like the below is required:
<pre><code class="language-php">&lt;?php
// database.php
return [
    'adapter' =&gt; [
        'driver' =&gt; 'Pdo_Mysql',
        'database' =&gt; 'db_name',
        'username' =&gt; 'db_username',
        'password' =&gt; 'db_password',
        'charset' =&gt; 'utf8'
    ]
];</code></pre>
As in grocery CRUD Enterprise we are using the power of Zend Framework the drivers are from Zend Framework DB version 2. For more you can see the documentation at <a href="https://framework.zend.com/manual/2.4/en/modules/zend.db.adapter.html" target="_blank" rel="noopener noreferrer">Zend\Db\Adapter </a>

The second configuration file is the one that you need to include for grocery CRUD. The configuration file will look like the below:
<pre><code class="language-php">&lt;?php
// config.php
return [
    // So far 34 languages including: Afrikaans, Arabic, Bengali, Bulgarian, Catalan, Chinese, Czech, Danish,
    // Dutch, English, French, German, Greek, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean,
    // Lithuanian, Mongolian, Norwegian, Persian, Polish, Portuguese, Brazilian Portuguese, Romanian,
    // Russian, Slovak, Spanish, Thai, Turkish, Ukrainian, Vietnamese
    'default_language'	=&gt; 'English',

    // This is the assets folder where all the JavaScript, CSS, images and font files are located
    'assets_folder' =&gt; '/assets/grocery-crud/',

    // There are only three choices: "uk-date" (dd/mm/yyyy), "us-date" (mm/dd/yyyy) or "sql-date" (yyyy-mm-dd)
    'date_format' =&gt; 'uk-date',

    // The default per page when a user firstly see a list page
    'default_per_page'	=&gt; 10,

    // Having some options at the list paging. This is the default one that all the websites are using.
    // Make sure that the number of grocery_crud_default_per_page variable is included to this array.
    'paging_options' =&gt; ['10', '25', '50', '100'],

    // The environment is important so we can have specific configurations for specific environments
    'environment' =&gt; 'development',

    // The default skin that Grocery CRUD will use. Currently choose between 'bootstrap-v3' and 'bootstrap-v4'
    'skin' =&gt; 'bootstrap-v3',

    // This is basically in order to have some basic cache for the initial calls mainly for field types
    // of a database table
    'backend_cache' =&gt; false,

    'xss_clean' =&gt; false,

    // The character limiter at the datagrid columns, zero(0) value if you don't want any character
    // limitation to the column
    'column_character_limiter' =&gt; 50,

    // You can choose between 'minimal' or 'full'
    'text_editor_type' =&gt; 'full',

    // If open_in_modal is true then all the form operations (e.g. add, edit, clone... e.t.c.) will
    // open within a modal and we will have the datagrid on the background.
    // In case you would like however to have a standalone page for all the form operations change this to false.
    'open_in_modal' =&gt; true,

    // This is the hash symbol (#) that we have at the URL in order to have tha basic operations in the URL so you
    // can navigate back to the URL that you were. For example, when you click at edit form for the id 46, the
    // URL will also change to #/edit/46 so you can also share the link.
    // In case you would like to switch this functionality to off change this to false.
    'hash_in_url' =&gt; true,


    // The maximum number of buttons that we would like to have for the actions buttons.
    // If the number of buttons exceeds this number then the last button on the right
    // is going to change into a "More" dropdown button.
    // If the maximum number is 1 then as we only have one button as a dropdown list the translation
    // is "Actions" rather than "More"
    'max_action_buttons' =&gt; [
        'mobile' => 1,
        'desktop' => 2
    ],

    // The allowed file types on upload. If the file extension doesn't exist in the array
    // it will throw an error and the upload will not be completed
    'upload_allowed_file_types' =&gt;  [
        'gif', 'jpeg', 'jpg', 'png', 'svg', 'tiff', 'doc', 'docx',  'rtf', 'txt', 'odt', 'xls', 'xlsx', 'pdf',
        'ppt', 'pptx', 'pps', 'ppsx', 'mp3', 'm4a', 'ogg', 'wav', 'mp4', 'm4v', 'mov', 'wmv', 'flv', 'avi',
        'mpg', 'ogv', '3gp', '3g2'
    ],

    // For more read http://framework.zend.com/manual/current/en/modules/zend.cache.storage.adapter.html
    // If you are not sure about how to use it, you can just change the ttl value (time to live) and
    // the file path of the cache
    'cache' =&gt; [
        'adapter' =&gt; [
            'name'    =&gt; 'filesystem',
            'options' =&gt; [
                'namespace' =&gt; 'gcrud',
                'ttl' =&gt; 3600 * 24 * 30 * 6,
                'cache_dir' =&gt; realpath(__DIR__ . '/Cache/')
            ],
        ],
        'plugins' =&gt; [
            'exception_handler' =&gt; ['throw_exceptions' =&gt; false],
        ],
    ],
];</code></pre>
At the config file there are 3 basic sections that we need to be aware of:
<ol>
 	<li><strong>The assets_folder: </strong> The assets folder is the folder that can publicly be accessible by the end user. These folders includes: images, JavaScript files, fonts and stylesheets files.</li>
 	<li><strong>The environment: </strong>Make sure that the <code>development</code> environment is the one that you are using when you are developing the project. and <code>production</code> is the one that is used when you are publishing the website to production.</li>
 	<li><strong>The cache: </strong>Grocery CRUD is based on cache to do as less queries to the database as possible it is <strong>strongly </strong><b>advised </b>to use cache to your project. The default cache is the files cache but of course you can change the cache configurations to add a faster method to cache. All the configurations for the cache can be found at:  <a href="https://framework.zend.com/manual/2.4/en/modules/zend.cache.storage.adapter.html">Zend\Cache\Storage\Adapter</a></li>
</ol>
<strong>Step3.</strong>

If you are using native PHP (without any framework) then you just need to copy the examples at the desired folder.

As it is always better to have a real example. Let's say that you have a PHP project that has the below structure (usually when people are using native PHP they don't use routes and hence the following structure).
<pre>├── assets
├── libs
├── index.php
├── customers.php
└── films.php
</pre>
and all the JavaScript and CSS files are in the <code>assets</code> folder.

Copy the config files: config.php, database.php, example.php, view.php at your app folder.

So now your folder will look like this:
<pre>├── assets
├── libs
├── index.php
<strong>├── config.php
├── database.php
├── example.php
├── view.php</strong>
├── customers.php
└── films.php
</pre>
And the example.php looks like this:
<pre><code class="language-php">&lt?php
// example.php

include("../libraries/autoload.php");

use GroceryCrud\Core\GroceryCrud;

$database = include('database.php');
$config = include('config.php');

$crud = new GroceryCrud($config, $database);

$crud-&gt;setTable('customers');
$crud-&gt;setSubject('Customer', 'Customers');

$output = $crud-&gt;render();

if ($output-&gt;isJSONResponse) {
    header('Content-Type: application/json; charset=utf-8');
    echo $output-&gt;output;
    exit;
}

$css_files = $output-&gt;css_files;
$js_files = $output-&gt;js_files;
$output = $output-&gt;output;

include('view.php');</code></pre>
So now we will basically change just slightly the example.php to fit to our needs for the <code>films.php</code>. So first of all let's assume that the <code>films.php</code> has some code of your own project. For that reason, I will include the <code>...</code> at the below example so you can understand that this is basically your code (e.g. header, footer, some functionality... e.t.c.).

So the final example for films.php will look like this:
<pre><code class="language-php">&lt;?php
// films.php

include("libraries/autoload.php");

use GroceryCrud\Core\GroceryCrud;

$database = include('database.php');
$config = include('config.php');

$crud = new GroceryCrud($config, $database);

$crud-&gt;setTable('films');
$crud-&gt;setSubject('Film', 'Films');

$output = $crud-&gt;render();

if ($output-&gt;isJSONResponse) {
    header('Content-Type: application/json; charset=utf-8');
    echo $output-&gt;output;
    exit;
}

$css_files = $output-&gt;css_files;
$js_files = $output-&gt;js_files;
$output = $output-&gt;output;

// The below include is not required. If you have another way to show:
// a. the output
// b. the CSS and JS files
// Then you can basically include the results of the output and the CSS/JS files to your own framework's output or template
include('view.php');
</code></pre>
<div id="with-composer"></div>
Now from the above code you will have a full working CRUD without the need to do anything else! You can now enjoy all the power of Grocery CRUD at the documentation (and you didn't use any terminal at all).
<h2>2. Installation with composer</h2>
If you prefer the video tutorials well... we did create a <a href="https://www.youtube.com/watch?v=buIwAipWSqo" target="_blank" rel="noopener noreferrer">video tutorial</a> with all the below information into one video.

The most recommended way to install PHP libraries nowadays is through <a href="https://getcomposer.org/" target="_blank" rel="noopener noreferrer">composer</a>. Grocery CRUD Enterprise has private code and you should have one more step from the normal composer installations. This extra step will change at the future however this work is still in progress and currently you will need to do these 2 extra steps.
<strong>Step 1. </strong>
Download the version of groceryCRUD Enterpirse from https://www.grocerycrud.com/users or through the email that you did get. For example the file to download is: <code>grocery-crud-enterprise-v2.8.7.zip</code>

<strong>Step 2.</strong>

store this file through a folder that you are adding your libraries. This can be anywhere at your local environment however it is important to not rename the zip file. As this file is an artifact, we will name our folder <code>artifacts/</code> you can of course use your own names like <code>lib/</code> or even more specific <code>groceryCRUD/</code> if you are going to use artifacts only for groceryCRUD

<strong>Step 3.</strong>

Add the below code at your composer.json
<pre><code class="js">{
    "repositories": [
        {
            "type": "artifact",
            "url": "/path/to/artifacts/"
        }
    ],
    "require": {
        "grocerycrud/enterprise": "version-number"
    }
}
</code></pre>
For example (a project that will have only groceryCRUD Enterprise as third party libraries):
<pre><code class="js">{
    "repositories": [
        {
            "type": "artifact",
            "url": "artifacts/"
        }
    ],
    "require": {
        "grocerycrud/enterprise": "2.*.*"
    }
}
</code></pre>
As many people are new to composer and sometimes is really annoying to not have real examples, I will give a more specific example of how your composer will look like. So let's say that you have installed <a href="https://laravel.com/" target="_blank" rel="noopener noreferrer">laravel</a> to your project. Your composer.json will look something like this (see with bold the new lines):
<pre><code class="js">{
	"name": "laravel/laravel",
	"description": "The Laravel Framework.",
	"keywords": ["framework", "laravel"],
	"license": "MIT",
	"type": "project",
        <strong>"repositories": [
            {
                "type": "artifact",
                "url": "artifacts/"
            }
        ]</strong>
	"require": {
		"laravel/framework": "5.0.*",
                <strong>"grocerycrud/enterprise": "2.*.*"</strong>
	},
	"require-dev": {
		"phpunit/phpunit": "~4.0",
		"phpspec/phpspec": "~2.1"
	},
	"autoload": {
		"classmap": [
			"database"
		],
		"psr-4": {
			"App\\": "app/"
		}
	},
	"autoload-dev": {
		"classmap": [
			"tests/TestCase.php"
		]
	},
	"scripts": {
		"post-install-cmd": [
			"php artisan clear-compiled",
			"php artisan optimize"
		],
		"post-update-cmd": [
			"php artisan clear-compiled",
			"php artisan optimize"
		],
		"post-create-project-cmd": [
			"php -r \"copy('.env.example', '.env');\"",
			"php artisan key:generate"
		]
	},
	"config": {
		"preferred-install": "dist"
	},
}</code></pre>
<strong>Step 4.</strong>
Now just run <code>composer update</code> or <code>composer install</code> if you are running composer for the first time on your project. Now you did install the enterprise version to your project. You will need also to copy the assets and add it to your public folder for all the JavaScript,CSS, fonts... e.t.c.

<strong>Step 5.</strong>
In order to install all your assets to your project. You need to <strong>manually copy </strong> the folder public to your public structured project.

To have a more specific example. So let's say that you are using laravel and the structure looks like this:
<pre>├── app
│   ├── Commands
│   ├── Console
│   ├── Events
│   ├── Exceptions
│   ├── Handlers
│   ├── Http
│   ├── Providers
│   └── Services
├── bootstrap
├── config
├── database
│   ├── migrations
│   └── seeds
├── public
│   ├── css
│   └── fonts
├── resources
│   ├── assets
│   ├── lang
│   └── views
├── storage
│   ├── app
│   ├── framework
│   └── logs
├── tests
└── vendor
</pre>
In that case the best place to have your public folder of groceryCRUD enterprise is at pubic-&gt;grocery-crud folder. So you will need to copy the folder from : <code>vendor/grocerycrud/enterprise/public/grocery-crud/</code> to the public folder of laravel
So after the copy your folder structure will look like this (in bold you can find the changed ones)
<pre>├── app
│   ├── Commands
│   ├── Console
│   ├── Events
│   ├── Exceptions
│   ├── Handlers
│   ├── Http
│   ├── Providers
│   └── Services
├── bootstrap
├── config
├── database
│   ├── migrations
│   └── seeds
├── public
│   ├── css
│   ├── fonts
<strong>|   └── grocery-crud
|   |   ├── css
|   |   ├── fonts
|   |   ├── images
|   |   └── js</strong>
├── resources
│   ├── assets
│   ├── lang
│   └── views
├── storage
│   ├── app
│   ├── framework
│   └── logs
├── tests
└── vendor
</pre>
<strong>Step 6.</strong>
Now you need to create your configurations files in order to make grocery CRUD Enterprise to work. So basically there are 3 things that you will need to configured
1. Where the public folder is
2. The database configurations
3. The cache folder (this is optional but it is very recommended to do it as your CRUD can be 10X faster.)

You can find all the code below of the examples at:
<code>vendor/grocerycrud/enterprise/example</code>

There are 2 config files that you are <strong>required </strong>to configure. The first one is the database connection credentials. A simple database file like the below is required:
<pre><code class="language-php">&lt;?php
// database.php
return [
    'adapter' =&gt; [
        'driver' =&gt; 'Pdo_Mysql',
        'database' =&gt; 'db_name',
        'username' =&gt; 'db_username',
        'password' =&gt; 'db_password',
        'charset' =&gt; 'utf8'
    ]
];</code></pre>
As in grocery CRUD Enterprise we are using the power of Zend Framework the drivers are from Zend Framework DB version 2. For more you can see the documentation at <a href="https://framework.zend.com/manual/2.4/en/modules/zend.db.adapter.html">Zend\Db\Adapter </a>

The second configuration file is the one that you need to include for grocery CRUD. The configuration file will look like the below:
<pre><code class="language-php">&lt;?php
// config.php
return [
    // So far 34 languages including: Afrikaans, Arabic, Bengali, Bulgarian, Catalan, Chinese, Czech, Danish,
    // Dutch, English, French, German, Greek, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean,
    // Lithuanian, Mongolian, Norwegian, Persian, Polish, Portuguese, Brazilian Portuguese, Romanian,
    // Russian, Slovak, Spanish, Thai, Turkish, Ukrainian, Vietnamese
    'default_language'	=&gt; 'English',

    // This is the assets folder where all the JavaScript, CSS, images and font files are located
    'assets_folder' =&gt; '/assets/grocery-crud/',

    // There are only three choices: "uk-date" (dd/mm/yyyy), "us-date" (mm/dd/yyyy) or "sql-date" (yyyy-mm-dd)
    'date_format' =&gt; 'uk-date',

    // The default per page when a user firstly see a list page
    'default_per_page'	=&gt; 10,

    // Having some options at the list paging. This is the default one that all the websites are using.
    // Make sure that the number of grocery_crud_default_per_page variable is included to this array.
    'paging_options' =&gt; ['10', '25', '50', '100'],

    // The environment is important so we can have specific configurations for specific environments
    'environment' =&gt; 'development',

    // The default skin that Grocery CRUD will use. Currently choose between 'bootstrap-v3' and 'bootstrap-v4'
    'skin' =&gt; 'bootstrap-v3',

    // This is basically in order to have some basic cache for the initial calls mainly for field types
    // of a database table
    'backend_cache' =&gt; false,

    'xss_clean' =&gt; false,

    // The character limiter at the datagrid columns, zero(0) value if you don't want any character
    // limitation to the column
    'column_character_limiter' =&gt; 50,

    // You can choose between 'minimal' or 'full'
    'text_editor_type' =&gt; 'full',

    // If open_in_modal is true then all the form operations (e.g. add, edit, clone... e.t.c.) will
    // open within a modal and we will have the datagrid on the background.
    // In case you would like however to have a standalone page for all the form operations change this to false.
    'open_in_modal' =&gt; true,

    // This is the hash symbol (#) that we have at the URL in order to have tha basic operations in the URL so you
    // can navigate back to the URL that you were. For example, when you click at edit form for the id 46, the
    // URL will also change to #/edit/46 so you can also share the link.
    // In case you would like to switch this functionality to off change this to false.
    'hash_in_url' =&gt; true,


    // The maximum number of buttons that we would like to have for the actions buttons.
    // If the number of buttons exceeds this number then the last button on the right
    // is going to change into a "More" dropdown button.
    // If the maximum number is 1 then as we only have one button as a dropdown list the translation
    // is "Actions" rather than "More"
    'max_action_buttons' =&gt; [
        'mobile' => 1,
        'desktop' => 2
    ],

    // The allowed file types on upload. If the file extension doesn't exist in the array
    // it will throw an error and the upload will not be completed
    'upload_allowed_file_types' =&gt;  [
        'gif', 'jpeg', 'jpg', 'png', 'svg', 'tiff', 'doc', 'docx',  'rtf', 'txt', 'odt', 'xls', 'xlsx', 'pdf',
        'ppt', 'pptx', 'pps', 'ppsx', 'mp3', 'm4a', 'ogg', 'wav', 'mp4', 'm4v', 'mov', 'wmv', 'flv', 'avi',
        'mpg', 'ogv', '3gp', '3g2'
    ],

    // For more read http://framework.zend.com/manual/current/en/modules/zend.cache.storage.adapter.html
    // If you are not sure about how to use it, you can just change the ttl value (time to live) and
    // the file path of the cache
    'cache' =&gt; [
        'adapter' =&gt; [
            'name'    =&gt; 'filesystem',
            'options' =&gt; [
                'namespace' =&gt; 'gcrud',
                'ttl' =&gt; 3600 * 24 * 30 * 6,
                'cache_dir' =&gt; realpath(__DIR__ . '/Cache/')
            ],
        ],
        'plugins' =&gt; [
            'exception_handler' =&gt; ['throw_exceptions' =&gt; false],
        ],
    ],
];</code></pre>
At the config file there are 3 basic sections that we need to be aware of:
<ol>
 	<li><strong>The assets_folder: </strong> The assets folder is the folder that can publicly be accessible by the end user. These folders includes: images, JavaScript files, fonts and stylesheets files.</li>
 	<li><strong>The environment: </strong>Make sure that the <code>development</code> environment is the one that you are using when you are developing the project. and <code>production</code> is the one that is used when you are publishing the website to production.</li>
 	<li><strong>The cache: </strong>Grocery CRUD is based on cache to do as less queries to the database as possible it is <strong>strongly </strong><b>advised </b>to use cache to your project. The default cache is the files cache but of course you can change the cache configurations to add a faster method to cache. All the configurations for the cache can be found at:  <a href="https://framework.zend.com/manual/2.4/en/modules/zend.cache.storage.adapter.html">Zend\Cache\Storage\Adapter</a></li>
</ol>
<strong>Step 7.</strong>

And now we are ready to make grocery CRUD Enterprise to put it to work! Let's have an example of the very first use. A first example without any framework installation will look like this:
<pre><code class="language-php">&lt;?php
// example.php

include("vendor/autoload.php");

use GroceryCrud\Core\GroceryCrud;

$database = include('database.php');
$config = include('config.php');

$crud = new GroceryCrud($config, $database);

$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');

$output = $crud->render();

if ($output->isJSONResponse) {
    header('Content-Type: application/json; charset=utf-8');
    echo $output->output;
    exit;
}

$css_files = $output->css_files;
$js_files = $output->js_files;
$output = $output->output;

include('view.php');
</code></pre>
And the <code>view.php</code> is a simple page (of course the implementation can be much better with a framework but this is just a quick example to see how easy you can install grocery CRUD Enterprise):
<pre><code class="language-php">&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
    &lt;meta charset="utf-8" /&gt;
    &lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt;
    &lt;?php foreach($css_files as $file): ?&gt;
        &lt;link type="text/css" rel="stylesheet" href="&lt;?php echo $file; ?&gt;" /&gt;
    &lt;?php endforeach; ?&gt;
&lt;/head&gt;
&lt;body&gt;
        &lt;div style="padding: 20px 10px;"&gt;
            &lt;?php echo $output; ?&gt;
        &lt;/div&gt;
        &lt;?php foreach($js_files as $file): ?&gt;
            &lt;script src="&lt;?php echo $file; ?&gt;"&gt;&lt;/script&gt;
        &lt;?php endforeach; ?&gt;
&lt;/body&gt;
&lt;/html&gt;
</code></pre>
And congrats! You did install grocery CRUD Enterprise with composer. Now you can enjoy all the power of grocery CRUD Enterprise at your project and why not create something AWESOME today!