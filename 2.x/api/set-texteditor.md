---
id: set-texteditor
title: setTexteditor
permalink: docs/set-texteditor
previous: set-table
next: set-theme
---

# setTexteditor


<pre><code class="language-php">setTexteditor(array $fields)</code></pre>
The method setTexteditor is used when we want to specify one field as text that will be edited with a texteditor. The default texteditor is CKeditor. For example:

<pre><code class="language-php">$crud->setTexteditor(['notes', 'full_text']);</code></pre>

You can find a full working example below:
<pre><code class="language-php">$crud->setTable('film');
$crud->setSubject('Film', 'Films');
$crud->setTexteditor(['description']);

$output = $crud->render();</code></pre>

The result of the above example can be found below. Press the add or the edit button in order to see the editor working:
[demo]demo_set_texteditor[/demo]