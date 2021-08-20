---
id: javascript-events
title: JavaScript Events
description: Example for JavaScript events that Grocery CRUD uses for custom development through JavaScript.
permalink: docs/javascript-events
previous: 
next:
---

# JavaScript Events

Grocery CRUD Enterprise is dispatching some events on some actions. So far we have the below events:

## Datagrid Ready Event

"Datagrid Ready" event is triggered when the first load of the datagrid has been completed.
With simple words all the data load has been completed, and you are ready to add your custom
stuff in the datagrid. Please keep in mind that this event will triggerred only once 
per refresh and **not** in every datagrid refresh/update.

<pre><code class="language-js">window.addEventListener('gcrud.datagrid.ready', () => {
    console.log('datagrid ready triggered');
});</code></pre>

## Add Form Event

The add form event is triggered when the add/insert form is loaded.

<pre><code class="language-js">window.addEventListener('gcrud.form.add_form', () => {
    console.log('add_form triggered');
});</code></pre>

## Edit, Clone and Read Form

All the below events are very similar, and I guess they are self-explanatory. The only main
difference is that you are also getting some extra details from this event.
The most common info is the primary key value for the event.

<pre><code class="language-js">window.addEventListener('gcrud.form.edit_form', ({detail}) => {
    console.log('edit_form triggered', detail);
});

window.addEventListener('gcrud.form.clone_form', ({detail}) => {
    console.log('clone_form triggered', detail);
});

window.addEventListener('gcrud.form.read_form', ({detail}) => {
    console.log('read_form triggered', detail);
});</code></pre>





