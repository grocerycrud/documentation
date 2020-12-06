---
id: set-sequence-name
title: setSequenceName
permalink: docs/set-sequence-name
previous: set-rules
next: set-skin
---

# setSequenceName


<pre><code class="php">setSequenceName(string $sequenceName)</code></pre>

Postgres database is recognising the insert id with a sequence key. This key can be easily guessed automatically but there are many cases that we are adding the key as a different name. In that case we can use the function:

<pre><code class="php">$crud->setSequenceName('my_sequence_name');</code></pre>

so we can customise the name of the sequence so it will get the insertId after an insert operation.