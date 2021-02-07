---
id: grocery-crud-enterprise-laravel-8-installation
title: Install Grocery CRUD Enterprise in Laravel 8
permalink: docs/grocery-crud-laravel-8-installation
previous:
next:
---

# Laravel 8 installation

This is a full tutorial of a suggested way to install Grocery CRUD Enterprise 
to your already existing project with Laravel version 8.

<blockquote><strong>Notice:</strong> Grocery CRUD Enterprise is a framework agnostic library. That simply means that it doesn't matter which framework you are using and it doesn't matter which architecture you are using. It can work in any PHP platform! This tutorial is taking some architecture decisions basically for you! If you need to have the full freedom of what structure to choose we are suggesting to see the full installation guide <a href="/docs/grocery-crud-enterprise-installation">here</a>.</blockquote>

**Step 1. Copying the zip file to the correct folder**

From the email that you've received or from the user's page (you will get instructions at the email of how to access user's page) download the zip file that say's "With composer".

Your file will look something like this: <code>grocery-crud-enterprise-v2.8.7.zip</code>. Now at your root directory create a new directory with name <code>artifacts</code> and copy the zip file there <strong>without</strong> unziping it. The final file structure will look something like this:
<pre>├── app
<strong>├── artifacts
│   └── grocery-crud-enterprise-v2.8.7.zip</strong>
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

**Step 2. Update composer.json**

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

**Step 3. Update composer from the console**

Update composer in order to get the library of Grocery CRUD Enterprise at the <code>vendor</code> folder
Now go to your root folder with your terminal and simply type:

<pre>composer update</pre>

You will be able to see many updates such us zend db but you will also see this:

<pre><code> - Installing grocerycrud/enterprise (2.8.7)</code></pre>

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

**Step 4. Copying the assets folder to our project**

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

**Step 5. Create the configuration file for Grocery CRUD Enterprise**
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
    'assets_folder' => env('APP_URL') . '/assets/grocery-crud/',

    // There are only three choices: "uk-date" (dd/mm/yyyy), "us-date" (mm/dd/yyyy) or "sql-date" (yyyy-mm-dd)
    'date_format' => 'uk-date',

    // The default per page when a user firstly see a list page
    'default_per_page'  => 10,

    // Having some options at the list paging. This is the default one that all the websites are using.
    // Make sure that the number of grocery_crud_default_per_page variable is included to this array.
    'paging_options' => ['10', '25', '50', '100'],

    // The environment is important so we can have specific configurations for specific environments
    'environment' => 'development',

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
    
    // The allowed file types on upload. If the file extension doesn't exist in the array
    // it will throw an error and the upload will not be completed
    'upload_allowed_file_types' =>  [
        'gif', 'jpeg', 'jpg', 'png', 'svg', 'tiff', 'doc', 'docx',  'rtf', 'txt', 'odt', 'xls', 'xlsx', 'pdf',
        'ppt', 'pptx', 'pps', 'ppsx', 'mp3', 'm4a', 'ogg', 'wav', 'mp4', 'm4v', 'mov', 'wmv', 'flv', 'avi',
        'mpg', 'ogv', '3gp', '3g2'
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
];</code></pre>

<strong>Important Notice:</strong> Make sure that you have configured the correct website path at the file <code>.env</code>. More specifically change the below code:

<pre><code>APP_URL=http://localhost</code></pre>

to your original project path. For example:

<pre><code>APP_URL=http://local.grocerycrud.com</code></pre>

**Step 6. Configuring our routes and creating our controller to render our CRUD**
Now we will need to create our routes to point to our controller. Let's start by configuring routes! Go to routes/web.php and add those two lines of code:

<pre><code class="php">// web.php
Route::get('customers', 'CustomersController@datagrid');
Route::post('customers', 'CustomersController@datagrid');</code></pre>

As you can see at the above code, we are simply saying that if you have at the first parameter the word <code>customers</code> then direct the user to <code>CustomersController</code> and the function <code>datagrid</code>. Now a common mistake that we are often seeing is that developers are forgetting to also allow <code>post</code> requests to be available. Grocery CRUD Enterprise is using <em>GET</em> and <em>POST</em> requests in order to work.

Now that we've created our routes let's create our empty for now Controller. In order to do that go to: <code>app/Http/Controllers/</code> and create a new file with name <code>CustomersController.php</code>. There add a simple controller like the one below:

<script src="https://gist.github.com/scoumbourdis/19ac4287427fa581a53e517ffe47283e.js"></script>

As you can also see from the above code, we did also add the <code>use GroceryCrud\Core\GroceryCrud;</code> in order to make sure that Grocery CRUD Enterprise can load. In case this line doesn't work for you, please make sure that you follow the above steps in order to install Grocery CRUD Enterprise with composer first.

Now our datagrid has just a response "Hello World!" So if you go to your website and navigate to: example.com/customers you should see the phrase "Hello World!". If you see this message that means that your routes are configured correctly and that we can load Grocery CRUD Enterprise

<div id="step-7">
    <strong>Step 7. Preparing our blade view for a generic template to load our output string, JS and CSS files</strong> 
</div>
In Grocery CRUD Enterprise we are using the function render() to render 3 main things:
<ul>
	<li>The HTML output string</li>
	<li>The CSS files</li>
	<li>The JavaScript files</li>
</ul>

So it is important to have a template that can load all of the above. Usually in our project we've already have a template to load the CSS and JS files but in case we don't, we can create a new template view like the below. Go to: <code>resources/views/</code> and create a new file with name: <code>default_template.blade.php</code>. Then copy the below code:
<script src="https://gist.github.com/scoumbourdis/861efc53ee1ffd1b731f00f3c76ebf9f.js"></script>

As you may also notice (and this is the second most common mistake for Laravel installations) we are also adding the CSRF token as a meta tag on the header:

<pre><code class="php">&lt;meta name="csrf-token" content="{{ csrf_token() }}"&gt;</code></pre>

And we are are having the CSRF token as a default header with the below code:

<pre><code class="javascript">$(document).ready(function () {
    $.ajaxSetup({
        headers: {
            'X-CSRF-TOKEN': $('meta[name="csrf-token"]').attr('content')
        }
    });
});</code></pre>

As this will be a generic template we are also making sure that we are checking if jQuery exists with the below code:

<pre><code class="javascript">if (typeof $ !== 'undefined') {</code></pre>

<strong>Step 9. Load Grocery CRUD Enterprise and make it work!</strong>

Now finally after 9 steps it is time to see Grocery CRUD Enterprise working on your screen! In order to do that your final controller will look like below:

<script src="https://gist.github.com/scoumbourdis/48e13bac40d43b0e95d4f5d0beac9795.js"></script>

Let's explain a little bit what we did at the controller. Grocery CRUD Enterprise needs two kind of configurations:

<ul>
	<li>The database connection</li>
	<li>The Grocery CRUD Enterprise configurations</li>
</ul>

The database configuration can be taken dynamically from Laravel as it is already located at: <code>config/database.php</code>. So in order to retrieve the database connection data we are simply doing this:

<pre><code class="php">$databaseConnection = config('database.default');
$databaseConfig = config('database.connections.' . $databaseConnection);
</code></pre>

In our case, our default database is MySQL and that's why we have as hardcoded the value of the Zend driver as <code>Pdo_Mysql</code> So the final result of the configuration is:

<pre><code class="php">private function _getDatabaseConnection() {
        $databaseConnection = config('database.default');
        $databaseConfig = config('database.connections.' . $databaseConnection);
        return [
            'adapter' => [
                'driver' => 'Pdo_Mysql',
                'database' => $databaseConfig['database'],
                'username' => $databaseConfig['username'],
                'password' => $databaseConfig['password'],
                'charset' => 'utf8'
            ]
        ];
}
</code></pre>

Please have in mind that for different databases you will need to change the adapter driver. For example you can use the following drivers:

<ul>
	<li><code>Pdo_Pgsql</code> for PostgreSQL</li>
	<li><code>Pdo_Sqlite</code> for  SQLite</li>
	<li>For Microsoft SQL server you should follow the <a href="https://www.grocerycrud.com/enterprise/examples-3/database-connection-mssql">Connection with MSSQL guidelines</a></li>
</ul>

And you can also see all the available database connections from <a href="https://framework.zend.com/manual/2.4/en/modules/zend.db.adapter.html">Zend Db adapter</a>.

The next configuration is the configuration that we did describe at step 5 and we are simply calling this configuration like this:

<pre><code class="php">$config = config('grocerycrud');</code></pre>

Now let's explain quickly what the below code is doing:

<pre><code class="php">if ($output->isJSONResponse) {
    return response($output->output, 200)
          ->header('Content-Type', 'application/json')
          ->header('charset', 'utf-8');
}
</code></pre>

At the above code, we are checking if the response is JSON and if not we are calling our main template view. In case the response is JSON then we are simply returning the JSON response that it is already formatted as a string by Grocery CRUD Enterprise with some JSON headers.

<strong>Step 10. [IMPORTANT] Some advices about the best way to structure your controller</strong>

With Grocery CRUD Enterprise, we've notice that we are repeating the same code again and again. That's why it is strongly recommended to move the initial call with the configurations and the final output code into two separate functions. For example the above controller can be refactored with the below one:

<script src="https://gist.github.com/scoumbourdis/42b8164c0a199510554ce1869564babc.js"></script>

So as you can also see our current implementation of customers is only the below lines:

<pre><code class="php">public function datagrid()
{
    $crud = $this->_getGroceryCrudEnterprise();

    $crud->setTable('customers');
    $crud->setSubject('Customer', 'Customers');

    $output = $crud->render();

    return $this->_show_output($output);
}</code></pre>

And of course we can only now copy those few lines of code in case we need to create another CRUD.

For example:
<pre><code class="php">public function offices()
{
    $crud = $this->_getGroceryCrudEnterprise();

    $crud->setTable('offices');
    $crud->setSubject('Office', 'Offices');

    $output = $crud->render();

    return $this->_show_output($output);
}</code></pre>

<strong>Step 11. Enjoy ❤️</strong>

Don't forget to celebrate your installation. Take a break and drink some coffee ☕ , tea or water and enjoy the power of Grocery CRUD Enterprise at your project!

In case you have issues with the installation also consider to check the most common mistakes of Grocery CRUD here: <a href="https://youtu.be/X0gnDD0qTS8" target="_blank" rel="noopener noreferrer">https://youtu.be/X0gnDD0qTS8</a>. This video has examples for Codeigniter framework but you can follow the same instructions for Laravel framework as well.


