---
id: set-relation-dynamic
title: setRelationDynamic
description: Database relation with a 1 to n (1:n) relation with dynamic search.
canonical: docs/set-relation-dynamic
previous: set-relation
next: set-relation-n-to-n
---

# setRelationDynamic
<pre><code class="language-php">setRelationDynamic(string $fieldName , string $relatedTable, string $relatedTitleField)</code></pre>

Same as [setRelation](/v3.x/docs/set-relation) but with dynamic search for the relation data. Ideal for big amount of data on the relation table.

## Example

A full working example can be found here:
<pre><code class="language-php">$crud-&gt;setTable('employees');
$crud-&gt;setSubject('Employee', 'Employees');
$crud-&gt;setRelationDynamic('officeCode','offices','city');
$crud-&gt;displayAs('officeCode','City');

$output = $crud-&gt;render();</code></pre>
You can see the result of the above code at the below datagrid. You can see how the functionality behaves by simply
searching the dynamic field "City".


`embed:demo_set-relation-dynamic`