---
id: set-csrf-token-value
title: setCsrfTokenValue
description: 
permalink: docs/set-csrf-token-value
previous: set-csrf-token-name
next: set-database-schema
---

# setCsrfTokenValue


<pre><code class="language-php">setCsrfTokenValue(string $tokenValue)</code></pre>
Specify the token value for CSRF protection. This value will only be sent through AJAX calls if it is not empty.

<h2>Codeigniter version 4 example</h2>

<strong>Step 1.</strong> Go to <code>app/Config/Filters.php</code> and uncomment the <code>'csrf'</code> string at <code>$globals</code> For example:

<pre><code class="language-php">// Always applied before every request
public $globals = [
	'before' => [
		//'honeypot'
		'csrf',
	],
	'after'  => [
		'toolbar',
		//'honeypot'
	],
];</code></pre>

<strong>Step 2.</strong> Add the functions setCsrfTokenName and setCsrfTokenName:

<pre><code class="language-php">$crud-&gt;setTable('customers');
$crud-&gt;setSubject('Customer', 'Customers');
$crud-&gt;columns(['customerName','phone','addressLine1','creditLimit']);

$crud-&gt;setCsrfTokenName(csrf_token());
$crud-&gt;setCsrfTokenValue(csrf_hash());

$output = $crud-&gt;render();</code></pre>

and that's it really!

<h2>Codeigniter version 3 example</h2>

<strong>Step 1.</strong> Go to <code>application/config/config.php</code> and change the <code>csrf_protection</code> to be equal with <code>TRUE</code>. More specifically:
<pre><code class="language-php">$config['csrf_protection'] = TRUE;</code></pre>
<strong>Step 2.</strong> Add the functions setCsrfTokenName and setCsrfTokenName:
<pre><code class="language-php">$crud-&gt;setTable('customers');
$crud-&gt;setSubject('Customer', 'Customers');
$crud-&gt;columns(['customerName','phone','addressLine1','creditLimit']);

$crud-&gt;setCsrfTokenName($this-&gt;security-&gt;get_csrf_token_name());
$crud-&gt;setCsrfTokenValue($this-&gt;security-&gt;get_csrf_hash());

$output = $crud-&gt;render();</code></pre>
