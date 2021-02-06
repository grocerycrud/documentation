---
id: grocery-crud-enterprise-codeigniter-4
title: Codeigniter 4 Installation
permalink: docs/grocery-crud-enterprise-codeigniter-4
previous:
next:
---

# Codeigniter 4 Installation

This is a full tutorial of a suggested way to install Grocery CRUD Enterprise to your already existing project with Codeigniter 4 framework. For some people this tutorial may require too many steps. However have in mind that if you follow the instructions step by step you will have a successful installation as this page is actively updated.

<strong>Step 1.</strong> From the email that you've received or from the user's page (you will get instructions at the email of how to access user's page) download the file that say's "Without composer". Once you've downloaded it, unzip it!
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
<strong>Step 2.</strong> rename the folder <code>libraries</code> to <code>GroceryCrudEnterprise</code> and move it to your project at the following path <code>app/Libraries/GroceryCrudEnterprise</code> with this structure we simply follow the "Codeigniter way" of adding libraries.

<strong>Notice:</strong> Have in mind here that although the folder of Grocery CRUD Enterprise has the name <code>libraries</code> (with lowercase) that has almost nothing to do with the Codeigniter folder <code>Libraries</code> (with capital L). This is a very common confusion that people may have during the installation. As per step 2. you will basically rename the folder <code>libraries</code> to <code>GroceryCrudEnterprise</code> to also avoid this confusion.

<strong>Step 3.</strong> go to the folder <code>public</code> and copy the folder <code>grocery-crud</code> to your <code>public</code> folder of your Codeigniter project.

<strong>Step4.</strong> We did currently installed Grocery CRUD Enterprise in our project and we need to create our configuration files in order to make it work! Go to <code>app/Config</code> and create a file with name <code>GroceryCrudEnterprise.php</code>. As the configuration is different than other frameworks we will use a custom one that will look like this (just copy really the code below)

<pre><code class="language-php">&lt;?php namespace Config;

use CodeIgniter\Config\BaseConfig;

class GroceryCrudEnterprise extends BaseConfig
{
    public function getDefaultConfig() {
        helper('url');

        return [
            // So far 34 languages including: Afrikaans, Arabic, Bengali, Bulgarian, Catalan, Chinese, Czech, Danish,
            // Dutch, English, French, German, Greek, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean,
            // Lithuanian, Mongolian, Norwegian, Persian, Polish, Portuguese, Brazilian Portuguese, Romanian,
            // Russian, Slovak, Spanish, Thai, Turkish, Ukrainian, Vietnamese
            'default_language'	=> 'English',

            // This is the assets folder where all the JavaScript, CSS, images and font files are located
            'assets_folder' => base_url() . '/grocery-crud/',

            // There are only three choices: "uk-date" (dd/mm/yyyy), "us-date" (mm/dd/yyyy) or "sql-date" (yyyy-mm-dd)
            'date_format' => 'uk-date',

            // The default per page when a user firstly see a list page
            'default_per_page'	=> 10,

            // Having some options at the list paging. This is the default one that all the websites are using.
            // Make sure that the number of grocery_crud_default_per_page variable is included to this array.
            'paging_options' => ['10', '25', '50', '100'],

            // The environment is important so we can have specific configurations for specific environments
            'environment' => 'development',

            // The default skin that Grocery CRUD will use. Currently choose between 'bootstrap-v3' and 'bootstrap-v4'
            'skin' => 'bootstrap-v4',

            // This is basically in order to have a php cache. Be aware that in case you disable the php cache
            // things will get too slow
            'backend_cache' => false,

            'xss_clean' => false,

            // The character limiter at the datagrid columns, zero(0) value if you don't want any character
            // limitation to the column
            'column_character_limiter' => 50,

            // You can choose between 'minimal' or 'full'
            'text_editor_type' => 'full',

            // If open_in_modal is true then all the form operations (e.g. add, edit, clone... e.t.c.) will
            // open within a modal and we will have the datagrid on the background.
            // In case you would like however to have a standalone page for all the form operations change this to false.
            'open_in_modal' => true,

            // This is the hash symbol (#) that we have at the URL in order to have tha basic operations in the URL so you
            // can navigate back to the URL that you were. For example, when you click at edit form for the id 46, the
            // URL will also change to #/edit/46 so you can also share the link.
            // In case you would like to switch this functionality to off change this to false.
            'hash_in_url' => true,

            // The maximum number of buttons that we would like to have for the actions buttons.
            // If the number of buttons exceeds this number then the last button on the right
            // is going to change into a "More" dropdown button.
            // If the maximum number is 1 then as we only have one button as a dropdown list the translation
            // is "Actions" rather than "More"
            'max_action_buttons' => [
                'mobile' => 1,
                'desktop' => 2
            ],

            // For more read http://framework.zend.com/manual/current/en/modules/zend.cache.storage.adapter.html
            // If you are not sure about how to use it, you can just change the ttl value (time to live) and
            // the file path of the cache
            'cache' => [
                'adapter' => [
                    'name'    => 'filesystem',
                    'options' => [
                        'namespace' => 'gcrud',
                        'ttl' => 3600 * 24 * 30 * 6,
                        'cache_dir' => realpath(__DIR__ . '/Cache/')
                    ],
                ],
                'plugins' => [
                    'exception_handler' => ['throw_exceptions' => false],
                ],
            ],
        ];
    }
}</code></pre>
<div id="final-structure">In order to confirm that so far you did copy the correct files, your folder structure will look something like this:</div>
<pre>.
├── LICENSE
├── README.md
├── _support
├── app
│   ├── Common.php
│   ├── Config
│   │   ├── App.php
│   │   ├── Autoload.php
│   │   ├── ...
│   │   ├── Format.php
│   │   ├── <strong>GroceryCrudEnterprise.php</strong>
│   │   ├── Honeypot.php
│   │   ├── ...
│   │   └── View.php
│   ├── Controllers
│   │   ├── BaseController.php
│   │   └── Home.php
│   ├── Database
│   │   ├── Migrations
│   │   └── Seeds
│   ├── Filters
│   ├── Helpers
│   ├── Language
│   ├── Libraries
│   │   ├── <strong>GroceryCrudEnterprise</strong>
│   │   │   ├── <strong>autoload.php</strong>
│   │   │   ├── <strong>bin</strong>
│   │   │   ├── <strong>composer</strong>
│   │   │   ├── ...
│   │   │   ├── <strong>phpunit</strong>
│   │   │   ├── <strong>symfony</strong>
│   │   │   └── <strong>zendframework</strong>
│   ├── Models
│   ├── ThirdParty
│   ├── Views
│   │   ├── errors
│   │   └── welcome_message.php
│   └── index.html
├── composer.json
├── contributing.md
├── env
├── license.txt
├── phpunit.xml.dist
├── public
│   ├── <strong>grocery-crud</strong>
│   │   ├── <strong>css</strong>
│   │   ├── <strong>fonts</strong>
│   │   ├── <strong>images</strong>
│   │   └── <strong>js</strong>
│   ├── favicon.ico
│   ├── index.php
│   └── robots.txt
├── spark
├── system
├── tests
└── writable</pre>
<strong>Step5.</strong> Now you are ready basically to use grocery CRUD Enterprise. You only need some small modifications. The easiest way to create two private methods to your controller that it will look like this:
<pre><code class="language-php">&lt;?php namespace App\Controllers;

// Add those two lines at the beginning of your controller
include(APPPATH . 'libraries/GroceryCrudEnterprise/autoload.php');
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

include(APPPATH . 'Libraries/GroceryCrudEnterprise/autoload.php');
use GroceryCrud\Core\GroceryCrud;

class Example extends BaseController
{
    public function index() 
    {
        $output = (object)[
            'css_files' => [],
            'js_files' => [],
            'output' => ''
        ];

        return $this->_example_output($output);
    }
    public function customers()
    {
        $crud = $this->_getGroceryCrudEnterprise();

        $crud->setCsrfTokenName(csrf_token());
        $crud->setCsrfTokenValue(csrf_hash());

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
        return $groceryCrud;
    }
}</code></pre>

Go to <code>app/Views</code> and create a file with name <code>example.php</code> and it is the exact same view that we were using as an example at Community edition. More specifically the view <em>example.php</em> will contain the below code:

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

If you would like you can also check the above steps into a video tutorial:

<iframe loading="lazy" width="560" height="315" src="https://www.youtube.com/embed/XIoMR38ANnE" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

<h2 id="troubleshooting">Troubleshooting</h2>
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

For example in our case we've forgot to change the default database credentials to our ones. So by going to <code>.env</code> file and uncommenting this lines:
<pre><code class="language-php"># database.default.hostname = localhost
# database.default.database = ci4
# database.default.username = root
# database.default.password = root
# database.default.DBDriver = MySQLi</code></pre>
to your specific database credentials everything is just working smoothly.

<strong>Notice:</strong> Grocery CRUD Enterprise is a framework agnostic library. That simply means that it doesn't matter which framework you are using and it doesn't matter the architecture you are using. This tutorial is taking some architecture decisions basically for you. If you need to have the full freedom of what structure to choose we are suggesting to see the full installation guide <a href="/docs/grocery-crud-enterprise-installation">here</a>.