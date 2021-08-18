---
id: javascript-events
title: JavaScript Events
description: Example for JavaScript events that Grocery CRUD uses for custom development through JavaScript.
permalink: docs/javascript-events
previous: 
next:
---

# JavaScript Events

<pre><code class="language-js">window.addEventListener('gcrud.datagrid.ready', () => {
    console.log('datagrid ready triggered');
});

window.addEventListener('gcrud.form.add_form', () => {
    console.log('add_form triggered');
});

window.addEventListener('gcrud.form.edit_form', ({detail}) => {
    console.log('edit_form triggered', detail);
});

window.addEventListener('gcrud.form.clone_form', ({detail}) => {
    console.log('clone_form triggered', detail);
});

window.addEventListener('gcrud.form.read_form', ({detail}) => {
    console.log('read_form triggered', detail);
});</code></pre>





