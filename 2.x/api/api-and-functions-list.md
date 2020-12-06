---
id: api-and-functions-list
title: API and Functions list
permalink: docs/api-and-functions-list
previous: why-grocery-crud
next: basic-example
---

# API and Functions list

| Function name  | Small description |
| ------------- | ------------- |
| [addFields](/docs/add-fields)  |The fields that will be visible to the end user for add/insert form.  |
| cloneFields   |The fields that will be visible to the end user for clone form.  |
| columns   |Specifying the fields that the end user will see as the datagrid columns.  |
| defaultOrdering   |The default ordering that the datagrid will have before the user will press any button to order by column.  |
| displayAs   |Displaying the field name with a more readable label to the end-user.  |
| editFields   | The fields that will be visible to the end user for edit/update form.  |
| fieldType   | Changing the default field type from the database to fit to our needs.  |
| fields   | This function is really just a facade function to call all the 4 functions at once: addFields, editFields, readFields and cloneFields.  |
| getState   | Simply get the current state name as a string.  |
| getStateInfo   | Get all the information about the current state.  |
| like   | Filter the queries with a extra where LIKE statement. |
| readFields   | The fields that will be visible when the end-user navigates to the view form.  |
| render   | This is the most basic function. In other words this means “make it work”.  |
| requiredFields   | The most common validation. Checks is the field provided by the user is empty.  |
| setActionButton   | Adding extra action buttons to the rows of the datagrid.  |
| setAdd   | Setting the insert functionality. This function is rare to use as the default is already enabled.  |
| setApiUrlPath   | Change the default API URL path and instead use the provided URL. Useful when we use Routes. |
| setClone   | Enabling the clone functionality for the datagrid. Clone is basically copying all the data to an insert form. |
| setDelete   | Setting the delete functionality. This function is rare to use as the default is already enabled.. |
| setEdit   | Setting the update functionality. This function is rare to use as the default is already enabled. |
| setExport   | Setting the export functionality. This function is rare to use as the default is already enabled. |
| setLangString   | Change any handle of the translation. |
| setLanguage   | Set the language of the CRUD. All the languages that Grocery CRUD supports are listed at the [Languages Support](#languages-support) section. |
| setModel   | Changing the default model with a custom one. |
| setPrimaryKey   | Set manually the primary key for a table. |
| setPrint   | Setting the print functionality. This function is rare to use as the default is already enabled. |
| setRead   | In order to enable the “View” button at your grid you will need to use the function setRead. The view of the form (read only) is false by default. |
| setRelation   | This is the function that is used to connect two tables with a 1 to n (1:n) relation.  |
| setRelationNtoN   | A connection for 3 tables with n-n relation (also known as n:n or m:n).  |
| setRule  | The setRule function is used to set a validation rule at the backend. Same as Codeigniter 4 [setRule](https://codeigniter4.github.io/userguide/libraries/validation.html#setrule)  |
| setSubject   | Set a subject title for all the CRUD operations for the current CRUD.  |
| setTable   | This is the database table that the developer will use to create the CRUD.  |
| setTexteditor   |  Specifying the fields that will open with a texteditor (ckeditor). |
| setTheme   |  The setTheme is used in order to change the default theme (flexigrid). |
| uniqueFields   |  Check if the data for the specified fields are unique. This is used at the insert and the update operation. |
| unsetAdd   |  Removing the insert functionality at the current CRUD. |
| unsetAddFields   |  Unset (do not display) the specified fields for the insert form. |
| unsetBackToDatagrid   |  Unsets everything that has to do with buttons or links with go back to datagrid message |
| unsetBootstrap   |  Do not load Bootstrap CSS. This is used when the Bootstrap CSS is already loaded at the template. |
| unsetClone   |  The method unsetClone is removing completely the Clone operation for the end-user. |
| unsetCloneFields   |  Unset (do not display) the specified fields from the clone form. |
| unsetColumns  | Unset (do not display) the specified columns. |
| unsetDelete | Unset (and do not display) the delete functionality (also unsetting the delete multiple functionality) |
| unsetEdit  | Removing the edit operation for the end-user (from the frontend and the backend) |
| unsetEditFields  | Unset (do not display) the specified fields for the update form. |
| unsetExport  | Removing the export functionality for the current CRUD. |
| unsetFields  | Unset (do not display) the specified fields for insert, update, clone and view form. This method is simply combining the methods: unsetAddFields, unsetEditFields, unsetCloneFields, unsetReadFields. |
| unsetJquery  | Do not load jQuery. This is used when jQuery is already loaded at the template. |
| unsetJqueryUi  | Do not load jQuery UI. This is used when the jQuery UI (CSS and JS) is already loaded at the template. |
| unsetOperations  | Removing all the permissions for any operation (expect print and export) for the end-user. |
| unsetPrint  | The method unsetPrint is removing completely the Print operation for the end-user. |
| unsetRead  | The method unsetRead is removing completely the Read operation for the end-user. |
| unsetReadFields  | Unset (do not display) the specified fields for the view (read only) form. |
| unsetTexteditor   |  Unsets the texteditor for the selected fields. This function is really rare to use as by default there is not any load of the texteditor for optimising purposes. |
| where   | Filter the queries with an extra where statement. |

### Callback Functionality

| Function name  | Small description |
| ------------- | ------------- |
| callbackAddField   |  A callback that is used in case you need to create a custom field for the add form. |
| callbackAfterDelete   |  The callback that will be used right after the delete. |
| callbackAfterInsert   | The callback that will be used right after the insert of the data. |
| callbackAfterUpdate   |  The callback that will be used right after the update of the data. |
| callbackBeforeDelete   |  The callback will be triggered before the delete functionality. |
| callbackBeforeInsert   |  The callback is used in cases we need to add or change data before the insert functionality. |
| callbackBeforeUpdate   | The callback is used in cases we need to add or change data before the update functionality. |
| callbackCloneField   | A callback that is used in case you need to create a custom field for the clone form. |
| callbackColumn   | The method callbackColumn is the transformation of the data for a column at the datagrid. |
| callbackDelete   | The basic usage of callbackDelete is when we want to replace the default delete functionality. |
| callbackEditField   | A callback that is used in case you need to create a custom field for the edit/update form. |
| callbackInsert   | The callback is used when we need to replace the default functionality of the insert. |
| callbackReadField   | This is a callback in order to create a custom field at the read/view form. |
| callbackUpdate   | The callback is used when we need to replace the default update functionality. |

