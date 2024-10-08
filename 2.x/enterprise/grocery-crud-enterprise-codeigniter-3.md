---
id: grocery-crud-enterprise-codeigniter-3
title: Codeigniter 3 Installation
description: Step by step tutorial. Install Grocery CRUD Enterprise on Codeigniter version 3.
canonical: v2.x/docs/grocery-crud-enterprise-codeigniter-3
previous: api-and-functions-list
next: basic-example
---

# Codeigniter 3 Installation

This is a full tutorial of a suggested way to install Grocery CRUD Enterprise to your already existing project with Codeigniter framework.

First of all, the most common usage of Grocery CRUD Enterprise is an upgrade from the open-source edition. That simply means the project is built with Codeigniter framework and it is very possible to already have installed Grocery CRUD Free edition. So at the below steps we are trying to have an installation guide without causing any conflicts to the already existing community version (so you can use both if you like).

<strong>Step 1.</strong> From the email that you've received or from the user's page (you will get instructions at the email of how to access user's page) download the file that say's "Without composer". Once you've downloaded it, unzip it!
The folder structure that you will get is the following:
<pre>├── examples
│   ├── config.php
│   ├── database.php
│   ├── example.php
│   └── view.php
├── libraries
│   ├── autoload.php
│   ├── bin
│   ├── composer
│   ├── ...
│   ├── phpunit
│   ├── symfony
│   └── zendframework
└── public
    └── grocery-crud
        ├── css
        ├── fonts
        ├── images
        └── js</pre>
<strong>Step 2.</strong> rename the folder <code>libraries</code> to <code>GroceryCrudEnterprise</code> and move it to your project at the following path <em>application/libraries/GroceryCrudEnterprise</em> with this structure we simply follow the "Codeigniter way" of adding libraries.
<strong>Step 3.</strong> go to the folder <code>public</code> and copy the folder <code>grocery-crud</code> to your <code>assets</code> folder of your Codeigniter project. If you don't have one, then it will be good to create one!

<strong>Step4.</strong> We did currently installed Grocery CRUD Enterprise in our project and we need to create our configuration files in order to make it work. Rename the configuration files from examples: <code>config.php</code> to <code>gcrud-enterprise.php</code> and copy it to <em>application/config</em> folder at your project. Don't forget to add at your config file the path for the folder at the file <code>gcrud-enterprise.php</code> . In your case it will be:
<pre><code class="language-php">'assets_folder' =&gt; base_url() . 'assets/grocery-crud/',</code></pre>
<div id="final-structure">So far your Codeigniter project should look like this:</div>
<pre>├── application
│   ├── cache
│   ├── config
│   │   ├── autoload.php
│   │   ├── ...
│   │   ├── gcrud-enterprise.php
│   │   ├── ...
│   │   └── user_agents.php
│   ├── controllers
│   ├── core
│   ├── errors
│   ├── helpers
│   ├── hooks
│   ├── language
│   ├── libraries
│   │   ├── GroceryCrudEnterprise
│   │   │   ├── autoload.php
│   │   │   ├── bin
│   │   │   ├── composer
│   │   │   ├── ...
│   │   │   ├── phpunit
│   │   │   ├── symfony
│   │   │   └── zendframework
│   │   ├── ...
│   │   ├── ...
│   │   └── index.html
│   ├── logs
│   ├── models
│   ├── private
│   ├── third_party
│   └── views
├── assets
│   ├── ...
│   ├── grocery-crud
│   │   ├── css
│   │   ├── fonts
│   │   ├── images
│   │   └── js
│   └── ...
└── system</pre>
and your file application/config/gcrud-enteprise.php will look something like this:

<pre><code class="language-php">&lt;?php
return [
    // So far 34 languages including: Afrikaans, Arabic, Bengali, Bulgarian, Catalan, Chinese, Czech, Danish,
    // Dutch, English, French, German, Greek, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean,
    // Lithuanian, Mongolian, Norwegian, Persian, Polish, Portuguese, Brazilian Portuguese, Romanian,
    // Russian, Slovak, Spanish, Thai, Turkish, Ukrainian, Vietnamese
    'default_language'	=> 'English',

    // This is the assets folder where all the JavaScript, CSS, images and font files are located
    'assets_folder' => base_url() . 'assets/grocery-crud/',

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

<div class="tip">

<strong>Important Notice:</strong> The most common mistake of the installation of grocery CRUD Enteprise is when the assets_folder has a wrong path. If you did follow all the steps and you see that your webpage looks like that:

<img style="border: 1px solid #DDD;" src="/assets/uploads/general/wrong-codeigniter-installation.png" alt="wrong-codeigniter-installation" />

then make sure that you have configured your application/config/config.php file at $config['base_url']. For example if your project URL looks like this:
<code>http://localhost/my-test-project/index.php</code> then your base_url should look like this:
<code>$config['base_url'] = 'http://localhost/my-test-project/';</code>

</div>
<strong>Step5.</strong> Now you are ready basically to use grocery CRUD Enterprise. You only need some small modifications. The easiest way to create two private methods to your controller that it will look like this:
<pre><code class="language-php">&lt;?php if ( ! defined('BASEPATH')) exit('No direct script access allowed');

// Add those two lines at the beginning of your controller
include(APPPATH . 'libraries/GroceryCrudEnterprise/autoload.php');
use GroceryCrud\Core\GroceryCrud;

...

private function _getDbData() {
$db = [];
include(APPPATH . 'config/database.php');
return [
'adapter' =&gt; [
'driver' =&gt; 'Pdo_Mysql',
'host'     =&gt; $db['default']['hostname'],
'database' =&gt; $db['default']['database'],
'username' =&gt; $db['default']['username'],
'password' =&gt; $db['default']['password'],
'charset' =&gt; 'utf8'
]
];
}
private function _getGroceryCrudEnterprise($bootstrap = true, $jquery = true) {
$db = $this-&gt;_getDbData();
$config = include(APPPATH . 'config/gcrud-enterprise.php');
$groceryCrud = new GroceryCrud($config, $db);
return $groceryCrud;
}</code></pre>
And now when you want to use groceryCRUD enterprise you will simply do this:
<pre><code class="language-php">// Your function at your controller
public function demo_set_model()
{
    $crud = $this-&gt;_getGroceryCrudEnterprise();
    $crud-&gt;setTable('customers');
    $crud-&gt;setSubject('Customer', 'Customers');
    $crud-&gt;columns(['customerName','country','state','addressLine1']);
    $output = $crud-&gt;render();
    $this-&gt;_example_output($output);
}

function _example_output($output = null) {
    if (isset($output-&gt;isJSONResponse) &amp;&amp; $output-&gt;isJSONResponse) {
                header('Content-Type: application/json; charset=utf-8');
                echo $output-&gt;output;
                exit;
    }

    $this-&gt;load-&gt;view('example.php',$output);    
}
</code></pre>
The example.php is located at: application/views/example.php and it is the exact same view that we were using as an example at Free edition. More specifically the view <em>example.php</em> contains the below code:
<pre><code class="language-php">&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
 &lt;meta charset="utf-8" /&gt;
 
&lt;?php 
foreach($css_files as $file): ?&gt;
 &lt;link type="text/css" rel="stylesheet" href="&lt;?php echo $file; ?&gt;" /&gt;
 
&lt;?php endforeach; ?&gt;
&lt;?php foreach($js_files as $file): ?&gt;
 
 &lt;script src="&lt;?php echo $file; ?&gt;"&gt;&lt;/script&gt;
&lt;?php endforeach; ?&gt;
 
&lt;style type='text/css'&gt;
body
{
 font-family: Arial;
 font-size: 14px;
}
a {
 font-size: 14px;
}
&lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;!-- Beginning header --&gt;
 &lt;div&gt;
 &lt;a href='&lt;?php echo site_url('examples/offices_management')?&gt;'&gt;Offices&lt;/a&gt; | 
 &lt;a href='&lt;?php echo site_url('examples/employees_management')?&gt;'&gt;Employees&lt;/a&gt; |
 &lt;a href='&lt;?php echo site_url('examples/customers_management')?&gt;'&gt;Customers&lt;/a&gt; |
 &lt;a href='&lt;?php echo site_url('examples/orders_management')?&gt;'&gt;Orders&lt;/a&gt; |
 &lt;a href='&lt;?php echo site_url('examples/products_management')?&gt;'&gt;Products&lt;/a&gt; | 
 &lt;a href='&lt;?php echo site_url('examples/film_management')?&gt;'&gt;Films&lt;/a&gt;
 
 &lt;/div&gt;
&lt;!-- End of header--&gt;
 &lt;div style='height:20px;'&gt;&lt;/div&gt; 
 &lt;div&gt;
&lt;?php echo $output; ?&gt;
 
 &lt;/div&gt;
&lt;!-- Beginning footer --&gt;
&lt;div&gt;Footer&lt;/div&gt;
&lt;!-- End of Footer --&gt;
&lt;/body&gt;
&lt;/html&gt;
</code></pre>

<strong>Notice:</strong> Grocery CRUD Enterprise is a framework agnostic library. That simply means that it doesn't matter which framework you are using and it doesn't matter the architecture you are using. This tutorial is taking some architecture decisions basically for you. If you need to have the full freedom of what structure to choose we are suggesting to see the full installation guide <a href="/docs/grocery-crud-enterprise-installation">here</a>.

<strong>Update:</strong> If you would like to see a quick video tutorial of how to install Grocery CRUD Enterprise with Codeigniter from scratch you can go straight away and see the video here: <a href="https://www.youtube.com/watch?v=FC54Db7LOG0">Grocery CRUD Enterprise - Installation for Codeigniter</a>

<strong>Latest Update:</strong> As I had many requests to basically have a full example with Codeigniter into one place, you can find everything that I've just describe above with the <strong>latest </strong> Codeigniter version and with the latest Grocery CRUD Enterprise at this link: <a href="https://www.grocerycrud.com/users/enterprise_latest_version">https://www.grocerycrud.com/users/enterprise_latest_version</a> by downloading <code>with Codeigniter X.X.X</code>. Although it is not required, it is fully suggested to read this document first as it useful for you to understand better the file structure.