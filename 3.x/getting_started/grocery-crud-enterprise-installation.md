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

- <a href="/v3.x/docs/grocery-crud-enterprise-codeigniter-4">Installation in Codeigniter v4</a>
- <a href="/v3.x/docs/grocery-crud-enterprise-laravel-10-installation">Laravel v10 installation</a>

<div id="with-composer"></div>

<h2>1. Installation with composer</h2>

The most recommended way to install PHP libraries nowadays is through <a href="https://getcomposer.org/" target="_blank" rel="noopener noreferrer">composer</a>.
Grocery CRUD Enterprise has private code and there are two more steps from the normal composer installations.
This extra steps will change at the future however this work is still in progress.

<h3>Prerequisites</h3>

- You have purchased <a href="https://www.grocerycrud.com/enterprise" target="_blank">Grocery CRUD Enterprise</a> and
  you have access to <a href="https://www.grocerycrud.com/users/" rel="nofollow" target="_blank">Client's page</a>.
- PHP 7 or later.
- You already have a `composer.json` file into your project.
- You've already installed composer to your project and the vendor files by using the command `composer install`.

<h3>Step 1. Download</h3>
Login to <a href="https://www.grocerycrud.com/users/" rel="nofollow" target="_blank">Client's page</a> and navigate to
"Version 3 BETA" from the sidebar menu.

![Version 3 Sidebar Menu](/uploads/documentation/version-3-sidebar-menu.png)

Then download the zip file that say's "Installation with composer".

![Download composer zip file](/uploads/documentation/download-composer-zip-file.png)

Your file will look something like this: <code>grocery-crud-enterprise-3.0.0-beta.1.zip</code>.

<h3>Step 2. Creation of artifacts folder</h3>

Go to your project root folder and create a new folder with the name <code>artifacts</code>. Now copy the zip file as-is.
Do not extract or change the name of the zip file.

After this change your folder structure will look like this:

<pre>
├── app
├── artifacts
│   └── grocery-crud-enterprise-3.0.0-beta.1.zip
├── vendor
├── composer.json
...
</pre>

Considering that you've already had a `composer.json` file into your project, run the following command:

<pre><code class="language-sh">composer config repositories.grocery-crud artifact artifacts/</code></pre>

If the above code succeeds, your composer file will look like this:

<pre><code class="language-json">{
    "name": "johnny/my-awesome-project",
    "autoload": {
        "psr-4": {
            "Johnny\\MyAwesomeProject\\": "src/"
        }
    },
    "authors": [
        {
            "name": "John Skoubourdis"
        }
    ],
    "repositories": {
        "grocery-crud": {
            "type": "artifact",
            "url": "artifacts/"
        }
    }
}
</code></pre>

If the command fails for any reason don't worry too much! You can always copy the sections "repositories" from the above code and paste them in your
`composer.json`.

<h3>Step 3. Installation</h3>

Now you can install the library with the following command:

<pre><code class="language-sh">composer require "grocery-crud/enterprise:3.*.*@dev"</code></pre>

If the command succeeds, you will see something like this:

![Installing grocery-crud/enterprise 3.0.0-beta.1](/uploads/documentation/composer-success.png)

and your composer file will look like this:

<pre><code class="language-json">{
    "name": "johnny/my-awesome-project",
    "autoload": {
        "psr-4": {
            "Johnny\\MyAwesomeProject\\": "src/"
        }
    },
    "authors": [
        {
            "name": "John Skoubourdis"
        }
    ],
    "repositories": {
        "grocery-crud": {
            "type": "artifact",
            "url": "artifacts/"
        }
    },
    "require": {
        "grocery-crud/enterprise": "3.*.*@dev"
    }
}</code></pre>

Now theoretically you've just installed Grocery CRUD. However, there are few more steps in order to make it work.

<h3>Step 4. Copying assets folder</h3>

As Grocery CRUD is a CRUD Generator that also has CSS and JavaScript files we need to make sure that we also have the
public assets including in our public folder.

In order to install all your assets to your project. You need to <strong>manually copy</strong> the content of the
folder `public` to your public structured project.

Let's have an example! Let's say that you project structure looks like this:

<pre>├── app
├── bootstrap
├── public
│   ├── css
│   └── fonts
...
├── tests
└── vendor
</pre>

