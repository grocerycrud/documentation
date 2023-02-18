---
id: grocery-crud-enterprise-laravel-10-installation
title: Install Grocery CRUD Enterprise in Laravel 10
description: Step-by-step installation guidance of Grocery CRUD Enterprise in Laravel 10 framework.
canonical: docs/grocery-crud-enterprise-laravel-8-installation
previous: api-and-functions-list
next: basic-example
---

# Laravel 10 installation

**Table of contents:**

1. [Prerequisites](#prerequisites)
2. [Download Grocery CRUD zip file](#download-grocery-crud-zip-file)
3. [Install Grocery CRUD Enterprise via composer](#install-grocery-crud-enterprise-via-composer)
4. [Copy assets folder](#copy-assets-folder)
5. [Configuration file](#configuration-file)
6. [Routes Configuration](#routes-configuration)
7. [Preparing our Resources](#preparing-our-resources)
8. [See it working 👀](#see-it-working)
9. [Let's refactor our Controller](#let's-refactor-our-controller)
10. [Celebrate 🎉](#celebrate)

This is a full tutorial of a suggested way to install Grocery CRUD Enterprise
to your already existing project with Laravel version 10

## Prerequisites

- You have purchased <a href="https://www.grocerycrud.com/enterprise" target="_blank">Grocery CRUD Enterprise</a> and 
you have access to <a href="https://www.grocerycrud.com/users/" rel="nofollow" target="_blank">Client's page</a>.
- PHP 8 or later.
- You've already installed Laravel 10 to your project via composer.
- You've already installed composer to your project and the vendor files by using the command `composer install`. 

## Download Grocery CRUD zip file

Login to <a href="https://www.grocerycrud.com/users/" rel="nofollow" target="_blank">Client's page</a> and navigate to "Version 3 BETA" sidebar menu

![Version 3 Sidebar Menu](/uploads/documentation/version-3-sidebar-menu.png)

Then download the zip file that say's "with composer".

![Download composer zip file](/uploads/documentation/download-composer-zip-file.png)

Your file will look something like this: <code>grocery-crud-enterprise-3.0.0-beta.1.zip</code>. Now at your root directory create a new directory with name <code>artifacts</code> and copy the zip file there <strong>without</strong> unziping it. The final file structure will look something like this:
<pre>├── app
├── artifacts
│   └── grocery-crud-enterprise-3.0.0-beta.1.zip
├── artisan
├── bootstrap
├── composer.json
├── config
├── database
├── lang
...
├── tests
└── vendor
</pre>

## Install Grocery CRUD Enterprise via composer

Add the following commands:

<pre><code class="language-sh">composer config repositories.grocery-crud artifact artifacts/
composer require grocery-crud/enterprise:3.0.*@dev</code></pre>

After those commands your `composer.json` file will look more or less like this:
<pre><code class="language-json">{
    "name": "laravel/laravel",
    "type": "project",
    "description": "The Laravel Framework.",
    "keywords": [
        "framework",
        "laravel"
    ],
    "license": "MIT",
    "require": {
        "php": "^8.1",
        "grocery-crud/enterprise": "3.0.*@dev",
        "guzzlehttp/guzzle": "^7.2",
        "laravel/framework": "^10.0",
        "laravel/sanctum": "^3.2",
        "laravel/tinker": "^2.8"
    },
    "require-dev": {
        "fakerphp/faker": "^1.9.1",
        "laravel/pint": "^1.0",
        "laravel/sail": "^1.18",
        "mockery/mockery": "^1.4.4",
        "nunomaduro/collision": "^7.0",
        "phpunit/phpunit": "^10.0",
        "spatie/laravel-ignition": "^2.0"
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
            "pestphp/pest-plugin": true,
            "php-http/discovery": true
        }
    },
    "minimum-stability": "stable",
    "prefer-stable": true,
    "repositories": {
        "grocery-crud": {
            "type": "artifact",
            "url": "artifacts/"
        }
    }
}
</code></pre>

Update composer in order to get the library of Grocery CRUD Enterprise at the <code>vendor</code> folder
Now go to your root folder with your terminal and simply type:

<pre><code class="language-sh">composer update</code></pre>

You will be able to see many updates such us lamina db and also:

<pre><code> - Installing grocery-crud/enterprise (3.0.0-beta.1)</code></pre>

Now Grocery CRUD Enterprise is available through composer so you could see the below folder structure at your <code>vendor</code> folder:

<pre>vendor
├── ...
...
├── fzaninotto
├── grocery-crud
│   └── enterprise
│       ├── change-log.txt
│       ├── composer.json
│       ├── example
│       ├── LICENCE.md
│       ├── public
│       └── src
├── hamcrest
...</pre>

## Copy assets folder

The easiest way to copy the public assets is with our wonderful artisan tool of Laravel. In short, just one line of code:

<pre><code class="language-sh">php artisan vendor:publish --provider="GroceryCrud\LaravelAssetsServiceProvider"</code></pre>

From the above command you will get the following result:

![Laravel copy assets through artisan](/uploads/documentation/laravel-assets-copy.png)

and your `public` folder will look like this:

<pre>├── favicon.ico
├── index.php
├── robots.txt
└── vendor
    └── grocery-crud
        ├── css
        ├── icons
        ├── js
        └── static
</pre>

If this worked then go to the next step ⏩. If not don't worry as you can also do the steps manually.

More specifically, navigate to: <code>vendor/grocery-crud/enterprise/public</code> and copy it to the public folder:
<code>public/vendor</code>. There is a big possibility that you don't have a <code>vendor</code> folder at your public 
folder. If that's the case, just create it! Now rename the <code>public</code> folder to <code>grocery-crud</code> 
and your final path will look like this: <code>public/vendor/grocery-crud</code>.

## Configuration file

Go to your project's <code>config</code> folder and create a file with name <code>grocerycrud.php</code> that will include the below code:

<pre><code class="language-php">&lt;?php
// config/grocerycrud.php

return [
    // So far 34 languages including: Afrikaans, Arabic, Bengali, Bulgarian, Catalan, Chinese, Czech, Danish,
    // Dutch, English, French, German, Greek, Hindi, Hungarian, Indonesian, Italian, Japanese, Korean,
    // Lithuanian, Mongolian, Norwegian, Persian, Polish, Portuguese, Brazilian Portuguese, Romanian,
    // Russian, Slovak, Spanish, Thai, Turkish, Ukrainian, Vietnamese
    'default_language'  => 'English',

    // This is the assets folder where all the JavaScript, CSS, images and font files are located
    'assets_folder' => env('APP_URL') . '/vendor/grocery-crud/',

    // The default per page when a user firstly see a list page
    'default_per_page'	=> '10',

    // Having some options at the list paging. This is the default one that all the websites are using.
    // Make sure that the number of grocery_crud_default_per_page variable is included to this array.
    'paging_options' => ['10', '25', '50', '100'],

    // The environment is important, so we can have specific configurations for specific environments
    'environment' => 'development',

    // The default theme that Grocery CRUD will use. Currently, you can choose between 'bootstrap-v3' and 'bootstrap-v4'
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
    'publish_events' => true,

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
    'optimize_sql_queries' => false,

    // Remember the quick search upon refresh. The search information is stored in the browser local storage
    'remember_quick_search' => true,
];</code></pre>

<strong>Important Notice:</strong> Make sure that you have configured the correct website path at the file <code>.env</code>. More specifically change the below code:

<pre><code class="language-sh">APP_URL="http://localhost"</code></pre>

to your original project path. For example:

<pre><code class="language-sh">APP_URL="http://local.grocerycrud.com"</code></pre>


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

As you can see at the above code, we are simply saying that for the URL `/admin/customers-management` for `POST` or 
`GET` method then load the Controller `AdminController` and the function `customers`.
For now, I am just adding 6 lines of code for the simplicity of the installation. However, you can always create a 
specific function that can do that for you so you will not need to copy-paste 6 lines of code all the time.


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

&lt;/head&gt;
&lt;body&gt;
	&lt;div style="padding: 20px"&gt;
		{!! $output !!}
	&lt;/div&gt;

	@foreach ($js_files as $js_file)
    	&lt;script src="{{ $js_file }}"&gt;&lt;/script&gt;
	@endforeach
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

After that short break enjoy the power of Grocery CRUD Enterprise at your project! From now on with few lines of PHP you can get a full working CRUD for your project 🤗

In case you still have issues with the installation also consider checking the video tutorial: <a target="_blank" href="https://www.youtube.com/watch?v=bCJTU6PWhYs">Troubleshooting Grocery CRUD Enteprise part 1</a>.

<blockquote><strong>Notice:</strong> Grocery CRUD Enterprise is a framework agnostic library. That simply means that it doesn't matter which framework you are using and it doesn't matter which architecture you are using. It can work in any PHP platform! This tutorial is taking some architecture decisions basically for you! If you need to have the full freedom of what structure to choose we are suggesting to see the full installation guide <a href="/v3.x/docs/grocery-crud-enterprise-installation">here</a>.</blockquote>
