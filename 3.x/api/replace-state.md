---
id: replace-state
title: replaceState
description: 
canonical: docs/replace-state
previous: map-column
next: set-api-url-path
---

# replaceState

<pre><code class="language-php">replaceState(string $stateName, StateInterface $newState)</code></pre>
Replace the default state by the custom object state that we are adding as an input.

<h2>Example 1</h2>

A simple example of replacing the default ExportState with a custom one that will export all the columns and not only the visible ones.

<pre><code class="language-php">&lt;?php
use GroceryCrud\Core\State\ExportState;
use GroceryCrud\Core\State\StateInterface;

class CustomExportState extends ExportState implements StateInterface {
    public function getStateParameters() {
        $stateParameters = parent::getStateParameters();

        $stateParameters->visible_columns = null;

        return $stateParameters;
    }

}</code></pre>

And you can use the above custom state by using the below code:

<pre><code class="language-php">$exportState = new CustomExportState($crud);
$crud->replaceState('Export', $exportState);</code></pre>

<h2>Example 2</h2>

A most common use of this state is on export, where we would like to have a different export way for your data. The below example still uses the queries from Zend Db calls but you can literally use your own libraries even for database calls (e.g. when we have more than 10.000 rows).

<strong>Step 1.</strong> Make sure that you have installed a PHP library for exporting to a spreadsheet. For example in my case i am using composer and I've wrote the below command line in my console:

<pre><code class="language-bash">composer require mk-j/php_xlsxwriter</code></pre>

<strong>Step 2.</strong> Create a custom State that will implement the <code>GroceryCrud\Core\State\StateInterface</code> (required). We have a complete example by using the php_xlswriter library below:

<pre><code class="language-php">&lt;?php
namespace MyCustomStates;

use GroceryCrud\Core\GroceryCrud as GCrud;
use GroceryCrud\Core\State\StateInterface;
use GroceryCrud\Core\State\ExportState as GcExportState;


class ExportState implements StateInterface {

    protected $exportStateObject;
    protected $gCrud;

    /**
     * DatagridState constructor.
     * @param \GroceryCrud\Core\GroceryCrud $gCrud
     * @throws \GroceryCrud\Core\Exceptions\Exception
     */
    function __construct(GCrud $gCrud)
    {
        $this->gCrud = $gCrud;
        $this->exportStateObject = new GcExportState($gCrud);

        $this->exportStateObject->setPage(1);

        // Please have in mind that our new limitation is 10.000 as we've tested and checked that the database
        // memory has some limitations with Zend db when we are calling more than 10.000 rows and send all of
        // our results.
        $this->exportStateObject->setPerPage(10000);
    }

    public function render() {
        // As this is a custom file and you can literaly do whatever you wish, if the queries are not optimized for your
        // needs (e.g. the 10.000 rows are too little) then you can use the function:
        // $this->exportStateObject->getStateParameters(); and create your own queries with your way to export data to
        // excel (e.g. you don't have to use the getFinalData if it doesn't fit your needs)
        $output = $this->exportStateObject->getFinalData();

        $results = $output->data;
        $columns = $output->columns;
        
        // Use your own folder that you have all the exported spreadsheets. In our example we are 
        // using "export/" (have in mind that I am not adding the slash at the end)
        $temporaryFolderPath = 'export';

        $this->exportToExcelWithXlsWriter($results, $columns, $temporaryFolderPath);

        exit;
    }

    public function exportToExcelWithXlsWriter($results, $columns, $temporaryFolderPath) {

        $header  = [];

        foreach ($columns as $column) {
            $header[] = $column->displayAs;
        }

        $data = [
            $header
        ];

        foreach ($results as $row) {
            $tmp_row = [];
            foreach ($columns as $column) {
                $tmp_row[] = $row[$column->name];
            }

            $data[] = $tmp_row;
        }

        $subjectPlural = $this->gCrud->getSubjectPlural();

        $filename = !empty($subjectPlural) ? $subjectPlural : 'Spreadsheet';
        $filename .= '_' . date('Y-m-d');

        $filePath = $temporaryFolderPath. '/' . $filename . '_' . uniqid() .'.xlsx';

        $writer = new \XLSXWriter();
        $writer->writeSheet($data);
        $writer->writeToFile($filePath);

        // WARNING! This is just an example of a way to export an excel file without running out of memory
        // Before using this redirection with a public access please make sure that you understand the security risks
        // and that you have cronjobs to remove older spreadsheets or else this could drive you to a security and
        // privacy breach
        header('Location:' . $filePath);

        exit;
    }
}
</code></pre>
<strong>Step 3.</strong> Include the PHP library into your CRUD by adding at the beginning of your file (e.g. Controller if we are talking about Codeigniter):

<pre><code class="language-php">// states is the folder that I have all my custom states
include('states/ExportState.php');

// It is better to use namespaces so it will not be conflicted with other libraries
use MyCustomStates\ExportState;</code></pre>

<strong>Step 4.</strong> Lastly, let's replace our default ExportState with our custom one. Please have in mind that the library is completely replacing the default one so if you are going to use this you will also need to make sure that you have validated the input data:


<pre><code class="language-php">// ExportState is from MyCustomStates\ExportState
$exportState = new ExportState($crud);
$crud->replaceState('Export', $exportState);</code></pre>

For security reasons we don't have a demo of the above replacement as it may impact the bandwidth limitations of the website. The current example works fine for 10.000 rows but you can go further than that by also replacing the database queries and use your custom queries by also using the framework default database connection (e.g. For Codeigniter you can use Models)
