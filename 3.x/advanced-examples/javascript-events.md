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
events are not enabled by default on Grocery CRUD Enterprise version 3.

> Important note: To enable JavaScript events, please be aware that you need to set the configuration value 
> "publish_events" to `true`. If this value is left as the default `false`, the events will not be triggered,
> so make sure to update it accordingly.

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
    "gcrud.datagrid.page-change",
    "gcrud.datagrid.ready",
    "gcrud.filtering.form-submit",
    "gcrud.filtering.modal-open",
    "gcrud.form.add",
    "gcrud.form.add-load",
    "gcrud.form.edit",
    "gcrud.form.edit-load",
    "gcrud.form.insert",
    "gcrud.form.insert-success",
    "gcrud.form.modal-close",
    "gcrud.form.read",
    "gcrud.form.read-load",
    "gcrud.form.update",
    "gcrud.form.update-success",
    "gcrud.search-async.search",
]
</code></pre>

## Set Quick Search Value

<pre><code class="language-js">groceryCrudSetQuickSearchValue('columnName', 'columnValue')</code></pre>

The `groceryCrudSetQuickSearchValue` function is a JavaScript utility that allows you to programmatically 
set the value of a quick search field in Grocery CRUD Enterprise. 
This function is particularly useful when you need to implement custom filter buttons or other advanced filtering mechanisms.

<strong>Parameters:</strong>

<ul>
    <li><code>columnName</code>: The name of the column in the datagrid that you want to filter.</li>
    <li><code>columnValue</code>: The value that you want to set for the quick search field.</li>
</ul>

Here's an example of how to use the `groceryCrudSetQuickSearchValue` function:

An external button sets the quick search value for the `department_id` column to '3' upon being clicked:

<pre><code class="language-html">&lt;button id="setSearchValue"&gt;Marketing Department&lt;/button&gt;</code></pre>

And in the JavaScript file:

<pre><code class="language-js">document.getElementById('setSearchValue').addEventListener('click', () => {
    groceryCrudSetQuickSearchValue('department_id', '3');
});</code></pre>

In this example, the function sets the quick search value for the `department_id` column to '3' when the button with
the ID `setSearchValue` is clicked.

## Set Form Field Value

<pre><code class="language-js">groceryCrudSetFieldValue('fieldName', 'fieldValue')</code></pre>

`groceryCrudSetFieldValue` function is a JavaScript utility that allows you to set the value of a form field in 
Grocery CRUD Enterprise. This function is particularly useful when you need  to dynamically fill form fields 
in add or edit forms.

<strong>Parameters:</strong>

- `fieldName`: The name of the form field that you want to set.
- `fieldValue`: The value that you want to set for the form field.

<strong>Usage:</strong>

Here's an example of how to use the `groceryCrudSetFieldValue` function:

An external button sets the value for the `department_name` field to 'Marketing' upon being clicked:

<pre><code class="language-html">&lt;button id="setFieldValue"&gt;Marketing Department&lt;/button&gt;</code></pre>

And in the JavaScript file:

<pre><code class="language-js">document.getElementById('setFieldValue').addEventListener('click', () => {
    groceryCrudSetFieldValue('department_name', 'Marketing');
});</code></pre>

In this example, the function sets the value for the `department_name` field to 'Marketing' when the button 
with the ID `setFieldValue` is clicked.

## Use Redux Actions

There are cases that you would like to trigger some Redux actions directly from your JavaScript code.
In that case from version 3.1.15, or later you can use the `groceryCrudEmitReduxAction` function.

Below you can see some examples of how to use the `groceryCrudEmitReduxAction` function. Please keep in mind 
that for not all the actions are available to use. Currently, we have only the necessary actions, followed by the
below examples.

### Trigger Depended Fields

With the usage of <a href="/docs/set-dependent-relation" target="_blank">setDependentRelation</a> you can set a field 
to be depended on another field. If you would like to trigger the dependent field from your JavaScript code though, you
will notice that the dependency is not triggered automatically.
More specifically when we use `groceryCrudSetFieldValue` the dependency is not triggered. 
In that case you can use the `groceryCrudEmitReduxAction` function as follows:

<pre><code class="language-js">groceryCrudSetFieldValue('country', 'GR');
groceryCrudEmitReduxAction('depended-fields/update-dependency', {
  fieldName: 'country',
  fieldValue: 'GR'
});</code></pre>

### Trigger Insert Form

If you would like to trigger the add form from your JavaScript code, you can use the
`groceryCrudEmitReduxAction` function as follows:

<pre><code class="language-js">groceryCrudEmitReduxAction('form/add');</code></pre>

### Trigger Edit Form

For the edit form triggering, you can use the `groceryCrudEmitReduxAction` function as follows:

<pre><code class="language-js">groceryCrudEmitReduxAction('form/edit', {
    primaryKeyValue: '42'
});
</code></pre>

### Trigger Clone Form

With a similar way as the edit form, you can trigger the clone form as well.

<pre><code class="language-js">groceryCrudEmitReduxAction('form/clone', {
    primaryKeyValue: '42'
});</code></pre>

