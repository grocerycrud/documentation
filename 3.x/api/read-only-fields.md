---
id: read-only-fields
title: readOnlyFields
description: Specifying the fields that can't be edited and will only be viewed. 
canonical: docs/read-only-fields
previous: read-only-edit-fields
next: set-read
---

# readOnlyFields

<pre><code class="language-php">readOnlyFields(array $fields)</code></pre>
Specifying the fields that can't be edited and will only be viewed. The rule will be the same for the insert and update operations. 

## Example

The below code:
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->readOnlyFields(['salesRepEmployeeNumber','creditLimit']);</code></pre>

Will have as a result the following output:

`embed:demo_read-only-fields`