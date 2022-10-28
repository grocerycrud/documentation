---
id: set-language-path
title: setLanguagePath
description: 
permalink: docs/set-language-path
previous: set-language
next: set-model
---

# setLanguagePath


<pre><code class="language-php">setLanguagePath(string $languagePath)</code></pre>
<div class="quick-description">Available from version >= 2.5.6</div>
<code>setLanguagePath</code> is used in order to change the default path of the language folder. This is extremely useful when the language file of Grocery CRUD doesn't fit your needs as you may use a different dialect. You can either use the folder of the languages or the direct path for your php file. For example:

<h2>With the folder:</h2>
<pre><code class="language-php">$crud->setLanguagePath('application/language/grocery-crud/');</code></pre>
or without the slash:
<pre><code class="language-php">$crud->setLanguagePath('application/language/grocery-crud');</code></pre>

Of course also don't forget to also choose the preferable language. For example:

<pre><code class="language-php">$crud->setLanguagePath('application/language/grocery-crud');
$crud->setLanguage('Greek');</code></pre>

<h2>With the language file directly:</h2>
You can also pick up directly the language file that you would like to have. For example:

<pre><code class="language-php">$crud->setLanguagePath('application/language/grocery-crud/Spanish.php');</code></pre>

<strong>Notice:</strong> Please have in mind that if the the <code>setLanguagePath</code> has a direct file as a string then the <code>setLanguage</code> function will not work anymore.

<strong>You can also see a full example below:</strong>

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->setLanguagePath('application/language/grocery-crud');
$crud->setLanguage('Spanish');

$output = $crud->render();</code></pre>
