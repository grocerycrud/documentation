---
id: postgresql-connection
title: Connect with PostgreSQL database
description: Step-by-step guide, on how to connect with a PostgreSQL database
permalink: docs/postgresql-connection
previous: api-and-functions-list
next: basic-example
---

# PostgreSQL connection

<strong>Step 1.</strong> So first, we will need to make sure that we've installed correctly some extra drivers into your PHP ini so you can enable the functionality of PostgreSQL connection. To make the long story short one quick way is to uncomment the extension on the <code>php.ini</code> file:
<pre><code>extension=pgsql.so</code></pre>
<strong>Notice:</strong> As they are plenty ways to install those drivers and it very depends on the operation system that you are using and the PostgreSQL database version for now I am keeping it simple that you will just need to make sure that you will include the above extensions on your <code>php.ini</code> file. At the future this notice will probably be removed and we will replaced it with a more specific tutorial of how to install PostgreSQL in PHP.

<strong>Step 2. Configuring Grocery CRUD Enterprise PostgreSQL connection:</strong>

Your database file for connecting with PostgreSQL after the <a href="https://www.grocerycrud.com/enterprise/enterprise-documentation/installation-guide" target="_blank" rel="noopener noreferrer">installation guide</a> it should look something like this:

<pre><code class="language-php">&lt;?php
return [
    'adapter' => [
        'driver' => 'Pdo_Pgsql', // This is the driver that you should be using
        'database' => 'my_database_name',
        'username' => 'my_username',
        'password' => 'my_password'
        'charset' => 'utf8'
    ]
];</code></pre>

And this should be it! You will now be able to use all the features that Grocery CRUD Enterprise is offering with PostgreSQL database.

## Codeigniter 4 Example

You can also find a full example of a Codeigniter Framework version 4 controller below:

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
                // It is important to have this specific name as this is the driver for Zend Db
                'driver' => 'Pdo_Pgsql',
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