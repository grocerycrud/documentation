---
id: grocery-crud-enterprise-installation
title: Installation Guide
description: Step-by-Step installation of Grocery CRUD Enterprise with or without composer.
canonical: docs/grocery-crud-enterprise-installation
previous: api-and-functions-list
next: basic-example
---

# Installation Guide

There are 2 ways to install grocery CRUD Enterprise to your project:

- <a href="#with-composer">With Composer</a> (recommended for latest PHP frameworks like Laravel 9 or Codeigniter 4)
- <a href="#without-composer">Without Composer</a> (recommended for people that are using older PHP Frameworks such as Codeigniter 3)


If you are looking for more specific installation guidance, you can also check the below tutorials:
- <a href="/v3.x/docs/grocery-crud-enterprise-codeigniter-3">Installation in Codeigniter v3</a>
- <a href="/v3.x/docs/grocery-crud-enterprise-codeigniter-4">Installation in Codeigniter v4</a>
- <a href="/v3.x/docs/grocery-crud-enterprise-laravel-8-installation">Laravel v8 installation</a>

<div id="without-composer"></div>

<h2>1. Installation with composer</h2>
If you prefer the video tutorials well... we did create a <a href="https://www.youtube.com/watch?v=buIwAipWSqo" target="_blank" rel="noopener noreferrer">video tutorial</a> with all the below information into one video.

The most recommended way to install PHP libraries nowadays is through <a href="https://getcomposer.org/" target="_blank" rel="noopener noreferrer">composer</a>. 
Grocery CRUD Enterprise has private code and you should have one more step from the normal composer installations. This extra step will change at the future however this work is still in progress and currently you will need to do these 2 extra steps.

<h3>Step 1.</h3>
Download the version of groceryCRUD Enterpirse from https://www.grocerycrud.com/users or through the email that you did get. For example the file to download is: <code>grocery-crud-enterprise-3.0.0.zip</code>

<h3>Step 2.</h3>

Store this file through a folder that you are adding your libraries. This can be anywhere at your local environment 
however it is important to not rename the zip file. As this file is an artifact, we will name our
folder <code>artifacts</code> you can of course use your own names like
<code>lib</code> or even more specific <code>grocery-crud</code> if you are going to use artifacts only for 
groceryCRUD. 

For the below examples we are going to use the folder `artifacts` which is the suggested folder name that is 
recommended by Composer.

<h3>Step 3.</h3>

Add the below code at your composer.json
<pre><code class="js">{
    "repositories": [
        {
            "type": "artifact",
            "url": "/path/to/artifacts/"
        }
    ],
    "require": {
        "grocery-crud/enterprise": "version-number"
    }
}
</code></pre>
For example, for a project that will have only groceryCRUD Enterprise as third party libraries:

<pre><code class="js">{
    "repositories": [
        {
            "type": "artifact",
            "url": "artifacts/"
        }
    ],
    "require": {
        "grocery-crud/enterprise": "3.*.*@dev"
    }
}
</code></pre>
As many people are new to composer and sometimes is really annoying to not have real examples, I will give a more specific example of how your composer will look like. So let's say that you have installed <a href="https://laravel.com/" target="_blank" rel="noopener noreferrer">laravel</a> to your project. Your composer.json will look something like this (see with bold the new lines):
<pre><code class="js">{
    "name": "laravel/laravel",
    "type": "project",
    "description": "The Laravel Framework.",
    "keywords": ["framework", "laravel"],
    "license": "MIT",
    "require": {
        "php": "^8.0.2",
        "grocery-crud/enterprise": "3.*.*@dev",
        "guzzlehttp/guzzle": "^7.2",
        "laravel/framework": "^9.19",
        "laravel/sanctum": "^3.0",
        "laravel/tinker": "^2.7"
    },
    "require-dev": {
        "fakerphp/faker": "^1.9.1",
        "laravel/pint": "^1.0",
        "laravel/sail": "^1.0.1",
        "mockery/mockery": "^1.4.4",
        "nunomaduro/collision": "^6.1",
        "phpunit/phpunit": "^9.5.10",
        "spatie/laravel-ignition": "^1.0"
    },
    "autoload": {
        "psr-4": {
            "App\\": "app/",
            "Database\\Factories\\": "database/factories/",
            "Database\\Seeders\\": "database/seeders/"
        }
    },
    "autoload-dev": {
        "psr-4": {
            "Tests\\": "tests/"
        }
    },
    "scripts": {
        "post-autoload-dump": [
            "Illuminate\\Foundation\\ComposerScripts::postAutoloadDump",
            "@php artisan package:discover --ansi"
        ],
        "post-update-cmd": [
            "@php artisan vendor:publish --tag=laravel-assets --ansi --force"
        ],
        "post-root-package-install": [
            "@php -r \"file_exists('.env') || copy('.env.example', '.env');\""
        ],
        "post-create-project-cmd": [
            "@php artisan key:generate --ansi"
        ]
    },
    "extra": {
        "laravel": {
            "dont-discover": []
        }
    },
    "config": {
        "optimize-autoloader": true,
        "preferred-install": "dist",
        "sort-packages": true,
        "allow-plugins": {
            "pestphp/pest-plugin": true
        }
    },
    "minimum-stability": "dev",
    "prefer-stable": true,
    "repositories": {
        "grocery-crud": {
            "type": "artifact",
            "url": "artifacts/"
        }
    }
}
</code></pre>

