---
id: set-sequence-name
title: setSequenceName
description: Postgres database recognise the insert id with a sequence key.
canonical: docs/set-sequence-name
previous: set-relation-n-to-n
next: display-as
---

# setSequenceName

<pre><code class="language-php">setSequenceName(string $sequenceName)</code></pre>

Postgres database recognise the insert id with a sequence key. This key can be easily guessed automatically but there are many cases that we are adding the key as a different name. In that case we can use the function:

<pre><code class="language-php">$crud->setSequenceName('my_sequence_name');</code></pre>

so we can customise the name of the sequence so it will get the insertId after an insert operation.