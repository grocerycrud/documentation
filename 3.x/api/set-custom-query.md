---
id: set-custom-query
title: setCustomQuery
description: Set a custom select query for datagrid data retrieval.
canonical: docs/set-custom-query
previous: set-csrf-token-name
next: get-state
---

# setCustomQuery

<pre><code class="language-php">setCustomQuery(string $selectQuery[, string $countQuery])</code></pre>

Set a custom select query for datagrid data retrieval. You can use `setCustomQuery` to provide your own SQL query
for the listing/datagrid operation. This is useful when you need to have complex queries that involve joins, 
subqueries, or specific filtering.

> ⚠️ There are some limitations when using `setCustomQuery`:
>  - Currently, we are not supporting filtering and sorting. We may add support for these features in future releases.
>  - Pagination is only supported when you provide the second parameter `$countQuery`.
>  - You always need to return the primary key of the table in the select query for proper functioning of the CRUD operations.
>  - The filtering on the custom query will not filter the results of the CRUD operations (edit, delete, etc). 
In case you need to filter the results of the CRUD operations you will either need to use `$crud->where()` or have custom
validation on "before" callbacks for all the operations. 

Pagination is only supported when you provide the second parameter `$countQuery`. If you do not provide it then all
the data will be fetched in the datagrid without pagination.

<h2>Example Usage</h2>

<pre><code class="language-php">$selectQuery = "SELECT users.id, users.name, roles.role_name 
                FROM users 
                JOIN roles ON users.role_id = roles.id 
                WHERE users.active = 1";
$countQuery = "SELECT COUNT(*) as total 
                FROM users 
                JOIN roles ON users.role_id = roles.id 
                WHERE users.active = 1";
$crud->setCustomQuery($selectQuery, $countQuery);
$output = $crud->render();</code></pre>

or without pagination:

<pre><code class="language-php">$selectQuery = "SELECT users.id, users.name, roles.role_name 
                FROM users 
                JOIN roles ON users.role_id = roles.id 
                WHERE users.active = 1 AND roles.role_name = 'Manager'";
$crud->setCustomQuery($selectQuery);
$crud->unsetPagination();
$output = $crud->render();</code></pre>

<h2>Full Example</h2>

You can find a full working example below:

<pre><code class="language-php">$selectQuery = "
    SELECT
        f.film_id,
        f.title,
        f.release_year,
        GROUP_CONCAT(a.fullname SEPARATOR ', ') AS actors
    FROM film f
    JOIN film_actor fa ON f.film_id = fa.film_id
    JOIN actor a ON fa.actor_id = a.actor_id
    WHERE f.rating = 'PG'
    GROUP BY f.film_id, f.title, f.release_year
";
$countQuery = "
    SELECT COUNT(DISTINCT f.film_id) AS total
    FROM film f
    JOIN film_actor fa ON f.film_id = fa.film_id
    JOIN actor a ON fa.actor_id = a.actor_id
    WHERE f.rating = 'PG'
";
$crud->setCustomQuery($selectQuery, $countQuery);

$crud->setSubject('Film', 'Films');
$crud->columns(['title', 'release_year', 'actors']);
$crud->setTable('film'); // Table name is still required for CRUD operations

// Some additional configurations which will make more sense for this example
$crud->unsetAdd();
$crud->unsetEditFields(['rating']);
// Using where to filter CRUD operations so users with no access to not be able to
// edit/delete films that are not 'PG'
$crud->where(['rating' => 'PG']);
$crud->setRelationNtoN(
    'actors', 'film_actor',
    'actor', 'film_id',
    'actor_id', 'fullname',
    null, null, 'priority'
);
$crud->setRelationNtoN(
    'categories', 'film_category',
    'category', 'film_id',
    'category_id', 'name',
     null, null, 'priority'
);

$output = $crud->render();</code></pre>

You can see the results for the above example at the below demo:

`embed:demo_set-custom-query`