<h3>Step 4.</h3>

Now just run <code>composer update</code> or <code>composer install</code> if you are running composer for the first time on your project. Now you did install the enterprise version to your project. You will need also to copy the assets and add it to your public folder for all the JavaScript,CSS, fonts... e.t.c.

<h3>Step 5.</h3>

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

<h3>Step 6.</h3>

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
    'default_language'	=> 'English',

    // This is the assets folder where all the JavaScript, CSS, images and font files are located
    'assets_folder' => '/assets/grocery-crud/',

    // There are only three choices: "uk-date" (dd/mm/yyyy), "us-date" (mm/dd/yyyy) or "sql-date" (yyyy-mm-dd)
    'date_format' => 'uk-date',

    // The default per page when a user firstly see a list page
    'default_per_page'	=> 10,

    // Having some options at the list paging. This is the default one that all the websites are using.
    // Make sure that the number of grocery_crud_default_per_page variable is included to this array.
    'paging_options' => ['10', '25', '50', '100'],

    // The environment is important so we can have specific configurations for specific environments
    'environment' => 'development',

    // Currently you can choose between 'bootstrap-v3', 'bootstrap-v4' and 'bootstrap-v5'
    'skin' => 'bootstrap-v5',

    // Automatically cleans all the inputs by trimming strings and by completely removing any HTML tag
    // to prevent XSS attacks. This is a global configuration for all the inputs so be aware in case you
    // switch this to true
    'xss_clean' => false,

    // The character limiter at the datagrid columns, zero(0) value if you don't want any character
    // limitation to the column
    'column_character_limiter' => 50,

    // Configuration for the texteditor. You can choose between 'minimal' or 'full'
    'text_editor_type' => 'full',

    // The allowed file types on upload. If the file extension doesn't exist in the array
    // it will throw an error and the upload will not be completed
    'upload_allowed_file_types' =>  [
        'gif', 'jpeg', 'jpg', 'png', 'svg', 'tiff', 'doc', 'docx',  'rtf', 'txt', 'odt', 'xls', 'xlsx', 'pdf',
        'ppt', 'pptx', 'pps', 'ppsx', 'mp3', 'm4a', 'ogg', 'wav', 'mp4', 'm4v', 'mov', 'wmv', 'flv', 'avi',
        'mpg', 'ogv', '3gp', '3g2'
    ],

    // If open_in_modal is true then all the form operations (e.g. add, edit, clone... e.t.c.) will
    // open within a modal and we will have the datagrid on the background.
    // In case you would like however to have a standalone page for all the form operations change this to false.
    'open_in_modal' => true,

    // This is the hash symbol (#) that we have at the URL in order to have tha basic operations in the URL so you
    // can navigate back to the URL that you were. For example, when you click at edit form for the id 46, the
    // URL will also change to #/edit/46 so you can also share the link.
    // In case you would like to switch this functionality to off change this to false.
    'hash_in_url' => true,

    // The button style that we have for the action buttons at the datagrid (list) page
    // Choose between 'icon', 'text', 'icon-text'
    'action_button_type' => 'icon-text',

    // The maximum number of buttons that we would like to have for the actions buttons.
    // If the number of buttons exceeds this number then the last button on the right
    // is going to change into a "More" dropdown button.
    // If the maximum number is 1 then as we only have one button as a dropdown list the translation
    // is "Actions" rather than "More"
    'max_action_buttons' => [
        'mobile' => 1,
        'desktop' => 2
    ],

    // Choose between 'left' or 'right'
    'actions_column_side' => 'left',

    // We have noticed that especially after using setRelation within a table that had more than 10K rows
    // that the datagrid was getting slower. For that reason we have optimized SQL wherever possible, and we
    // also have disabled the ordering for setRelation fields.  Keep in mind that the optimization of the queries
    // can be up to 20x faster!! Especially in big tables (e.g. with 1 million rows).
    // In case you would like though to use the ordering for the setRelation field, and you don't have big tables
    // you can set this to `false` and you will probably not notice any difference
    'optimize_sql_queries' => true,

    // Remember the quick search upon refresh. The search information is stored in the browser local storage
    'remember_quick_search' => false,
];</code></pre>
At the config file there are 3 basic sections that we need to be aware of:
<ol>
 	<li><strong>The assets_folder: </strong> The assets folder is the folder that can publicly be accessible by the end user. These folders includes: images, JavaScript files, fonts and stylesheets files.</li>
 	<li><strong>The environment: </strong>Make sure that the <code>development</code> environment is the one that you are using when you are developing the project. and <code>production</code> is the one that is used when you are publishing the website to production.</li>
 	<li><strong>The cache: </strong>Grocery CRUD is based on cache to do as less queries to the database as possible it is <strong>strongly </strong><b>advised </b>to use cache to your project. The default cache is the files cache but of course you can change the cache configurations to add a faster method to cache. All the configurations for the cache can be found at:  <a href="https://framework.zend.com/manual/2.4/en/modules/zend.cache.storage.adapter.html">Zend\Cache\Storage\Adapter</a></li>
