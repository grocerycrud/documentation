---
id: set-csrf-token-name
title: setCsrfTokenName
description: Specify the token name for CSRF protection.
canonical: docs/set-csrf-token-name
previous: unset-react
next: set-csrf-token-value
---

# setCsrfTokenName

<pre><code class="language-php">setCsrfTokenName(string $tokenName)</code></pre>
Specify the token name for CSRF protection. This field will be sent in every AJAX request if the token value is not empty. The token value can be set with <a href="/docs/set-csrf-token-value">setCsrfTokenValue</a>. The default CSRF token name is <code>__csrf</code>.

As it doesn't make too much sense to use <code>setCsrfTokenName</code> without <code>setCsrfTokenValue</code> there are examples of usage at the page of: <a href="/docs/set-csrf-token-value">setCsrfTokenValue</a>