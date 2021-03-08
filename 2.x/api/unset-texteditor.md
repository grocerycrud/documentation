---
id: unset-texteditor
title: unsetTexteditor
description: 
permalink: docs/unset-texteditor
previous: set-texteditor
next:
---

# unsetTexteditor


<pre><code class="language-php">unsetTexteditor(array $fields)</code></pre>
The function <code>unsetTexteditor</code> is really rare to use as by default there is not any load of the texteditor for optimising purposes (too big file). It maybe used in case you are enabling all the text-editors by default and then you need to disable it.

The syntax is simple, for example:

<pre><code class="language-php">$crud->unsetTexteditor(['notes', 'full_text']);</code></pre>

To understand better the functionality of the <code>unsetTexteditor</code> we have the below example:
<pre><code class="language-php">$crud->setTable('film');
$crud->setSubject('Film', 'Films');
$crud->setTexteditor(['description']);

$crud->unsetTexteditor(['description']);

$output = $crud->render();</code></pre>

Of course we can understand that it doesn't make any sense to have <code>setTexteditor</code> and then <code>unsetTexteditor</code> right after, however have in mind that this is just an example. The above code is equivalent to the below:

<pre><code class="language-php">$crud->setTable('film');
$crud->setSubject('Film', 'Films');

$output = $crud->render();</code></pre> 

That simply means that the default status of a textarea is <strong>without the texteditor</strong>.

A more real world example could be to have something like that:

<pre><code class="language-php">
if (user_text_editor_not_allowed()) {
   $crud->unsetTexteditor(['description']);
}</code></pre>

Below you can see an example by unsetting the 'description' field to have a texteditor. 
`embed:demo_unset-texteditor`


