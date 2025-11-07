---
id: grocery-crud-enterprise-codeigniter-4
title: Codeigniter 4 Installation
description: Step-by-step installation of Grocery CRUD Enterprise on Codeigniter version 4.
canonical: docs/grocery-crud-enterprise-codeigniter-4
previous: api-and-functions-list
next: basic-example
---

# Codeigniter 4 Installation

Below you will find the steps to install Grocery CRUD Enterprise on Codeigniter 4.
If you follow these steps carefully, you should be able to successfully install Grocery CRUD Enterprise
on your Codeigniter project easily.
Keep in mind that this tutorial may require several steps, but it is actively updated to provide the most accurate
and up-to-date instructions.

> Instead of relying solely on this tutorial, we'd like to draw your attention to the availability of 
> a <a href="/users/enterprise-version-wizard" target="_blank">helpful wizard</a> specially designed to streamline 
> the installation process of Grocery CRUD Enterprise for your specific project 🚀. 
> This wizard provides a concise, step-by-step tutorial with five easy-to-follow instructions. 
> To access this tool, simply click on the following 
> link: <a href="/users/enterprise-version-wizard" target="_blank">Grocery CRUD Enterprise Installation Wizard</a>. 
> Users are already using it, and their feedback has been overwhelmingly positive ❤️. Enjoy!

Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Step 1. Preparation](#step-1-preparation)
- [Step 2. Installation](#step-2-installation)
- [Step 3. Copying assets folder](#step-3-copying-assets-folder)
- [Step 4. Configuration file](#step-4-configuration-file)
- [Step 5. Your Controller](#step-5-your-controller)
- [Step 6. Routing](#step-6-routing)
- [Troubleshooting](#troubleshooting)

## Introduction

Since currently Codeigniter 4 is suggested to be installed <strong>via Composer</strong>, we will follow the same approach.
If you would like to install Grocery CRUD Enterprise on Codeigniter 4 without composer you can follow this tutorial:
[Install without composer](/v3.x/docs/grocery-crud-enterprise-installation#without-composer)

> <strong>Notice:</strong> Grocery CRUD Enterprise is a framework-agnostic library. 
> That simply means that it doesn't matter which framework you are using, and it doesn't matter which architecture 
> or tools (e.g. composer) you are using.
> This tutorial is taking some architecture decisions basically for you. If you need to have the full 
> freedom of what structure to choose, we are suggesting to see the full installation guide 
> <a href="/v3.x/docs/grocery-crud-enterprise-installation">here</a>.

## Prerequisites

- You have purchased <a href="https://www.grocerycrud.com/enterprise" target="_blank">Grocery CRUD Enterprise</a> and
  you have access to <a href="https://www.grocerycrud.com/users/" rel="nofollow" target="_blank">Client's page</a>.
- PHP 7.4 or later.
- You have <a href="https://getcomposer.org/" target="_blank">composer</a> installed
- You already have installed Codeigniter 4 into your project via composer.

## Step 1. Preparation

Considering that you've already had a `composer.json` file into your project, run the following command:

<pre><code class="language-sh">composer config repositories.grocery-crud '{"type": "composer", "url": "https://composer.grocerycrud.com/"}' --file composer.json</code></pre>

If the above code succeeds, your `composer.json` file will look like this:

<pre><code class="language-json">{
    "name": "codeigniter4/appstarter",
    "type": "project",
    "description": "CodeIgniter4 starter app",
    "homepage": "https://codeigniter.com",
    "license": "MIT",
    "require": {
        "php": "^7.4 || ^8.0",
        "codeigniter4/framework": "^4.0"
    },
    "require-dev": {
        "fakerphp/faker": "^1.9",
        "mikey179/vfsstream": "^1.6",
        "phpunit/phpunit": "^9.1"
    },
    "suggest": {
        "ext-fileinfo": "Improves mime type detection for files"
    },
    "autoload": {
        "exclude-from-classmap": [
            "**/Database/Migrations/**"
        ]
    },
    "autoload-dev": {
        "psr-4": {
            "Tests\\Support\\": "tests/_support"
        }
    },
    "scripts": {
        "test": "phpunit"
    },
    "support": {
        "forum": "http://forum.codeigniter.com/",
        "source": "https://github.com/codeigniter4/CodeIgniter4",
        "slack": "https://codeigniterchat.slack.com"
    },
    "repositories": {
        "grocery-crud": {
            "type": "composer",
            "url": "https://composer.grocerycrud.com/"
        }
    }
}
</code></pre>

If the command fails for any reason don't worry too much! You can always copy the section "repositories" from the above code and paste it in your
`composer.json`.

## Step 2. Installation

Now you can install the library with the following command:

<pre><code class="language-sh">composer require "grocery-crud/enterprise:^3.1" --prefer-dist</code></pre>

The first time you run the above command, you'll be asked to provide your `username` and `password` for the
composer package `grocery-crud/enterprise`. Your username is your email address and your password is the license key
for Grocery CRUD Enterprise. You can find your credentials in
the <a href="https://www.grocerycrud.com/users/profile" target="_blank">My Profile</a> page at the top right avatar
icon of <a href="https://www.grocerycrud.com/users/enterprise-version-wizard" target="_blank">user's page</a>.

After entering the correct username and password in the command line, you'll be asked if you want to store your
credentials in the `auth.json` file. I recommend answering `Y` (yes) to this question, so you won't have to
provide the credentials again in the future.

If the command succeeds, you will see something like this:

![Installing grocery-crud/enterprise](/uploads/documentation/composer-success.png)

Now theoretically you've just installed Grocery CRUD. However, there are few more steps in order to make it work.

## Step 3. Copying assets folder

As Grocery CRUD is a CRUD Generator that also has CSS and JavaScript files we need to make sure that we also have the
public assets including in our public folder.

In order to install all your assets to your project. You need to <strong>manually copy</strong> the content of the
folder `public` to your Codeigniter `public` folder. More specifically go to : <code>vendor/grocery-crud/enterprise/public</code> and copy
the folder `vendor` to your Codeigniter `public` folder. For example after the copy of the folder your folder structure will look like this:

<pre>
├── app
├── public
│   └── vendor
│       └── grocery-crud
│           ├── css
│           ├── icons
│           ├── js
│           └── static
...
├── composer.json
├── composer.lock
├── preload.php
└── vendor
</pre>

## Step 4. Configuration file 

We did currently install Grocery CRUD Enterprise in our project, and we need to create our configuration files in order to make it work! Go to <code>app/Config</code> and create a file with name <code>GroceryCrudEnterprise.php</code>. As the configuration is different than other frameworks we will use a custom one that will look like this (just copy really the code below)

<pre><code class="language-php">&lt;?php namespace Config;

use CodeIgniter\Config\BaseConfig;

class GroceryCrudEnterprise extends BaseConfig
{
    public function getDefaultConfig() {
        helper('url');

        return [
            // So far 35 languages including: Afrikaans, Arabic, Bengali, Bulgarian, Catalan, Chinese, Czech, Danish,
            // Dutch, English, French, German, Greek, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean,
            // Lithuanian, Latvian, Mongolian, Norwegian, Persian, Polish, Portuguese (pt-PT.Portuguese),
            // Brazilian Portuguese (pt-BR.Portuguese), Romanian,, Russian, Slovak, Spanish, Thai,
            // Turkish, Ukrainian, Vietnamese
            'default_language'	=> 'English',
        
            // This is the assets folder where all the JavaScript, CSS, images and font files are located
            'assets_folder' => base_url() . '/vendor/grocery-crud/',
        
            // The default per page when a user firstly see a list page
            'default_per_page'	=> 10,

            // Having some options at the list paging. This is the default one that all the websites are using.
            // Make sure that the number of grocery_crud_default_per_page variable is included to this array.
            'paging_options' => ['10', '25', '50', '100'],

            // The environment is important, so we can have specific configurations for specific environments
            'environment' => 'development',

            // Currently you can choose between 'bootstrap-v3', 'bootstrap-v4' and 'bootstrap-v5'
            'theme' => 'bootstrap-v5',

            // Automatically cleans all the inputs by trimming strings and by completely removing any HTML tag
            // to prevent XSS attacks. This is a global configuration for all the inputs so be aware in case you
            // switch this to true
            'xss_clean' => false,

            // The character limiter at the datagrid columns, zero(0) value if you don't want any character
            // limitation to the column
            'column_character_limiter' => 50,

            // The allowed file types on upload. If the file extension doesn't exist in the array
            // it will throw an error and the upload will not be completed
            'upload_allowed_file_types' =>  [
                'gif', 'jpeg', 'jpg', 'png', 'svg', 'tiff', 'doc', 'docx',  'rtf', 'txt', 'odt', 'xls', 'xlsx', 'pdf',
                'ppt', 'pptx', 'pps', 'ppsx', 'mp3', 'm4a', 'ogg', 'wav', 'mp4', 'm4v', 'mov', 'wmv', 'flv', 'avi',
                'mpg', 'ogv', '3gp', '3g2'
            ],

            // Set this variable to true if you want to remove the file from the server
            // when a row is deleted. The file will also be removed when the user is
            // removing the file from the upload field.
            // By default, the file is not deleted from the server in these cases.
            'remove_file_on_delete' => false,

            // Show image preview - As we currently don't have thumbnails to show please keep in mind that the full
            // image will be loaded in the browser.
            'show_image_preview' => false,

            // If open_in_modal is true then all the form operations (e.g. add, edit, clone... e.t.c.) will
            // open within a modal and we will have the datagrid on the background.
            // In case you would like however to have a standalone page for all the form operations change this to false.
            'open_in_modal' => true,

            // Have url history for the CRUD forms, so it will be easier for the user
            // to navigate back to the previous form page. For example /add, /edit/11, /clone/22, ... e.t.c.
            'url_history' => true,

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
            'optimize_sql_queries' => false,

            // Publish external events to the frontend (e.g. when the user clicks at the edit button)
            // For security reasons the configuration is set to false by default.
            'publish_events' => false,

            // Remember the sorting, the search and the paging upon refresh. The information is stored in the browser local storage
            'remember_state_upon_refresh' => true,

            // Remember the filters upon refresh. The information is stored in the browser local storage
            // Please note that if you have remember_state_upon_refresh set to false then this configuration
            // will also be set to false.
            'remember_filters_upon_refresh' => true,

            // Include JavaScript files in the main output and don't return them at 'js_files' variable
            // This is useful for quicker installations/demos, but it is recommended to set this to false
            // and have all of your JavaScript files at the bottom of your page before the body tag ends.
            // Please consider that when JavaScript files are included directly in the output, you lose the ability
            // to control when and where these files are loaded.
            'display_js_files_in_output' => false,
        ];
    }
}</code></pre>
<div id="final-structure">In order to confirm that so far you did copy the correct files, your folder structure will look something like this:</div>
<pre>.
├── LICENSE
├── README.md
├── app
│   ├── Common.php
│   ├── Config
│   │   ├── App.php
│   │   ├── Autoload.php
│   │   ├── ...
│   │   ├── Format.php
│   │   ├── <strong>GroceryCrudEnterprise.php</strong>
│   │   ├── Honeypot.php
│   │   ├── ...
│   │   └── View.php
│   ├── Filters
│   ├── Helpers
│   ├── Language
│   ├── Models
│   ├── ThirdParty
│   ├── Views
│   └── index.html
├── composer.json
├── contributing.md
├── env
├── license.txt
├── phpunit.xml.dist
├── public
│   └── vendor
│       └── grocery-crud
│           ├── css
│           ├── icons
│           ├── js
│           └── static
│   ├── favicon.ico
│   ├── index.php
│   └── robots.txt
├── spark
├── system
├── vendor
├── tests
└── writable</pre>

## Step 5. Your Controller

Now you are ready basically to use grocery CRUD Enterprise. You only need some small modifications. The easiest way to create two private methods to your controller that it will look like this:
<pre><code class="language-php">&lt;?php namespace App\Controllers;

// At the top of your controller file, add the following import
use GroceryCrud\Core\GroceryCrud;

...

private function _getDbData() {
    $db = (new \Config\Database())-&gt;default;
          return [
              'adapter' =&gt; [
              'driver' =&gt; 'Pdo_Mysql',
              'host'     =&gt; $db['hostname'],
              'database' =&gt; $db['database'],
              'username' =&gt; $db['username'],
              'password' =&gt; $db['password'],
              'charset' =&gt; 'utf8'
          ]
    ];
}
private function _getGroceryCrudEnterprise($bootstrap = true, $jquery = true) {
        $db = $this-&gt;_getDbData();
        $config = (new \Config\GroceryCrudEnterprise())-&gt;getDefaultConfig();

        $groceryCrud = new GroceryCrud($config, $db);

        $groceryCrud->setCsrfTokenName(csrf_token());
        $groceryCrud->setCsrfTokenValue(csrf_hash());

        return $groceryCrud;
}</code></pre>
And now when you want to use groceryCRUD enterprise you will simply do this:
<pre><code class="language-php">// Your function at your controller
public function customers()
{
    $crud = $this-&gt;_getGroceryCrudEnterprise();
    $crud-&gt;setTable('customers');
    $crud-&gt;setSubject('Customer', 'Customers');

    $output = $crud-&gt;render();
    
    return $this-&gt;_example_output($output);
}

private function _example_output($output = null) {
    if (isset($output-&gt;isJSONResponse) &amp;&amp; $output-&gt;isJSONResponse) {
                header('Content-Type: application/json; charset=utf-8');
                echo $output-&gt;output;
                exit;
    }

    return view('example.php', (array)$output);
}
</code></pre>
A full working example of a controller with name <code>Example</code> located at <code>app/Controllers/Example.php</code> can be found here:

<pre><code class="language-php">&lt;?php
namespace App\Controllers;

use GroceryCrud\Core\GroceryCrud;

class Example extends BaseController
{
    public function index() 
    {
        $output = (object)[
            'js_files' => [],
            'output' => ''
        ];

        return $this->_example_output($output);
    }
    public function customers()
    {
        $crud = $this->_getGroceryCrudEnterprise();

        $crud->setTable('customers');
        $crud->setSubject('Customer', 'Customers');

        $output = $crud->render();

        return $this->_example_output($output);
    }

    private function _example_output($output = null) {
        if (isset($output->isJSONResponse) && $output->isJSONResponse) {
                    header('Content-Type: application/json; charset=utf-8');
                    echo $output->output;
                    exit;
        }

        return view('example.php', (array)$output);
    }

    private function _getDbData() {
        $db = (new \Config\Database())->default;
        return [
            'adapter' => [
                'driver' => 'Pdo_Mysql',
                'host'     => $db['hostname'],
                'database' => $db['database'],
                'username' => $db['username'],
                'password' => $db['password'],
                'charset' => 'utf8'
            ]
        ];
    }
    private function _getGroceryCrudEnterprise($bootstrap = true, $jquery = true) {
        $db = $this->_getDbData();
        $config = (new \Config\GroceryCrudEnterprise())->getDefaultConfig();

        $groceryCrud = new GroceryCrud($config, $db);

        $groceryCrud->setCsrfTokenName(csrf_token());
        $groceryCrud->setCsrfTokenValue(csrf_hash());

        return $groceryCrud;
    }
}</code></pre>

Go to <code>app/Views</code> and create a file with name <code>example.php</code> that will look like this:

<pre><code class="language-php">&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
 &lt;meta charset="utf-8" /&gt;

&lt;?php foreach($js_files as $file): ?&gt;
 
 &lt;script src="&lt;?php echo $file; ?&gt;"&gt;&lt;/script&gt;
&lt;?php endforeach; ?&gt;
 
&lt;style type='text/css'&gt;
body
{
 font-family: Arial;
 font-size: 14px;
}
&lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;!-- Beginning header --&gt;
 &lt;div&gt;
     &lt;a href='&lt;?php echo site_url('example/customers')?&gt;'&gt;Customers&lt;/a&gt;
 &lt;/div&gt;
&lt;!-- End of header--&gt;
 
 &lt;!-- Beginning of main content --&gt;
 &lt;div style='height:20px;'&gt;&lt;/div&gt; 
 &lt;div style='padding: 10px;'&gt;
     &lt;?php echo $output; ?&gt;
 
 &lt;/div&gt;
 &lt;!-- End of main content --&gt;
 
&lt;!-- Beginning footer --&gt;

&lt;!-- End of Footer --&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>

## Step 6. Routing

Since Codeigniter 4.2.0 or later the Routing is not defaulting to auto-routing. 
This means that you will need to add the routes manually. Go to <code>app/Config/Routes.php</code> and add the 
below code for every function that is using grocery CRUD:

<pre><code class="language-php">// Make sure that you always add both lines for each CRUD function
$routes->add('/example/customers', 'Example::customers');
$routes->add('/example/customers/(:segment)(/(:segment))?', 'Example::customers/$1/$2');
</code></pre>

## Troubleshooting
<strong>1. Getting the message "Ooooops, something went wrong!"</strong>
The most common mistake of the installation of grocery CRUD Enteprise is when the assets_folder has a wrong path. If you did follow all the steps and you see that your webpage looks like that:

<img style="border: 1px solid #DDD;" src="/uploads/documentation/wrong-codeigniter-installation.png" alt="wrong-codeigniter-installation" />

then make sure that you have configured your <code>app/Config/App.php</code>
file at the line <code>public $baseURL = 'http://localhost:8080';</code>. For example if your project URL looks like this:
<code>http://localhost/my-test-project/public/index.php</code> then your <code>baseURL</code> should look like this:
<code>public $baseURL = 'http://localhost/my-test-project/public/';</code>

It is really important to also don't forget the trailing slash at the end of the URL.

The most common approach, best for security and suggested way of Codeigniter 4 installation is to configure your URL to point directly to your public folder. For example for apache virtual hosts you will probably have an apache configuration that is looking like this:

<pre><code>&lt;VirtualHost *:80&gt;
	DocumentRoot "/var/www/my-test-project/public"
	ServerName my-test-project.local
	ServerAlias www.my-test-project.local
&lt;/VirtualHost&gt;</code></pre>

At the above example your <code>$baseURL</code> should look like this:

<code>public $baseURL = 'http://my-test-project.local/';</code>

Too lazy to read the documentation? We have also created a video tutorial for that: <a target="_blank" href="https://www.youtube.com/watch?v=bCJTU6PWhYs">Troubleshooting Grocery CRUD Enteprise part 1</a>.

<strong>2. Getting an empty box with a border</strong>
If you are getting an empty box with a border that is looking like this:

<img style="border: 1px solid #DDD;" src="/uploads/documentation/gcrud-enterpise-empty-box.png" alt="wrong-codeigniter-installation" />

This is because by default Codeigniter 4 has as <code>CI_ENVIRONMENT=production</code> in simple words Codeigniter is trying to hide all of the errors by default and you will not get any errors. You can bypass that by renaming the <code>env</code> that you have at the root to <code>.env</code> and uncomment the below line:
<pre><code class="language-php"># CI_ENVIRONMENT = production</code></pre>
And replace it with:
<pre><code class="language-php">CI_ENVIRONMENT = development</code></pre>
If you are using Google Chrome press right click "Inspect Element" and then go to the Network tab and check where the response is red (or else it returns header 500). Once you click on the URL you can see the error as per below screenshot:

<img style="border: 1px solid #DDD;" src="/uploads/documentation/inspect-error.png" alt="inspect-error" />

You can also press right click "Open in new Tab" to see the error at full screen rather than the "Preview" tab.

For example in our case we've forgotten to change the default database credentials to our ones. So by going to <code>.env</code> file and uncommenting this lines:
<pre><code class="language-php"># database.default.hostname = localhost
# database.default.database = ci4
# database.default.username = root
# database.default.password = root
# database.default.DBDriver = MySQLi</code></pre>
to your specific database credentials everything is just working smoothly.