</ol>
<h3>Step 7.</h3>

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
And congrats 🍻 ! You have installed grocery CRUD Enterprise with composer. Now you can enjoy all the power of grocery CRUD Enterprise at your project and why not create something AWESOME today!

<h3>Troubleshooting</h3>

In case you have issues with the installation we have created a video tutorial on how to solve some common issues that
you may experience:
- Getting the "Ooooops, something went wrong! If you can see this message, this is probably a misconfiguration in Grocery
  CRUD Enterprise!" message. Video tutorial: <a target="_blank" href="https://www.youtube.com/watch?v=bCJTU6PWhYs">Troubleshooting Grocery CRUD Enteprise part 1</a>

<br/>

<h2>2. Installation without Composer</h2>
For many people composer seems too complicated and they prefer the old fashioned copy-paste way.
Also if you are using a framework that it is not requiring composer or you are using native PHP then the installation without composer is the best choice.
There is nothing bad with the installation without composer, it is just that on updates it will require more manual work.

In case you prefer a video tutorial, we did create the below steps into a video see: <a href="https://www.youtube.com/watch?v=JPJPvGKWxtk">Grocery CRUD Enterprise - Installation without composer</a>

<h3>Step 1.</h3>

Download the zip file for installation without composer. You can also download the newest zip file from: https://www.grocerycrud.com/users .
In order to have a more specific example from now on we will use the name:  <code>grocery-crud-enterprise-v2.9.0-without-composer.zip</code> as the zip file

