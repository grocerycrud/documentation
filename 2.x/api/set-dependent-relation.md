---
id: set-dependent-relation
title: setDependentRelation
description: There are cases that dropdown list that was built from setRelation has dependencies between them.
canonical: docs/set-dependent-relation
previous: set-database-schema
next: set-model
---

# setDependentRelation

<pre><code class="language-php">setDependentRelation(string $fieldName, string $dependencyFromField, string $fieldNameRelation)</code></pre>
<div class="quick-description">Available from version >= 2.6.1</div>

There are cases that dropdown list that was built from setRelation has dependencies between them. The most common example that we see very often on registration forms is that the continent dropdown will filter the countries and countries dropdown will filter the cities.

You can see an example of the expected results here:

<img src="/uploads/documentation/depended-relation.gif" alt="Depended Relation Animated" />

The usage is coming with an <strong>extra</strong> line of code that is looking like this:

<pre><code class="language-php">$crud->setDependentRelation('relationFieldName', 'dependencyFieldName', 'parentId')</code></pre>

So for example if we have a <code>country</code> setRelation and a <code>city</code> setRelation that looks like this:

<pre><code class="language-php">$crud->setRelation('country_id','countries','name');
$crud->setRelation('city_id','cities','name');</code></pre>

If the <code>city_id</code> is depended (filterted) from <code>country_id</code> then we will need to add only one extra line that will look like this:

<pre><code class="language-php">$crud->setDependentRelation('city_id','country_id','country');</code></pre>

With this line of code the result will be that when the country changes then it filters the city_id dropdown will have filtered only the ones from this country. 

You can see a full example below:

<pre><code class="language-php">$crud->setTable('customers_db');
$crud->setSubject('Customer', 'Customers');

$crud->displayAs('continent_id', 'Continent');
$crud->displayAs('country_id', 'Country');
$crud->displayAs('city_id', 'City');

$crud->setRelation('continent_id','continents','name');
$crud->setRelation('country_id','countries','name');
$crud->setRelation('city_id','cities','name');

$crud->setDependentRelation('country_id','continent_id','continent_code');
$crud->setDependentRelation('city_id','country_id','country');

$output = $output->render();
</code></pre>

In case you would like to see the results of the above example we do have the data copied here: <a href="https://gist.github.com/scoumbourdis/bc72fce984fedb2d57e4256bc438c4ae">https://gist.github.com/scoumbourdis/bc72fce984fedb2d57e4256bc438c4ae</a>