In that case the best place to have your public folder of groceryCRUD enterprise is at `pubic/vendor/grocery-crud`
folder. So you will need to copy the folders from : <code>vendor/grocery-crud/enterprise/public</code>
to the public folder of your project. So after the copy of the folders, your new structure will look like this:

<pre>├── app
├── bootstrap
├── public
│   ├── css
│   ├── fonts
│   └── vendor
│       └── grocery-crud
│           ├── css
│           ├── icons
│           ├── js
│           └── static
...
├── tests
└── vendor
</pre>

<h3>Step 6.</h3>

Now you need to create your configurations files in order to make grocery CRUD Enterprise to work. So basically there are 3 things that you will need to configure:

1. Your configuration file
2. The database configurations

You can find all the code below of the examples at:
<code>vendor/grocery-crud/enterprise/example</code>

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

As in grocery CRUD Enterprise we are using the power of Lamina Framework the drivers are from Lamina Framework DB.
For more you can see the documentation at <a target="_blank" href="https://docs.laminas.dev/laminas-db/adapter/">Laminas\Db\Adapter\Adapter</a>.

The second configuration file is the one that you need to include for grocery CRUD. The configuration file will look like the below:

<pre><code class="language-php">&lt;?php

return [
    // So far 34 languages including: Afrikaans, Arabic, Bengali, Bulgarian, Catalan, Chinese, Czech, Danish,
    // Dutch, English, French, German, Greek, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean,
    // Lithuanian, Mongolian, Norwegian, Persian, Polish, Portuguese, Brazilian Portuguese, Romanian,
    // Russian, Slovak, Spanish, Thai, Turkish, Ukrainian, Vietnamese
    'default_language'  => 'English',

    // This is the assets folder where all the JavaScript, CSS, images and font files are located
    'assets_folder' => '/vendor/grocery-crud/',

    // The default per page when a user firstly see a list page
    'default_per_page'	=> '10',

    // Having some options at the list paging. This is the default one that all the websites are using.
    // Make sure that the number of grocery_crud_default_per_page variable is included to this array.
    'paging_options' => ['10', '25', '50', '100'],

    // The environment is important, so we can have specific configurations for specific environments
    'environment' => 'development',

    // The default theme that Grocery CRUD will use. Currently, you can choose between 'bootstrap-v4' and 'bootstrap-v5'
    'theme' => 'bootstrap-v5',

    'xss_clean' => false,

    // The character limiter at the datagrid columns, zero(0) value if you don't want any character
    // limitation to the column
    'column_character_limiter' => 50,

    // The allowed file types on upload. If the file extension doesn't exist in the array
    // it will throw an error and the upload will not be completed
    'upload_allowed_file_types' =>  [
        'gif', 'jpeg', 'jpg', 'png', 'svg', 'tiff', 'doc', 'docx',  'rtf', 'txt', 'odt', 'xls', 'xlsx', 'pdf',
        'ppt', 'pptx', 'pps', 'ppsx', 'mp3', 'm4a', 'ogg', 'wav', 'mp4', 'm4v', 'mov', 'wmv', 'flv', 'avi',
        'mpg', 'ogv', '3gp', '3g2', 'psd'
    ],

    'remove_file_on_delete' => false,

    // Show image preview - As we currently don't have thumbnails to show please keep in mind that the full
    // image will be loaded in the browser.
    'show_image_preview' => true,

    'open_in_modal' => true,

    'url_history' => true,

    // Configuration to publish action events (coming from Redux) with all the details that the action is having
    // This is useful to have a better control over the events that are being triggered in the application
    // However, please use with caution as this may leak some sensitive information to the application
    // For more read about security issues about XSS see wikipedia link
    // here https://en.wikipedia.org/wiki/Cross-site_scripting
    'publish_events' => false,

    // The button style that we have for the action buttons at the datagrid (list) page
    // Choose between 'icon', 'text', 'icon-text'
    'action_button_type' => 'icon-text',

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
];
</code></pre>

At the config file there are 2 basic sections that we need to be aware of:

