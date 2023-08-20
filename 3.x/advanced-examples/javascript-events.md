---
id: javascript-events
title: JavaScript Events
description: Example for JavaScript events that Grocery CRUD uses for custom development through JavaScript.
canonical: docs/javascript-events
previous: 
next:
---

# JavaScript Events

Grocery CRUD Enterprise is dispatching some events on some actions. For performance and security reasons the external
events are not enabled by default on Grocery CRUD Enterprise version 3. In order to enable it you will need to change 
the configuration value `publish_events` to `true`. 

## Datagrid Update Event

"Datagrid Ready" event is triggered when the first load of the datagrid has been completed.
With simple words all the data load has been completed, and you are ready to add your custom
stuff in the datagrid. Please keep in mind that this event will triggerred only once 
per refresh and **not** in every datagrid refresh/update.

<pre><code class="language-js">window.addEventListener('gcrud.datagrid.ready', () => {
    console.log('datagrid ready triggered');
});</code></pre>

## Add Form Event

The add form event is triggered when the add/insert form is loaded.

<pre><code class="language-js">window.addEventListener('gcrud.form.add', () => {
    console.log('Add Form triggered');
});</code></pre>

## Edit, Clone and Read Form

All the below events are very similar, and I guess they are self-explanatory. The only main
difference is that you are also getting some extra details from this event.
The most common info is the primary key value for the event.

<pre><code class="language-js">window.addEventListener('gcrud.form.edit', ({detail}) => {
    console.log('edit form triggered', detail);
});

window.addEventListener('gcrud.form.clone', ({detail}) => {
    console.log('clone form triggered', detail);
});

window.addEventListener('gcrud.form.read', ({detail}) => {
    console.log('read form triggered', detail);
});</code></pre>

## All the events that we have so far

All the events that we have so far are listed below ordered alphabetically for the latest current version of Grocery CRUD Enterprise.

<pre><code class="language-js">
[
    "gcrud.column-width.change-width",
    "gcrud.column-width.reset-column-width",
    "gcrud.columns.modal",
    "gcrud.columns.modal-close",
    "gcrud.columns.ordering-change",
    "gcrud.columns.reset-ordering",
    "gcrud.columns.toggle-visible-column",
    "gcrud.configuration.init",
    "gcrud.configuration.init-fetch",
    "gcrud.configuration.main-configuration",
    "gcrud.datagrid.clear-cache",
    "gcrud.datagrid.clear-filtering",
    "gcrud.datagrid.data-fetch",
    "gcrud.datagrid.data-render",
    "gcrud.datagrid.ordering-reset",
    "gcrud.datagrid.ready",
    "gcrud.filtering.form-submit",
    "gcrud.filtering.modal-open",
    "gcrud.form.edit",
    "gcrud.form.edit-load",
    "gcrud.form.modal-close",
    "gcrud.form.read",
    "gcrud.form.read-load",
    "gcrud.form.update",
    "gcrud.form.update-success",
    "gcrud.search-async.search",
]
</code></pre>



