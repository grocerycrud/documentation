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
| [cloneFields](/docs/clone-fields)  |The fields that will be visible to the end user for clone form.  |
| [columns](/docs/columns)  |Specifying the fields that the end user will see as the datagrid columns.  |
| [defaultOrdering](/docs/default-ordering)  |The default ordering that the datagrid will have before the user will press any button to order by column.  |
| [displayAs](/docs/display-as)  |Displaying the field name with a more readable label to the end-user.  |
| [editFields](/docs/edit-fields)  | The fields that will be visible to the end user for edit/update form.  |
| [fieldType](/docs/field-type)  | Changing the default field type from the database to fit to our needs.  |
| [fields](/docs/fields)  | This function is really just a facade function to call all the 4 functions at once: addFields, editFields, readFields and cloneFields.  |
| [getState](/docs/getState)  | Simply get the current state name as a string.  |
| [getStateInfo](/docs/get-state-info)  | Get all the information about the current state.  |
| [like](/docs/like)  | Filter the queries with a extra where LIKE statement. |
| [readFields](/docs/read-fields)  | The fields that will be visible when the end-user navigates to the view form.  |
| [render](/docs/render)  | This is the most basic function. In other words this means “make it work”.  |
| [requiredFields](/docs/required-fields)  | The most common validation. Checks is the field provided by the user is empty.  |
| [setActionButton](/docs/set-action-button)  | Adding extra action buttons to the rows of the datagrid.  |
| [setAdd](/docs/set-add)  | Setting the insert functionality. This function is rare to use as the default is already enabled.  |
| [setApiUrlPath](/docs/set-api-url-path)  | Change the default API URL path and instead use the provided URL. Useful when we use Routes. |
| [setClone](/docs/set-clone)  | Enabling the clone functionality for the datagrid. Clone is basically copying all the data to an insert form. |
| [setDelete](/docs/set-delete)  | Setting the delete functionality. This function is rare to use as the default is already enabled.. |
| [setEdit](/docs/set-edit)  | Setting the update functionality. This function is rare to use as the default is already enabled. |
| [setExport](/docs/set-export)  | Setting the export functionality. This function is rare to use as the default is already enabled. |
| [setLangString](/docs/set-lang-string)  | Change any handle of the translation. |
| [setLanguage](/docs/set-language)  | Set the language of the CRUD. All the languages that Grocery CRUD supports are listed at the [Languages Support](#languages-support) section. |
| [setModel](/docs/set-model)  | Changing the default model with a custom one. |
| [setPrimaryKey](/docs/set-primary-key)  | Set manually the primary key for a table. |
| [setPrint](/docs/set-print)  | Setting the print functionality. This function is rare to use as the default is already enabled. |
| [setRead](/docs/set-read)  | In order to enable the “View” button at your grid you will need to use the function setRead. The view of the form (read only) is false by default. |
| [setRelation](/docs/set-relation)  | This is the function that is used to connect two tables with a 1 to n (1:n) relation.  |
| [setRelationNtoN](/docs/set-relation-n-to-n)  | A connection for 3 tables with n-n relation (also known as n:n or m:n).  |
| [setRule](/docs/set-rule)   | The setRule function is used to set a validation rule at the backend. Same as Codeigniter 4 [setRule](https://codeigniter4.github.io/userguide/libraries/validation.html#setrule)  |
| [setSubject](/docs/set-subject)  | Set a subject title for all the CRUD operations for the current CRUD.  |
| [setTable](/docs/set-table)  | This is the database table that the developer will use to create the CRUD.  |
| [setTexteditor](/docs/set-texteditor)  |  Specifying the fields that will open with a texteditor (ckeditor). |
| [setTheme](/docs/set-theme)  |  The setTheme is used in order to change the default theme (flexigrid). |
| [uniqueFields](/docs/unique-fields)  |  Check if the data for the specified fields are unique. This is used at the insert and the update operation. |
| [unsetAdd](/docs/unset-add)  |  Removing the insert functionality at the current CRUD. |
| [unsetAddFields](/docs/unset-add-fields)  |  Unset (do not display) the specified fields for the insert form. |
| [unsetBackToDatagrid](/docs/unset-back-to-datagrid)  |  Unsets everything that has to do with buttons or links with go back to datagrid message |
| [unsetBootstrap](/docs/unset-bootstrap)  |  Do not load Bootstrap CSS. This is used when the Bootstrap CSS is already loaded at the template. |
| [unsetClone](/docs/unset-clone)  |  The method unsetClone is removing completely the Clone operation for the end-user. |
| [unsetCloneFields](/docs/unset-clone-fields)  |  Unset (do not display) the specified fields from the clone form. |
| [unsetColumns](/docs/unset-columns)   | Unset (do not display) the specified columns. |
| [unsetDelete](/docs/unset-delete)  | Unset (and do not display) the delete functionality (also unsetting the delete multiple functionality) |
| [unsetEdit](/docs/unset-edit)   | Removing the edit operation for the end-user (from the frontend and the backend) |
| [unsetEditFields](/docs/unset-edit-fields)   | Unset (do not display) the specified fields for the update form. |
| [unsetExport](/docs/unset-export)   | Removing the export functionality for the current CRUD. |
| [unsetFields](/docs/unset-fields)   | Unset (do not display) the specified fields for insert, update, clone and view form. This method is simply combining the methods: unsetAddFields, unsetEditFields, unsetCloneFields, unsetReadFields. |
| [unsetJquery](/docs/unset-jquery)   | Do not load jQuery. This is used when jQuery is already loaded at the template. |
| [unsetJqueryUi](/docs/unset-jquery-ui)   | Do not load jQuery UI. This is used when the jQuery UI (CSS and JS) is already loaded at the template. |
| [unsetOperations](/docs/unset-operations)  | Removing all the permissions for any operation (expect print and export) for the end-user. |
| [unsetPrint](/docs/unset-print)   | The method unsetPrint is removing completely the Print operation for the end-user. |
| [unsetRead](/docs/unset-read)   | The method unsetRead is removing completely the Read operation for the end-user. |
| [unsetReadFields](/docs/unset-read-fields)   | Unset (do not display) the specified fields for the view (read only) form. |
| [unsetTexteditor](/docs/unset-texteditor)  |  Unsets the texteditor for the selected fields. This function is really rare to use as by default there is not any load of the texteditor for optimising purposes. |
| [where](/docs/where)  | Filter the queries with an extra where statement. |[

### Callback Functionality

| Function name  | Small description |
| ------------- | ------------- |
| [callbackAddField](/docs/callback-add-field)   |  A callback that is used in case you need to create a custom field for the add form. |
| [callbackAfterDelete](/docs/callback-after-delete)   |  The callback that will be used right after the delete. |
| [callbackAfterInsert](/docs/callback-after-insert)   | The callback that will be used right after the insert of the data. |
| [callbackAfterUpdate](/docs/callback-after-update)   |  The callback that will be used right after the update of the data. |
| [callbackBeforeDelete](/docs/callback-before-delete)   |  The callback will be triggered before the delete functionality. |
| [callbackBeforeInsert](/docs/callback-before-insert)   |  The callback is used in cases we need to add or change data before the insert functionality. |
| [callbackBeforeUpdate](/docs/callback-before-update)   | The callback is used in cases we need to add or change data before the update functionality. |
| [callbackCloneField](/docs/callback-clone-field)   | A callback that is used in case you need to create a custom field for the clone form. |
| [callbackColumn](/docs/callback-column)   | The method callbackColumn is the transformation of the data for a column at the datagrid. |
| [callbackDelete](/docs/callback-delete)   | The basic usage of callbackDelete is when we want to replace the default delete functionality. |
| [callbackEditField](/docs/callback-edit-field)   | A callback that is used in case you need to create a custom field for the edit/update form. |
| [callbackInsert](/docs/callback-insert)   | The callback is used when we need to replace the default functionality of the insert. |
| [callbackReadField](/docs/callback-read-field)   | This is a callback in order to create a custom field at the read/view form. |
| [callbackUpdate](/docs/callback-update)   | The callback is used when we need to replace the default update functionality. |