<ol>
 	<li><strong>The assets_folder: </strong> The assets folder is the folder that can publicly be accessible by the end user. These folders includes: images, JavaScript files, fonts and stylesheets files.</li>
 	<li><strong>The environment: </strong>Make sure that the <code>development</code> environment is the one that you are using when you are developing the project. and <code>production</code> is the one that is used when you are publishing the website to production.</li>
</ol>
<h3>Step 7.</h3>

And now we are ready to make grocery CRUD Enterprise to put it to work! As per the previous step, the files `view.php` 
and `example.php` are included in the `vendor/grocery-crud/enterprise/example` folder.

Let's have an example of the very first use. A first example without any framework installation will look like this:

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
  CRUD Enterprise!" message. I've created a video tutorial for Grocery CRUD Enterprise version 2 but it can be also applied
  to version 3: <a target="_blank" href="https://www.youtube.com/watch?v=bCJTU6PWhYs">Troubleshooting Grocery CRUD Enteprise part 1</a>

<br/>

<div id="without-composer"></div>

<h2>2. Installation without Composer</h2>

Many people find using a composer to be intimidating, so they opt for the more familiar copy-and-paste method 😃. 
This is especially common when working with frameworks that don't require a composer (e.g. Codeigniter 3), or when 
using native PHP. While there's nothing wrong with this approach, it does require more manual steps when we install
or upgrade Grocery CRUD Enterprise.

<h3>Prerequisites</h3>

- You have purchased <a href="https://www.grocerycrud.com/enterprise" target="_blank">Grocery CRUD Enterprise</a> and
  you have access to <a href="https://www.grocerycrud.com/users/" rel="nofollow" target="_blank">Client's page</a>.
- PHP 7 or later.
- You have enough patience to copy-paste some files and folders 😃.

<h3>Step 1. Download</h3>
Login to <a href="https://www.grocerycrud.com/users/" rel="nofollow" target="_blank">Client's page</a> and navigate to
"Version 3 BETA" from the sidebar menu.

![Version 3 Sidebar Menu](/uploads/documentation/version-3-sidebar-menu.png)

Then download the zip file that say's "Installation without composer".

![Download composer zip file](/uploads/documentation/download-without-composer.png)

Your file will look something like this: <code>grocery-crud-enterprise-3.0.0-beta.1-without-composer.zip</code>.

<h3>Step2.</h3>

Unzip the file and you will find a file structure like that:

<pre>├── LICENCE.md
├── change-log.txt
├── examples
│   ├── config.php
│   ├── database.php
│   ├── example.php
│   └── view.php
├── libraries
│   ├── autoload.php
│   ├── composer
│   │   ├── ClassLoader.php
│   │   ├── ...
│   │   └── platform_check.php
│   ├── grocery-crud
│   │   └── enterprise
│   ├── laminas
│   │   ├── laminas-db
│   │   └── laminas-stdlib
│   ├── scoumbourdis
│   │   ├── phpexcel
│   │   └── upload
│   └── vlucas
│       └── valitron
└── public
    └── vendor
        └── grocery-crud
            ├── css
            ├── icons
            ├── js
            └── static
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

As in grocery CRUD Enterprise we are using the power of Lamina Framework the drivers are from Lamina Framework DB.
For more you can see the documentation at <a target="_blank" href="https://docs.laminas.dev/laminas-db/adapter/">Laminas\Db\Adapter\Adapter</a>.

The second configuration file is the one that you need to include for grocery CRUD. The configuration file will look like the below:

<pre><code class="language-php">&lt;?php
// config.php

