---
id: upgrade-notes
title: Upgrade Notes
description: Upgrade notes to update from version 2 to version 3 of Grocery CRUD Enterprise.
permalink: docs/upgrade-notes
previous:
next:
---

# Upgrade Draft Notes

## PHP changes
- setActionButtonMultiple `iconName` instead of `cssClassIcon`
- setActionButton  `iconName` instead of `cssClassIcon`
- new functions `unsetColumnsButton` and `setColumnsButton`
- new function `setMasterDetail`
- new function `unsetTools`
- new function `defaultColumnWidth`
- `setRelationDynamic` function which can is getting the data dynamically on search. Very useful for relational tables with big amount of data (e.g. more than 300 rows). The syntax is exactly the same as `setRelation` function

## PHP Configuration Changes
-   `hash_in_url` configuration is renamed to `url_history` . The URLs doesn’t follow the structure to have hashes into the end. Instead they have the slash as a normal URL behaviour. For example: `admin/customers/edit/123` instead of: `admin/customers#/edit/123`. Also the default value for `url_history` is now `false` instead of `true` that was before
- Introducing new configuration with name `publish_events` which allow more details to the frontend JavaScript actions.
- `skin` configuration is now used for ‘light’ and ‘dark’ skin and we use the `theme` for the configuration of the theming. For example: `’theme’ ⇒ ‘bootstrap-v5’,` `’skin’ ⇒ ‘dark’`
- `text_editor_type` is now removed.
-   PHP Configuration `date_format` is removed. no more date configuration from the backend (e.g. UK-date or US-date). The date will be transformed into the frontend from the language and with the locale (trying to guest the best possible mapping)

-   PHP Configuration `remember_quick_search` is removed as we always remember our search values into the frontend
- PHP Configuration `optimize_sql_queries` is now defaulting to false

## JavaScript Configuration Changes
-  `settings` object has slight changes on the callbacks. Mainly all the callback functions are getting as a first parameter an object instead of directly the values.

Examples:
```
actionButtons = [{ 
	iconName: 'smile',
	label: 'Smiley',
	onClick: function ({primaryKeyValue}) {
    console.log('Smiley is clicked with primary key:' + primaryKeyValue);  
  }
}];
```
```
{
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
```

You can see the full documentation of the new JavaScript settings __here__
- `settings` object of JavaScript has renamed some values. More specifically:
    -  `hashEvents` has been removed to keep the "one source of truth" configuration. We now have the `urlHistory` coming from PHP configurations only
    -  `openInModal` has been removed to keep the "one source of truth" configuration. We now have the `openInModal` coming from PHP configurations only
       The below callbacks has been removed:
- `onRowMount` is removed since it is only confusing the developement as it is not triggered when the primaryKeyValue is updated. Use `onRowUpdate` instead

New properties/callbacks:
- `actionButtonsMultiple` that work with the same way as `actionButtons` but it will only show up when we have selected rows. Example:

```
actionButtonsMultiple: [{
         iconName: 'smile',
         label: 'Smiley',
         onClick: function ({selectedIds}) {
             console.log(selectedIds);
         }
        }],
```


## JavaScript Events
All the events has changed and there will come from the redux action by replacing `/` with `.` starting with `gcrud`. For example the redux action type `datagrid/data-render` will be published as an event `gcrud.datagrid.data-render`

Also as now the published events are actual JavaScript events, all the payload will be available through the property name `detail` according to the latest  <a href="https://developer.mozilla.org/en-US/docs/Web/API/CustomEvent/CustomEvent" target="_blank">Custom Event</a> docs.

All the event names will be available through the documentation page of [JavaScript events](/v3.x/docs/javascript-events)  

We are still keeping some events as is as they are triggered as non redux action (e.g. to show that the datagrid is ready). For example: `gcrud.datagrid.ready` event

## Functionality Changes
We have changed the way that we upload. Now the upload is triggered after the submit form.

## Changes

-   Renaming package from `grocerycrud/enterprise` to `grocery-crud/enterprise`
-   We removed the functions: **`unsetBootstrap` , `unsetJquery`, `unsetJqueryUi`, `unsetReact` instead use the `unsetCssTheme`, `unsetCssIcons`, `unsetCssThirdParty`**
-   field type `time` is removed. Instead use `native_time`.
-   **`callbackAddField` first parameter has the add field value and not the field type as we had on version 2. More specifically we have: `function ($fieldVlue, $fieldName)`**
-   Removing jQuery loader `$('.gc-container').groceryCrud()` and instead having the function `groceryCrudLoader` with an html element as the first attribue and `settings` as a second `object` attribute

## PHP function changes

- `setActionButtonMultiple` has two more parameters that are now documented (previously they were experimental) `$idFieldQueryName = 'id'` and `$querySeparator = '?'`

## Documentation
- Explain about `native_fields` such as `native_time`, `native_date` and `native_datetime`
- Add two new segments examples for `setActionButtonMultiple`