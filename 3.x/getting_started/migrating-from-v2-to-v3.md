---
id: migrating-from-v2-to-v3
title: Migrating from v2 to v3
description: Upgrade notes to update from version 2 to version 3 for Grocery CRUD Enterprise.
canonical: v3.x/docs/migrating-from-v2-to-v3
previous:
next:
---

# Migrating from v2 to v3

<strong>Table of contents:</strong>

Changes in v3:

- [Package new name](#package-new-name)
- [Composer as the suggested way of installation](#composer-as-the-suggested-way-of-installation)
- [Change in Assets Folder Location](#change-in-assets-folder-location)
- [PHP Configuration Changes](#php-configuration-changes)
- [Library API Changes](#library-api-changes)
- [New Features](#new-features)
- [Functionality Changes](#functionality-changes)

<br/>

<strong>Changes in v3:</strong>

## Package new name

The biggest change that you will actually notice is the package new name for Composer. 

The package previously known as: 

<pre><code>grocerycrud/enterprise</code></pre> 

has been renamed to:

<pre><code>grocery-crud/enterprise</code></pre>

with the inclusion of a dash in the name.

## Composer as the suggested way of installation
The documentation now recommends using <a href="https://getcomposer.org/" target="_blank">Composer</a> as the primary method for installation.

In the past we were mainly suggesting to copy the library and the assets folders manually. Currently, we advise users to
use Composer as the preferred method instead. This is because composer is a popular dependency manager for PHP and is widely
used in the PHP community anyway!

It makes it easy to manage the package and its dependencies, ensuring that everything is
properly installed and configured for use. Using composer also makes it easier to update the package when new versions
are released, as it handles all the necessary dependencies and file management automatically.

## Change in Assets Folder Location

The assets folder for our installation packages has been moved from `public/grocery-crud` to `public/vendor/grocery-crud`. 
This change was inspired by the assets folder structure used by 
<a href="https://laravel.com/docs/9.x/packages#public-assets" target="_blank">Laravel Public Assets</a> and 
was made to provide a more familiar structure for the public assets folder.

## PHP Configuration Changes

Breaking changes:
- The argument `skin` is now used for ‘light’ and ‘dark’ skin, and we use the `theme` for the configuration of the 
theming. For example: `’theme’ ⇒ ‘bootstrap-v5’,` `’skin’ ⇒ ‘dark’`

Configuration arguments that has been <strong>removed</strong>:
- `hash_in_url` has been removed. Replaced by `url_history`.
- The configuration argument `text_editor_type` has been removed. 
We are currently using <a href='https://www.npmjs.com/package/react-quill' target='_blank'>React Quill</a> as our text 
editor. We made this change since we have plans for the future of being able to add your favorite text editor more 
easily and not to rely on pre-configured text editors.
-   PHP Configuration `date_format` is removed. no more date configuration from the backend (e.g. UK-date or US-date).
    The date will be transformed into the frontend from the language and with the locale by trying to guest the best
    possible mapping. We appreciate any feedback on date formatting as it is an area that we are always looking to improve.
- PHP Configuration `remember_quick_search` is removed as we always remember our search values into the frontend

New configuration arguments:
-  Introducing new configuration argument `url_history` instead of `hash_in_url` as the functionality of the URL has been modified.
The `url_history` is a boolean value that can be set to `true` or `false`.
The new URL is more user-friendly, such as `admin/customers/edit/123` instead of `admin/customers#/edit/123`. 
The default value for `url_history` is `false`, as this may require additional 
route configuration in the framework being used.

- Introducing new configuration with name `publish_events` which allow more details to the frontend JavaScript actions.
The default value for this configuration is `false` since this is used from more advanced users.

Configuration changes:
- PHP Configuration `optimize_sql_queries` is now defaulting to `false`. As currently this is used for relational 
queries, it is more important to have functionalities like ordering to work as expected and to set it to `true` 
exceptionally when you have big relational data. Also, since we are now providing the new function 
[setRelationDynamic](/v3.x/docs/set-relation-dynamic) we are able to optimize the queries for relational data anyway, so
we can safely assume that this configuration is needed only on exceptional cases.

## Library API changes

Functions that has been <strong>removed</strong>:
- We have removed the functions: `unsetBootstrap` , `unsetJquery`, `unsetJqueryUi`, `unsetReact`
instead use the `unsetCssTheme`, `unsetCssIcons`, `unsetCssThirdParty`. Documentation to be updated soon.

API changes:
- The function `setActionButtonMultiple` is using the argument `iconName` instead of `cssClassIcon`.
- The function `setActionButton` is using the argument  `iconName` instead of `cssClassIcon`.
- The function `setActionButtonMultiple` has two more parameters `$idFieldQueryName = 'id'` and `$querySeparator = '?'`.
Documentation to be updated soon.
- Field type `time` is removed. Instead, use `native_time`.
- **`callbackAddField` first parameter has the add field value and not the field type as we had on version 2. 
More specifically we have: `function ($fieldVlue, $fieldName)`**. Documentation to be updated soon.

## New features
- New function `setRelationDynamic` which is getting the data dynamically on search.
  Very useful for relational tables with big amount of data (e.g. more than 300 rows).
  The syntax is exactly the same as `setRelation` function. For more check the documentation about [setRelationDynamic](/v3.x/docs/set-relation-dynamic).
- New function `setMasterDetail`. For more check the documentation about [Master Detail](/v3.x/docs/set-master-detail)
- New function `unsetTools`.
- New function `defaultColumnWidth`. Documentation to be updated soon.
- New functions `unsetColumnsButton` and `setColumnsButton` since we now have a new button "Columns".
- Introducing new native field types which are using the browser native input types. New field types are `native_time`, 
`native_date` and `native_datetime`. Very useful for mobile devices.

## Functionality Changes
We have changed the way that we upload. Now the upload is triggered after the submit form and the UI is the standard 
native upload input.

====================================================================================================

The below documentation is yet to be improved and updated.

## JavaScript changes

-   Removing jQuery loader `$('.gc-container').groceryCrud()` and instead having the function `groceryCrudLoader` with 
a HTML element as the first attribue and `settings` as a second `object` attribute

As you may expect, since we have completely rewritten the JavaScript code, there are many changes to the 
JavaScript events:

## JavaScript Configuration Changes
-  `settings` object has slight changes on the callbacks. Mainly all the callback functions are getting as a first parameter an object instead of directly the values.

Examples:
<pre><code class="language-javascript">actionButtons = [{ 
	iconName: 'smile',
	label: 'Smiley',
	onClick: function ({primaryKeyValue}) {
        console.log('Smiley is clicked with primary key:' + primaryKeyValue);  
    }
}];
</code></pre>
and:
<pre><code class="language-javascript">{
        callbackBeforeInsert: function ({data}) {
            console.log('callback that is called right before the insert', {data});
        },
        callbackBeforeUpdate: function ({data, primaryKeyValue}) {
            console.log('callback that is called right before the update', 
               {data, primaryKeyValue}
            );
        },
        editFields: [ // works with $crud->callbackEditField
            {
                fieldName: 'contact_last_name',
                onMount: function onMount({fieldName}) {
                    console.log(fieldName, 'on mount!!');
                },
                onUnmount: function onUnmount({fieldName}) {
                    console.log(fieldName, 'on unmount');
                }
            }
        ],
}
</code></pre>

You can see the full documentation of the new JavaScript settings at [JavaScript Events](/v3.x/docs/javascript-events)
- `settings` object of JavaScript has renamed some values. More specifically:
    -  `hashEvents` has been removed to keep the "one source of truth" configuration. We now have the `urlHistory` coming from PHP configurations only
    -  `openInModal` has been removed to keep the "one source of truth" configuration. We now have the `openInModal` coming from PHP configurations only
       The below callbacks has been removed:
- `onRowMount` is removed since it is only confusing the developement as it is not triggered when the primaryKeyValue is updated. Use `onRowUpdate` instead

New properties/callbacks:
- `actionButtonsMultiple` that work with the same way as `actionButtons` but it will only show up when we have selected rows. Example:

<pre><code class="language-javascript">
actionButtonsMultiple: [{
         iconName: 'smile',
         label: 'Smiley',
         onClick: function ({selectedIds}) {
             console.log(selectedIds);
         }
}],
</code></pre>


## JavaScript Events
All the events has changed and there will come from the redux action by replacing `/` with `.` starting with `gcrud`. For example the redux action type `datagrid/data-render` will be published as an event `gcrud.datagrid.data-render`

Also as now the published events are actual JavaScript events, all the payload will be available through the property name `detail` according to the latest  <a href="https://developer.mozilla.org/en-US/docs/Web/API/CustomEvent/CustomEvent" target="_blank">Custom Event</a> docs.

All the event names will be available through the documentation page of [JavaScript events](/v3.x/docs/javascript-events)

We are still keeping some events as is as they are triggered as non redux action (e.g. to show that the datagrid is ready). For example: `gcrud.datagrid.ready` event