return [
    // So far 34 languages including: Afrikaans, Arabic, Bengali, Bulgarian, Catalan, Chinese, Czech, Danish,
    // Dutch, English, French, German, Greek, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean,
    // Lithuanian, Mongolian, Norwegian, Persian, Polish, Portuguese, Brazilian Portuguese, Romanian,
    // Russian, Slovak, Spanish, Thai, Turkish, Ukrainian, Vietnamese
    'default_language'  => 'English',

    // This is the assets folder where all the JavaScript, CSS, images and font files are located
    'assets_folder' => '/vendor/grocery-crud/',

    // The default per page when a user firstly see a list page
    'default_per_page'	=> '10',

    // Having some options at the list paging. This is the default one that all the websites are using.
    // Make sure that the number of grocery_crud_default_per_page variable is included to this array.
    'paging_options' => ['10', '25', '50', '100'],

    // The environment is important, so we can have specific configurations for specific environments
    'environment' => 'development',

    // The default theme that Grocery CRUD will use. Currently, you can choose between 'bootstrap-v4' and 'bootstrap-v5'
    'theme' => 'bootstrap-v5',

    'xss_clean' => false,

    // The character limiter at the datagrid columns, zero(0) value if you don't want any character
    // limitation to the column
    'column_character_limiter' => 50,

    // The allowed file types on upload. If the file extension doesn't exist in the array
    // it will throw an error and the upload will not be completed
    'upload_allowed_file_types' =>  [
        'gif', 'jpeg', 'jpg', 'png', 'svg', 'tiff', 'doc', 'docx',  'rtf', 'txt', 'odt', 'xls', 'xlsx', 'pdf',
        'ppt', 'pptx', 'pps', 'ppsx', 'mp3', 'm4a', 'ogg', 'wav', 'mp4', 'm4v', 'mov', 'wmv', 'flv', 'avi',
        'mpg', 'ogv', '3gp', '3g2', 'psd'
    ],

    'remove_file_on_delete' => false,

    // Show image preview - As we currently don't have thumbnails to show please keep in mind that the full
    // image will be loaded in the browser.
    'show_image_preview' => true,

    'open_in_modal' => true,

    'url_history' => true,

    // Configuration to publish action events (coming from Redux) with all the details that the action is having
    // This is useful to have a better control over the events that are being triggered in the application
    // However, please use with caution as this may leak some sensitive information to the application
    // For more read about security issues about XSS see wikipedia link
    // here https://en.wikipedia.org/wiki/Cross-site_scripting
    'publish_events' => false,

    // The button style that we have for the action buttons at the datagrid (list) page
    // Choose between 'icon', 'text', 'icon-text'
    'action_button_type' => 'icon-text',

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
];

</code></pre>

At the config file there are 3 basic sections that we need to be aware of:

<ol>
 	<li><strong>The assets_folder: </strong> The assets folder is the folder that can publicly be accessible by the end user. 
These folders include: images, JavaScript files, fonts and stylesheets files.</li>
 	<li><strong>The environment: </strong>Make sure that the <code>development</code> environment is the one that you are using when you are developing the project. and <code>production</code> is the one that is used when you are publishing the website to production.</li>
</ol>
<h3>Step3.</h3>

If you are using native PHP (without any framework) then you just need to copy the examples at the desired folder.

