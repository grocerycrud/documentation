---
id: ms-sql-connection
title: Connect with Microsoft SQL database
description: Step-by-step guide, on how to connect with a Microsoft SQL database
canonical: docs/ms-sql-connection
previous: api-and-functions-list
next: basic-example
---

# Microsoft SQL connection

If you've worked with Microsoft SQL databases before you know that this is not a very straight forward connection to the database as it is requiring some first steps before being able to do it so! That's why we are having a specific tutorial for MSSQL database connection.

## Installing the drivers
So first of all we will need to make sure that we've installed correctly some extra drivers into your PHP ini so you can enable the functionality of MSSQL connection. To make the long story short you will need to end up with two extensions:
<pre><code>extension=sqlsrv.so
extension=pdo_sqlsrv.so</code></pre>
<strong>Notice:</strong> As they are plenty ways to install those drivers and it very depends on the operation system that you are using and the SQL database version for now I am keeping it simple that you will just need to make sure that you will include the above extensions on your <code>php.ini</code> file. At the future this notice will probably be removed and we will replace it with a more specific tutorial.

## Check MSSQL connection
Before testing to see if Grocery CRUD Enterprise is working as expected for you, you will need to make sure that you can connect successfully with the PDO drivers of MSSQL. In order to do so you will just need to run a test file connection that will look like this:

<pre><code class="language-php">&lt;?php
// First: Check that you can connect with the SQL PDO drivers (most important)
try {
    $conn = new PDO("sqlsrv:server = tcp:my-database.example.com,1433; Database = my_database_name", "my_server_username", "F0__787asdjhakdsaASJHSDAk");
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
}
catch (PDOException $e) {
    print("Error connecting to SQL Server.");
    die(print_r($e));
}

// Second: Check if you can connect with SQLSRV drivers as in some cases we are also using this approach
$connectionInfo = array(
        "UID" => "my_username@my_server_username",
        "pwd" => "F0__787asdjhakdsaASJHSDAk",
        "Database" => "my_database_name",
        "LoginTimeout" => 30,
        "Encrypt" => 1,
        "TrustServerCertificate" => 0
);
$serverName = "tcp:my-database.example.com,1433";

$conn = sqlsrv_connect($serverName, $connectionInfo);

echo "&lt;pre&gt;";
if ($conn) {
     echo "Connection established.\n";
} else {
     echo "Connection could not be established.\n";
     print_r( sqlsrv_errors(), true);
}

// Third: Check if you have access to see some system information as Grocery CRUD Enterprise will automatically
// check for you the primary key, if field types ... e.t.c.
$sql = "SELECT name FROM sys.Tables";
$stmt = sqlsrv_query( $conn, $sql);

while( $row = sqlsrv_fetch_array( $stmt, SQLSRV_FETCH_ASSOC) ) {
      print_r($row);
}</code></pre>

Once you will see only successful messages and a list of your tables in the database then you are ready to go to step 3
<h2>Configuring Grocery CRUD connection</h2>
Your database file for connecting with MSSQL after the <a href="/docs/grocery-crud-enterprise-installation" target="_blank">installation guide</a> it should look something like this:
<pre>//database.php
&lt;?php
return [
    'adapter' =&gt; [
        'driver' =&gt; 'Pdo',
        'dsn' =&gt; 'sqlsrv:server = tcp:my-database.example.com,1433; Database = my_database_name',
        'database' =&gt; 'my_database_name',
        'username' =&gt; 'my_username',
        'password' =&gt; 'F0__787asdjhakdsaASJHSDAk'
    ]
];</pre>
<strong>Notice:</strong> As you may have noticed, I did remove the <code>'charset' =&gt; 'utf8'</code> as it was causing me a weird connection issue. So in case you have a connection issue please also check that you haven't forgot to remove this line

And this should be it! You will now be able to use all the features that Grocery CRUD Enterprise is offering with MSSQL database.

## Codeigniter 4 Example

You can also find a full example of a Codeigniter Framework version 4 controller below:

<pre><code class="language-php">&lt;?php
namespace App\Controllers;

include(APPPATH . 'Libraries/GroceryCrudEnterprise/autoload.php');
use GroceryCrud\Core\GroceryCrud;

class Example extends BaseController
{
    private function _getDbData() {
        $db = (new \Config\Database())->default;
        return [
            'adapter' => [
                // It is important to have this specific name as this is the driver for Zend Db
                'driver' => 'Pdo',
                'dsn' => $db['DSN'],
                'database' => $db['database'],
                'username' => $db['username'],
                'password' => $db['password']
            ]
        ];
    }

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

    private function _getGroceryCrudEnterprise($bootstrap = true, $jquery = true) {
        $db = $this->_getDbData();
        $config = (new \Config\GroceryCrudEnterprise())->getDefaultConfig();

        $groceryCrud = new GroceryCrud($config, $db);
        return $groceryCrud;
    }
}</code></pre>