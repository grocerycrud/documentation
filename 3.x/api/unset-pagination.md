---
id: unset-pagination
title: unsetPagination
description: Hide the pagination controls from the datagrid footer.
canonical: docs/unset-pagination
previous: unset-operations
next: unset-print
---

# unsetPagination

<pre><code class="language-php">unsetPagination(void)</code></pre>

The `unsetPagination` method hides the pagination controls from the datagrid footer. 
This is useful when you want to display all records without pagination, or when working 
with custom queries that return a limited dataset.

<h2>Example Usage</h2>

<h3>Basic Example</h3>

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->unsetPagination();

$output = $crud->render();</code></pre>

<h2>Full Example</h2>

When using `setCustomQuery` without providing a count query,  it's recommended to 
use `unsetPagination` to ensure a consistent user experience.

This example shows how to use `unsetPagination` with a custom query that returns a small, specific dataset.

<pre><code class="language-php">$selectQuery = "
    SELECT
        cu.customerNumber,
        c.country,
        COUNT(DISTINCT cu.customerNumber) AS total_customers,
        SUM(cu.creditLimit) AS total_credit
    FROM customers cu
    JOIN (
        SELECT DISTINCT country FROM customers
    ) c ON cu.country = c.country
    GROUP BY c.country
    ORDER BY total_customers DESC
";

$crud->unsetPagination();

$crud->setCustomQuery($selectQuery);
$crud->setSubject('Country Summary', 'Country Summaries');
$crud->columns(['country', 'total_customers', 'total_credit']);
$crud->displayAs('total_customers', 'Total Customers');
$crud->displayAs('total_credit', 'Total Credit Limit');
$crud->setTable('customers'); // Required for the library to work

// Disable all CRUD operations as this is a read-only summary
$crud->unsetOperations();
// Disable filtering and ordering since it is not supported with custom queries yet.
$crud->unsetFilters();
$crud->unsetSearchColumns(['country', 'total_customers', 'total_credit']);
$crud->unsetSortingColumns(['country', 'total_customers', 'total_credit']);


$output = $crud->render();</code></pre>

You can see the results for the above example at the below demo:

`embed:demo_unset-pagination`