As it is always better to have a real example. Let's say that you have a PHP project that has the below structure 
(usually when people are using native PHP they don't use routes and hence the following structure).

<pre>├── assets
├── index.php
└── customers.php
</pre>

and all the JavaScript and CSS files are in the <code>assets</code> folder.

> Important Warning: The above structure is just an example, and we have over-simplified the example to make it easily
> understandable and configurable. We don't recommend to use the above (or the below) structure for real 
> projects since it is exposing the real PHP files to the end user. 

Copy the config files: `config.php`, `database.php`, `example.php`, `view.php` and the `libraries` folder at your 
project folder.

So now your folder will look like this:

<pre>
├── assets
├── libraries
│   ├── autoload.php
│   ├── composer
│   ├── grocery-crud
│   ├── laminas
│   ├── scoumbourdis
│   └── vlucas
├── index.php
├── config.php
├── database.php
├── example.php
├── view.php
└── customers.php
</pre>

Now also copy the assets to your project. For this specific example you will need to copy the assets folder from the 
`public` folder. So the final structure will look like this:

<pre>
├── assets
│   └── vendor
│       └── grocery-crud
│           ├── css
│           ├── icons
│           ├── js
│           └── static
├── libraries
│   ├── autoload.php
│   ├── composer
│   ├── grocery-crud
│   ├── laminas
│   ├── scoumbourdis
│   └── vlucas
├── index.php
├── config.php
├── database.php
├── example.php
├── view.php
└── customers.php
</pre>

Now the last changes that you need to do is to change the `assets_folder` at the `config.php` file to be 
`assets/vendor/grocery-crud`. So your new `config.php` file will look like this:

<pre><code class="language-php">&lt;?php
// config.php

return [
    // So far 34 languages including: Afrikaans, Arabic, Bengali, Bulgarian, Catalan, Chinese, Czech, Danish,
    // Dutch, English, French, German, Greek, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean,
    // Lithuanian, Mongolian, Norwegian, Persian, Polish, Portuguese, Brazilian Portuguese, Romanian,
    // Russian, Slovak, Spanish, Thai, Turkish, Ukrainian, Vietnamese
    'default_language'  => 'English',

    // This is the assets folder where all the JavaScript, CSS, images and font files are located
    'assets_folder' => '/assets/vendor/grocery-crud/',

    // The default per page when a user firstly see a list page
    'default_per_page'	=> '10',

    // Having some options at the list paging. This is the default one that all the websites are using.
    // Make sure that the number of grocery_crud_default_per_page variable is included to this array.
    'paging_options' => ['10', '25', '50', '100'],

    // The environment is important, so we can have specific configurations for specific environments
    'environment' => 'development',

    // The default theme that Grocery CRUD will use. Currently, you can choose between 'bootstrap-v4' and 'bootstrap-v5'
    'theme' => 'bootstrap-v5',

    'xss_clean' => false,

    // The character limiter at the datagrid columns, zero(0) value if you don't want any character
    // limitation to the column
    'column_character_limiter' => 50,

    // The allowed file types on upload. If the file extension doesn't exist in the array
    // it will throw an error and the upload will not be completed
    'upload_allowed_file_types' =>  [
        'gif', 'jpeg', 'jpg', 'png', 'svg', 'tiff', 'doc', 'docx',  'rtf', 'txt', 'odt', 'xls', 'xlsx', 'pdf',
        'ppt', 'pptx', 'pps', 'ppsx', 'mp3', 'm4a', 'ogg', 'wav', 'mp4', 'm4v', 'mov', 'wmv', 'flv', 'avi',
        'mpg', 'ogv', '3gp', '3g2', 'psd'
    ],

    'remove_file_on_delete' => false,

    // Show image preview - As we currently don't have thumbnails to show please keep in mind that the full
    // image will be loaded in the browser.
    'show_image_preview' => true,

    'open_in_modal' => true,

    'url_history' => true,

    // Configuration to publish action events (coming from Redux) with all the details that the action is having
    // This is useful to have a better control over the events that are being triggered in the application
    // However, please use with caution as this may leak some sensitive information to the application
    // For more read about security issues about XSS see wikipedia link
    // here https://en.wikipedia.org/wiki/Cross-site_scripting
    'publish_events' => false,

    // The button style that we have for the action buttons at the datagrid (list) page
    // Choose between 'icon', 'text', 'icon-text'
    'action_button_type' => 'icon-text',

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
];

</code></pre>

And the `example.php` looks like this:

<pre><code class="language-php">&lt?php
// This is the RAW file of example.php. We are going
// to change this file to fit our new project structure

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

As a last step, we are going to change just slightly the `example.php` to fit to our needs. 

Copy the file `example.php` to `films.php` and change the following lines:

<pre><code class="language-php">&lt;?php
// films.php

include("libraries/autoload.php"); // Changed this line here

use GroceryCrud\Core\GroceryCrud;

$database = include('database.php'); // Maybe those paths also need a change
$config = include('config.php'); // Maybe those paths also need a change

$crud = new GroceryCrud($config, $database);

$crud-&gt;setTable('films'); // And of course our specific CRUD
$crud-&gt;setSubject('Film', 'Films'); // And of course our specific CRUD

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

Now from the above code you will have a full working CRUD without the need to do anything else! 
You can now enjoy all the power of Grocery CRUD at the documentation (and you haven't used any terminal at all).

<h3>Troubleshooting</h3>

In case you have issues with the installation we have created a video tutorial on how to solve some common issues that
you may experience:

- Getting the "Ooooops, something went wrong! If you can see this message, this is probably a misconfiguration in Grocery
CRUD Enterprise!" message. I've created a video tutorial for Grocery CRUD Enterprise version 2 but it can be also applied
to version 3: <a target="_blank" href="https://www.youtube.com/watch?v=bCJTU6PWhYs">Troubleshooting Grocery CRUD Enteprise part 1</a>

<br/>