<h3>Step2.</h3>

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
    'default_language'	=> 'English',

    // This is the assets folder where all the JavaScript, CSS, images and font files are located
    'assets_folder' => '/assets/grocery-crud/',

    // There are only three choices: "uk-date" (dd/mm/yyyy), "us-date" (mm/dd/yyyy) or "sql-date" (yyyy-mm-dd)
    'date_format' => 'uk-date',

    // The default per page when a user firstly see a list page
    'default_per_page'	=> 10,

    // Having some options at the list paging. This is the default one that all the websites are using.
    // Make sure that the number of grocery_crud_default_per_page variable is included to this array.
    'paging_options' => ['10', '25', '50', '100'],

    // The environment is important so we can have specific configurations for specific environments
    'environment' => 'development',

    // Currently you can choose between 'bootstrap-v3', 'bootstrap-v4' and 'bootstrap-v5'
    'skin' => 'bootstrap-v5',

    // Automatically cleans all the inputs by trimming strings and by completely removing any HTML tag
    // to prevent XSS attacks. This is a global configuration for all the inputs so be aware in case you
    // switch this to true
    'xss_clean' => false,

    // The character limiter at the datagrid columns, zero(0) value if you don't want any character
    // limitation to the column
    'column_character_limiter' => 50,

    // Configuration for the texteditor. You can choose between 'minimal' or 'full'
    'text_editor_type' => 'full',

    // The allowed file types on upload. If the file extension doesn't exist in the array
    // it will throw an error and the upload will not be completed
    'upload_allowed_file_types' =>  [
        'gif', 'jpeg', 'jpg', 'png', 'svg', 'tiff', 'doc', 'docx',  'rtf', 'txt', 'odt', 'xls', 'xlsx', 'pdf',
        'ppt', 'pptx', 'pps', 'ppsx', 'mp3', 'm4a', 'ogg', 'wav', 'mp4', 'm4v', 'mov', 'wmv', 'flv', 'avi',
        'mpg', 'ogv', '3gp', '3g2'
    ],

    // If open_in_modal is true then all the form operations (e.g. add, edit, clone... e.t.c.) will
    // open within a modal and we will have the datagrid on the background.
    // In case you would like however to have a standalone page for all the form operations change this to false.
    'open_in_modal' => true,

    // This is the hash symbol (#) that we have at the URL in order to have tha basic operations in the URL so you
    // can navigate back to the URL that you were. For example, when you click at edit form for the id 46, the
    // URL will also change to #/edit/46 so you can also share the link.
    // In case you would like to switch this functionality to off change this to false.
    'hash_in_url' => true,

    // The button style that we have for the action buttons at the datagrid (list) page
    // Choose between 'icon', 'text', 'icon-text'
    'action_button_type' => 'icon-text',

    // The maximum number of buttons that we would like to have for the actions buttons.
    // If the number of buttons exceeds this number then the last button on the right
    // is going to change into a "More" dropdown button.
    // If the maximum number is 1 then as we only have one button as a dropdown list the translation
    // is "Actions" rather than "More"
    'max_action_buttons' => [
        'mobile' => 1,
        'desktop' => 2
    ],

    // Choose between 'left' or 'right'
    'actions_column_side' => 'left',

    // We have noticed that especially after using setRelation within a table that had more than 10K rows
    // that the datagrid was getting slower. For that reason we have optimized SQL wherever possible, and we
    // also have disabled the ordering for setRelation fields.  Keep in mind that the optimization of the queries
    // can be up to 20x faster!! Especially in big tables (e.g. with 1 million rows).
    // In case you would like though to use the ordering for the setRelation field, and you don't have big tables
    // you can set this to `false` and you will probably not notice any difference
    'optimize_sql_queries' => true,

    // Remember the quick search upon refresh. The search information is stored in the browser local storage
    'remember_quick_search' => false,
];</code></pre>
At the config file there are 3 basic sections that we need to be aware of:
<ol>
 	<li><strong>The assets_folder: </strong> The assets folder is the folder that can publicly be accessible by the end user. These folders includes: images, JavaScript files, fonts and stylesheets files.</li>
 	<li><strong>The environment: </strong>Make sure that the <code>development</code> environment is the one that you are using when you are developing the project. and <code>production</code> is the one that is used when you are publishing the website to production.</li>
 	<li><strong>The cache: </strong>Grocery CRUD is based on cache to do as less queries to the database as possible it is <strong>strongly </strong><b>advised </b>to use cache to your project. The default cache is the files cache but of course you can change the cache configurations to add a faster method to cache. All the configurations for the cache can be found at:  <a href="https://framework.zend.com/manual/2.4/en/modules/zend.cache.storage.adapter.html">Zend\Cache\Storage\Adapter</a></li>
</ol>
<h3>Step3.</h3>

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


<h3>Troubleshooting</h3>

In case you have issues with the installation we have created a video tutorial on how to solve some common issues that
you may experience:
- Getting the "Ooooops, something went wrong! If you can see this message, this is probably a misconfiguration in Grocery
  CRUD Enterprise!" message. Video tutorial: <a target="_blank" href="https://www.youtube.com/watch?v=bCJTU6PWhYs">Troubleshooting Grocery CRUD Enteprise part 1</a>

<br/>