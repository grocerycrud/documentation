---
id: grocery-crud-enterprise-laravel-8-installation
title: Install Grocery CRUD Enterprise in Laravel 8
description: Step-by-step installation guidance of Grocery CRUD Enterprise in Laravel 8 framework.
permalink: docs/grocery-crud-laravel-8-installation
previous: api-and-functions-list
next: basic-example
---

# Laravel 8 installation

**Table of contents:**

1. [Download Grocery CRUD zip file](#download-grocery-crud-zip-file)
2. [Install Grocery CRUD Enterprise via composer](#install-grocery-crud-enterprise-via-composer)
3. [Copy assets folder](#copy-assets-folder)
4. [Configuration file](#configuration-file)
5. [Routes Configuration](#routes-configuration)
6. [Preparing our Resources](#preparing-our-resources)
7. [See it working 👀](#see-it-working)
8. [Let's refactor our Controller](#let's-refactor-our-controller)
9. [Celebrate 🎉](#celebrate)

This is a full tutorial of a suggested way to install Grocery CRUD Enterprise
to your already existing project with Laravel version 8.

## Download Grocery CRUD zip file

From the email that you've received or from the user's page (you will get instructions at the email of how to access user's page) download the zip file that say's "With composer".

Your file will look something like this: <code>grocery-crud-enterprise-v2.9.0.zip</code>. Now at your root directory create a new directory with name <code>artifacts</code> and copy the zip file there <strong>without</strong> unziping it. The final file structure will look something like this:
<pre>├── app
<strong>├── artifacts
│   └── grocery-crud-enterprise-v2.9.0.zip</strong>
├── artisan
├── bootstrap
├── composer.json
├── composer.lock
├── config
├── database
├──.env
├──.gitattributes
├──.gitignore
├── package.json
├── phpunit.xml
├── public
├── readme.md
├── resources
├── routes
├── server.php
├── storage
├── tests
├── vendor
└── webpack.mix.js
</pre>

## Install Grocery CRUD Enterprise via composer

Add the "repositories" name with the below code:

<pre><code>"repositories": [
        {
            "type": "artifact",
            "url": "artifacts/"
        }
    ],</code></pre>

and add the <code>"grocerycrud/enterprise": "2.*.*"</code> to the "require" section.

So more specifically this is how the changes will look like:
<pre><code>"license": "MIT",
"repositories": [
    {
        "type": "artifact",
        "url": "artifacts/"
    }
],
"require": {
    "php": "^7.3|^8.0",
    "fideloper/proxy": "^4.4",
    "fruitcake/laravel-cors": "^2.0",
    "guzzlehttp/guzzle": "^7.0.1",
    "laravel/framework": "^8.12",
    "laravel/tinker": "^2.5",
    "grocerycrud/enterprise": "2.*.*"
},</code></pre>
So your <code>composer.json</code> will look something like this:

<pre><code>{
    "name": "laravel/laravel",
    "type": "project",
    "description": "The Laravel Framework.",
    "keywords": [
        "framework",
        "laravel"
    ],
    "license": "MIT",
    "repositories": [
        {
            "type": "artifact",
            "url": "artifacts/"
        }
    ],
    "require": {
        "php": "^7.3|^8.0",
        "fideloper/proxy": "^4.4",
        "fruitcake/laravel-cors": "^2.0",
        "guzzlehttp/guzzle": "^7.0.1",
        "laravel/framework": "^8.12",
        "laravel/tinker": "^2.5",
        "grocerycrud/enterprise": "2.*.*"
    },
    "require-dev": {
        "facade/ignition": "^2.5",
        "fakerphp/faker": "^1.9.1",
        "laravel/sail": "^1.0.1",
        "mockery/mockery": "^1.4.2",
        "nunomaduro/collision": "^5.0",
        "phpunit/phpunit": "^9.3.3"
    },
    "config": {
        "optimize-autoloader": true,
        "preferred-install": "dist",
        "sort-packages": true
    },
    "extra": {
        "laravel": {
            "dont-discover": []
        }
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
    "minimum-stability": "dev",
    "prefer-stable": true,
    "scripts": {
        "post-autoload-dump": [
            "Illuminate\\Foundation\\ComposerScripts::postAutoloadDump",
            "@php artisan package:discover --ansi"
        ],
        "post-root-package-install": [
            "@php -r \"file_exists('.env') || copy('.env.example', '.env');\""
        ],
        "post-create-project-cmd": [
            "@php artisan key:generate --ansi"
        ]
    }
}
</code></pre>

Update composer in order to get the library of Grocery CRUD Enterprise at the <code>vendor</code> folder
Now go to your root folder with your terminal and simply type:

<pre>composer update</pre>

You will be able to see many updates such us zend db but you will also see this:

<pre><code> - Installing grocerycrud/enterprise (2.9.0)</code></pre>

Now Grocery CRUD Enterprise is available through composer so you could see the below folder structure at your <code>vendor</code> folder:

<pre>vendor
├── ...
...
├── fzaninotto
├── grocerycrud
│   └── enterprise
│       ├── change-log.txt
│       ├── composer.json
│       ├── examples
│       ├── LICENCE.md
│       ├── public
│       └── src
├── hamcrest
...</pre>

## Copy assets folder

Now that we have available the package through vendor, we will also need to copy the public folders to our project. More specifically, navigate to: <code>vendor/grocerycrud/enterprise/public</code> and you will see the folder with name <code>grocery-crud</code>. Now go to your public folder and create a new folder with name <code>assets</code>. Then copy the folder <code>grocery-crud</code> to the <code>assets</code> folder. The final folder structure will look something like this:

<pre>├── app
├── artifacts
├── artisan
├── bootstrap
├── composer.json
├── composer.lock
├── config
├── database
├── package.json
├── phpunit.xml
├── public
<strong>    ├── assets
    │   └── grocery-crud
    │       ├── css
    │       ├── fonts
    │       ├── images
    │       ├── index.html
    │       └── js</strong>
    ├── css
    │   └── app.css
    ├── favicon.ico
    ├── index.php
    ├── js
    │   └── app.js
    ├── robots.txt
    └── web.config
├── readme.md
├── resources
├── routes
├── server.php
├── storage
├── tests
├── vendor
└── webpack.mix.js</pre>

## Configuration file

Go to your project's <code>config</code> folder and create a file with name <code>grocerycrud.php</code> that will include the below code:

<pre><code class="language-php">&lt;?php
// config/grocerycrud.php

return [
    // So far 34 languages including: Afrikaans, Arabic, Bengali, Bulgarian, Catalan, Chinese, Czech, Danish,
    // Dutch, English, French, German, Greek, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean,
    // Lithuanian, Mongolian, Norwegian, Persian, Polish, Portuguese, Brazilian Portuguese, Romanian,
    // Russian, Slovak, Spanish, Thai, Turkish, Ukrainian, Vietnamese
    'default_language'	=> 'English',

    // This is the assets folder where all the JavaScript, CSS, images and font files are located
    'assets_folder' => env('APP_URL') . '/assets/grocery-crud/',

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

<strong>Important Notice:</strong> Make sure that you have configured the correct website path at the file <code>.env</code>. More specifically change the below code:

<pre><code>APP_URL=http://localhost</code></pre>

to your original project path. For example:

<pre><code>APP_URL=http://local.grocerycrud.com</code></pre>

## Routes Configuration
Now we will need to create our routes to point to our controller. Let's start by configuring routes! Go to `routes/web.php` and add the below lines of code:

<pre><code class="language-php">&lt;?php
// routes/web.php
use App\Http\Controllers\AdminController; // <-- don't forget the use

Route::get('/', function () {
    return view('welcome');
});

// New code
Route::get('/admin/customers-management', [AdminController::class, 'customers']);
Route::get('/admin/customers-management/{operation}', [AdminController::class, 'customers']);
Route::get('/admin/customers-management/{operation}/{id}', [AdminController::class, 'customers']);
Route::post('/admin/customers-management', [AdminController::class, 'customers']);
Route::post('/admin/customers-management/{operation}', [AdminController::class, 'customers']);
Route::post('/admin/customers-management/{operation}/{id}', [AdminController::class, 'customers']);</code></pre>

As you can see at the above code, we are simply saying that for the URL `/admin/customers-management` for `POST` or `GET` method then load the Controller `AdminController` and the function `customers`.
For now, I am just adding 5 lines of code for the simplicity of the installation. However you can always create a specific function that can do that for you so you will not need to copy-paste 5 lines of code all the time.


Now that we've created our routes let's create our empty for now Controller. In order to do that go to: <code>app/Http/Controllers/</code> and create a new file with name <code>AdminController.php</code>. 
There add a simple controller like the one below:

<pre><code class="language-php">&lt;?php
// app/Http/Controllers/AdminController.php
namespace App\Http\Controllers;

use GroceryCrud\Core\GroceryCrud;

class AdminController extends Controller
{
    /**
     * Grocery CRUD Example
     *
     * @return \Illuminate\View\View
     */
    public function customers()
    {
        die("Hello World!");
    }
}
</code></pre>

As you can also see from the above code, we did also add the <code>use GroceryCrud\Core\GroceryCrud;</code> in order to make sure that Grocery CRUD Enterprise can load. In case this line doesn't work for you, please make sure that you follow the above steps in order to install Grocery CRUD Enterprise with composer first.

Now our datagrid has just a response "Hello World!" So if you go to your website and navigate to: `example.com/admin/customers-management` you should see the phrase "Hello World!". If you see this message that means that your routes are configured correctly and that we can load Grocery CRUD Enterprise 🎉. 

You've already did great! This was the most difficult part. Take a deep breath and let's continue as we have few more steps to cover!

## Preparing our Resources

In Grocery CRUD Enterprise we are using the function render() to render 3 main things:
<ul>
	<li>The HTML output string</li>
	<li>The CSS files</li>
	<li>The JavaScript files</li>
</ul>

So it is important to have a template that can load all the above. Usually in our project we've already have a template to load the CSS and JS files but in case we don't, we can create a new template view like the below. Go to: <code>resources/views/</code> and create a new file with name: <code>default_template.blade.php</code>. Then copy the below code:

<pre><code class="language-php">&lt;!DOCTYPE html&gt;
&lt;html lang="en"&gt;
&lt;head&gt;
	&lt;meta charset="UTF-8"&gt;
	&lt;title&gt;Example&lt;/title&gt;

	&lt;meta name="csrf-token" content="{{ csrf_token() }}"&gt;

	@foreach ($css_files as $css_file)
    	&lt;link rel="stylesheet" href="{{ $css_file }}"&gt;
	@endforeach
&lt;/head&gt;
&lt;body&gt;
	&lt;div style="padding: 20px"&gt;
		{!! $output !!}
	&lt;/div&gt;

	@foreach ($js_files as $js_file)
    	&lt;script src="{{ $js_file }}"&gt;&lt;/script&gt;
	@endforeach
	&lt;script&gt;
		if (typeof $ !== 'undefined') {
			$(document).ready(function () {
				$.ajaxSetup({
				    headers: {
				        'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content')
				    }
				});
			});
		}
	&lt;/script&gt;
&lt;/body&gt;
&lt;/html&gt;</code></pre>

As you may also notice (and this is the second most common mistake for Laravel installations) we are also adding the CSRF token as a meta tag on the header:

<pre><code class="language-php">&lt;meta name="csrf-token" content="{{ csrf_token() }}"&gt;</code></pre>

And we are are having the CSRF token as a default header with the below code:

<pre><code class="language-javascript">$(document).ready(function () {
    $.ajaxSetup({
        headers: {
            'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content')
        }
    });
});</code></pre>

As this will be a generic template we are also making sure that we are checking if jQuery exists with the below code:

<pre><code class="language-javascript">if (typeof $ !== 'undefined') {</code></pre>

## See it working!

Now finally after 6 steps it is time to see Grocery CRUD Enterprise working on your screen 👀! In order to do that your final controller will look like below:

<pre><code class="language-php">&lt;?php
// app/Http/Controllers/AdminController.php
namespace App\Http\Controllers;

use Illuminate\Http\Request;
use GroceryCrud\Core\GroceryCrud;

class AdminController extends Controller
{

    /**
     * Grocery CRUD Example
     *
     * @return \Illuminate\Http\Response|\Illuminate\View\View
     */
    public function customers()
    {
        $database = $this->_getDatabaseConnection();
        $config = config('grocerycrud');

        $crud = new GroceryCrud($config, $database);

        $crud->setTable('customers');
        $crud->setSubject('Customer', 'Customers');

        $output = $crud->render();

        if ($output->isJSONResponse) {
            return response($output->output, 200)
                ->header('Content-Type', 'application/json')
                ->header('charset', 'utf-8');
        }

        $css_files = $output->css_files;
        $js_files = $output->js_files;
        $output = $output->output;

        return view('default_template', [
            'output' => $output,
            'css_files' => $css_files,
            'js_files' => $js_files
        ]);
    }

    private function _getDatabaseConnection() {

        return [
            'adapter' => [
                'driver' => 'Pdo_Mysql',
                'database' => env('DB_DATABASE'),
                'username' => env('DB_USERNAME'),
                'password' => env('DB_PASSWORD'),
                'charset' => 'utf8'
            ]
        ];
    }

}</code></pre>

Let's explain a little bit what we did at the controller. Grocery CRUD Enterprise needs two kind of configurations:

<ul>
	<li>The database connection</li>
	<li>The Grocery CRUD Enterprise configurations</li>
</ul>

The database configuration can be taken dynamically from the `.env` file

In our case, our default database is MySQL and that's why we have as hardcoded the value of the Zend driver as <code>Pdo_Mysql</code>.
So the final result of the configuration is:

<pre><code class="language-php">private function _getDatabaseConnection() {

        return [
            'adapter' => [
                'driver' => 'Pdo_Mysql',
                'database' => env('DB_DATABASE'),
                'username' => env('DB_USERNAME'),
                'password' => env('DB_PASSWORD'),
                'charset' => 'utf8'
            ]
        ];
    }</code></pre>

Please have in mind that for different databases you will need to change the adapter driver. For example you can use the following drivers:

<ul>
	<li><code>Pdo_Pgsql</code> for PostgreSQL</li>
	<li><code>Pdo_Sqlite</code> for  SQLite</li>
	<li>For Microsoft SQL server you should follow the <a href="https://www.grocerycrud.com/enterprise/examples-3/database-connection-mssql">Connection with MSSQL guidelines</a></li>
</ul>

And you can also see all the available database connections from <a href="https://framework.zend.com/manual/2.4/en/modules/zend.db.adapter.html">Zend Db adapter</a>.

The very next configuration is the configuration that we did describe earlier about grocery CRUD:

<pre><code class="language-php">$config = config('grocerycrud');</code></pre>

Now let's explain quickly what the below code is doing:

<pre><code class="language-php">if ($output->isJSONResponse) {
    return response($output->output, 200)
          ->header('Content-Type', 'application/json')
          ->header('charset', 'utf-8');
}
</code></pre>

At the above code, we are checking if the response is JSON and if not we are calling our main template view. In case the response is JSON then we are simply returning the JSON response that it is already formatted as a string by Grocery CRUD Enterprise with some JSON headers.

## Let's refactor our Controller

With Grocery CRUD Enterprise, we've notice that we are repeating the same code again and again. That's why it is strongly recommended to move the initial call with the configurations and the final output code into two separate functions. For example the above controller can be refactored with the below one:

<pre><code class="language-php">&lt;?php
// app/Http/Controllers/AdminController.php
namespace App\Http\Controllers;

use GroceryCrud\Core\GroceryCrud;

class AdminController extends Controller
{

    /**
     * Grocery CRUD Example
     *
     * @return \Illuminate\Http\Response|\Illuminate\View\View
     */
    public function customers()
    {
        $crud = $this->_getGroceryCrudEnterprise();

        $crud->setTable('customers');
        $crud->setSubject('Customer', 'Customers');

        $output = $crud->render();

        return $this->_showOutput($output);
    }

    /**
     * Get everything we need in order to load Grocery CRUD
     *
     * @return GroceryCrud
     * @throws \GroceryCrud\Core\Exceptions\Exception
     */
    private function _getGroceryCrudEnterprise() {
        $database = $this->_getDatabaseConnection();
        $config = config('grocerycrud');

        $crud = new GroceryCrud($config, $database);

        return $crud;
    }


    /**
     * Grocery CRUD Output
     *
     * @return \Illuminate\Http\Response|\Illuminate\View\View
     */
    private function _showOutput($output) {
        if ($output->isJSONResponse) {
            return response($output->output, 200)
                ->header('Content-Type', 'application/json')
                ->header('charset', 'utf-8');
        }

        $css_files = $output->css_files;
        $js_files = $output->js_files;
        $output = $output->output;

        return view('default_template', [
            'output' => $output,
            'css_files' => $css_files,
            'js_files' => $js_files
        ]);
    }

    /**
     * Get database credentials as a Zend Db Adapter configuration
     * @return array[]
     */
    private function _getDatabaseConnection() {

        return [
            'adapter' => [
                'driver' => 'Pdo_Mysql',
                'database' => env('DB_DATABASE'),
                'username' => env('DB_USERNAME'),
                'password' => env('DB_PASSWORD'),
                'charset' => 'utf8'
            ]
        ];
    }

}</code></pre>

So as you can also see our current implementation of customers is only the below lines:

<pre><code class="language-php">public function customers()
{
    $crud = $this->_getGroceryCrudEnterprise();

    $crud->setTable('customers');
    $crud->setSubject('Customer', 'Customers');

    $output = $crud->render();

    return $this->_showOutput($output);
}</code></pre>

And of course we can only now copy those few lines of code in case we need to create another CRUD.

For example:
<pre><code class="language-php">public function offices()
{
    $crud = $this->_getGroceryCrudEnterprise();

    $crud->setTable('offices');
    $crud->setSubject('Office', 'Offices');

    $output = $crud->render();

    return $this->_showOutput($output);
}</code></pre>


## Celebrate

Don't forget to celebrate your installation 🎉. Take a break and drink some coffee ☕ tea or water, you deserve it! 

After that short break enjoy the power of Grocery CRUD Enterprise at your project! From now one with few lines of PHP you can get a full working CRUD for your project 🤗

In case you still have issues with the installation also consider checking the video tutorial: <a target="_blank" href="https://www.youtube.com/watch?v=bCJTU6PWhYs">Troubleshooting Grocery CRUD Enteprise part 1</a>.

<blockquote><strong>Notice:</strong> Grocery CRUD Enterprise is a framework agnostic library. That simply means that it doesn't matter which framework you are using and it doesn't matter which architecture you are using. It can work in any PHP platform! This tutorial is taking some architecture decisions basically for you! If you need to have the full freedom of what structure to choose we are suggesting to see the full installation guide <a href="/docs/grocery-crud-enterprise-installation">here</a>.</blockquote>

