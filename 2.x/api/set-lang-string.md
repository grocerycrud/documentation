---
id: set-lang-string
title: setLangString
permalink: docs/set-lang-string
previous: set-field-upload
next: set-language
---

# setLangString

<pre><code class="language-php">setLangString(string $handle, string $translation)</code></pre>
You can simply change any handle of the translation with the method <code>setLangString</code>. A common usage is when a translation is missing or you really need to change the default value of the string. It is pretty easy to do that as it requires only the handle and the translation. For example:

<pre><code class="language-php">$crud->setLangString('edit_item', 'Edit {subject} now!');
$crud->setLangString('view', 'Show me');
</code></pre>

At the below full example we are changing two of the handles: the print button and the delete button
<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');

$crud->setLangString('action_delete', 'Destroy!');
$crud->setLangString('print', 'Send to print');

$output = $crud->render();</code></pre>

You can also notice that we don't have the default strings and the strings are replaced by the custom text that we did use at the <code>setLangString</code> function:

[demo]demo_set_lang_string[/demo]