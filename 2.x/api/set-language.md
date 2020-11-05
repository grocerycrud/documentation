---
id: set-language
title: setLanguage
permalink: docs/set-language
previous: set-subject
next: set-skin
---

# setLanguage

<pre><code class="language-php">setLanguage(string $languageName)</code></pre>
All the lang strings in Grocery CRUD Enterprise are editable so we can have a multilingual functionality. The syntax is simple:
<pre><code class="language-php">$crud-&gt;setLanguage('Spanish')</code></pre>

The functionality also known as Locale or i18n (shortcut of Internationalization) is available in 34 languages so far including:
<ol>
<li>Arabic</li>
<li>Bengali</li>
<li>Bulgarian</li>
<li>Catalan</li>
<li>Chinese</li>
<li>Croatian</li>
<li>Czech</li>
<li>Danish</li>
<li>Dutch</li>
<li>English</li>
<li>French</li>
<li>German</li>
<li>Greek</li>
<li>Hindi</li>
<li>Hungarian</li>
<li>Indonesian</li>
<li>Italian</li>
<li>Japanese</li>
<li>Korean</li>
<li>Lithuanian</li>
<li>Mongolian</li>
<li>Norwegian</li>
<li>Persian</li>
<li>Polish</li>
<li>Romanian</li>
<li>Russian</li>
<li>Slovak</li>
<li>Spanish</li>
<li>Thai</li>
<li>Turkish</li>
<li>Ukrainian</li>
<li>Vietnamese</li>
<li>pt-BR.Portuguese</li>
<li>pt-PT.Portuguese</li>
</ol>

A more specific example can be found below:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Cliente', 'Clientes');
$crud->fields(['customerName','phone','addressLine1','creditLimit']);
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->setLanguage('Spanish');

$crud->displayAs('customerName', 'Nombre')
     ->displayAs('phone', 'Teléfono')
     ->displayAs('addressLine1', 'Dirección')
     ->displayAs('creditLimit', 'Límite de crédito');

$output = $crud->render();
</code></pre>

As you can also see all the dynamic strings (expect of the database field names) are translated in Spanish:
[demo]demo_set_language[/demo]
