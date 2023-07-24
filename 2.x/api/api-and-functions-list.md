---
id: api-and-functions-list
title: API and Functions list
description: You can find a full API list of all the functions of Grocery CRUD
canonical: docs/api-and-functions-list
previous: why-grocery-crud
next: getting-started
---

# API and Functions list

| Function name  | Small description |
| ------------- | ------------- |
| [addFields](/v2.x/docs/add-fields)  |The fields that will be visible to the end user for add/insert form.  |
| [cloneFields](/v2.x/docs/clone-fields)  |The fields that will be visible to the end user for clone form.  |
| [columns](/v2.x/docs/columns)  |Specifying the fields that the end user will see as the datagrid columns.  |
| [displayAs](/v2.x/docs/display-as)  |Displaying the field name with a more readable label to the end-user.  |
| [editFields](/v2.x/docs/edit-fields)  | The fields that will be visible to the end user for edit/update form.  |
| [fieldType](/v2.x/docs/field-type)  | Changing the default field type from the database to fit to our needs.  |
| [fields](/v2.x/docs/fields)  | This function is really just a facade function to call all the 4 functions at once: addFields, editFields, readFields and cloneFields.  |
| [getState](/v2.x/docs/getState)  | Simply get the current state name as a string.  |
| [getStateInfo](/v2.x/docs/get-state-info)  | Get all the information about the current state.  |
| [like](/v2.x/docs/like)  | Filter the queries with a extra where LIKE statement. |
| [readFields](/v2.x/docs/read-fields)  | The fields that will be visible when the end-user navigates to the view form.  |
| [render](/v2.x/docs/render)  | This is the most basic function. In other words this means “make it work”.  |
| [requiredFields](/v2.x/docs/required-fields)  | The most common validation. Checks is the field provided by the user is empty.  |
| [setActionButton](/v2.x/docs/set-action-button)  | Adding extra action buttons to the rows of the datagrid.  |
| [setAdd](/v2.x/docs/set-add)  | Setting the insert functionality. This function is rare to use as the default is already enabled.  |
| [setApiUrlPath](/v2.x/docs/set-api-url-path)  | Change the default API URL path and instead use the provided URL. Useful when we use Routes. |
| [setClone](/v2.x/docs/set-clone)  | Enabling the clone functionality for the datagrid. Clone is basically copying all the data to an insert form. |
| [setDelete](/v2.x/docs/set-delete)  | Set the delete functionality. This function is rare to use as the default is already enabled. |
| [setEdit](/v2.x/docs/set-edit)  | Set the update functionality. This function is rare to use as the default is already enabled. |
| [setExport](/v2.x/docs/set-export)  | Set the export functionality. This function is rare to use as the default is already enabled. |
| [setLangString](/v2.x/docs/set-lang-string)  | Change any handle of the translation. |
| [setLanguage](/v2.x/docs/set-language)  | Set the language of the CRUD. All the languages that Grocery CRUD supports are listed at the [Languages Support](#languages-support) section. |
| [setModel](/v2.x/docs/set-model)  | Changing the default model with a custom one. |
| [setPrimaryKey](/v2.x/docs/set-primary-key)  | Set manually the primary key for a table. |
| [setPrint](/v2.x/docs/set-print)  | Setting the print functionality. This function is rare to use as the default is already enabled. |
| [setRead](/v2.x/docs/set-read)  | In order to enable the “View” button at your grid you will need to use the function setRead. The view of the form (read only) is false by default. |
| [setRelation](/v2.x/docs/set-relation)  | This is the function that is used to connect two tables with a 1 to n (1:n) relation.  |
| [setRelationNtoN](/v2.x/docs/set-relation-n-to-n)  | A connection for 3 tables with n-n relation (also known as n:n or m:n).  |
| [setRule](/v2.x/docs/set-rule)   | The setRule function is used to set a validation rule at the backend. Same as Codeigniter 4 [setRule](https://codeigniter4.github.io/userguide/libraries/validation.html#setrule)  |
| [setSubject](/v2.x/docs/set-subject)  | Set a subject title for all the CRUD operations for the current CRUD.  |
| [setTable](/v2.x/docs/set-table)  | This is the database table that the developer will use to create the CRUD.  |
| [setTexteditor](/v2.x/docs/set-texteditor)  |  Specifying the fields that will open with a texteditor (ckeditor). |
| [setTheme](/v2.x/docs/set-theme)  |  The setTheme is used in order to change the default theme (flexigrid). |
| [uniqueFields](/v2.x/docs/unique-fields)  |  Check if the data for the specified fields are unique. This is used at the insert and the update operation. |
| [unsetAdd](/v2.x/docs/unset-add)  |  Removing the insert functionality at the current CRUD. |
| [unsetAddFields](/v2.x/docs/unset-add-fields)  |  Unset (do not display) the specified fields for the insert form. |
| unsetBackToDatagrid  |  Unsets everything that has to do with buttons or links with go back to datagrid message. Currently only available for community version. |
| [unsetBootstrap](/v2.x/docs/unset-bootstrap)  |  Do not load Bootstrap CSS. This is used when the Bootstrap CSS is already loaded at the template. |
| [unsetClone](/v2.x/docs/unset-clone)  |  The method unsetClone is removing completely the Clone operation for the end-user. |
| [unsetCloneFields](/v2.x/docs/unset-clone-fields)  |  Unset (do not display) the specified fields from the clone form. |
| [unsetColumns](/v2.x/docs/unset-columns)   | Unset (do not display) the specified columns. |
| [unsetDelete](/v2.x/docs/unset-delete)  | Unset and do not display the delete functionality Also unsetting the delete multiple functionality. |
| [unsetEdit](/v2.x/docs/unset-edit)   | Removing the edit operation for the end-user (from the frontend and the backend) |
| [unsetEditFields](/v2.x/docs/unset-edit-fields)   | Unset (do not display) the specified fields for the update form. |
| [unsetExport](/v2.x/docs/unset-export)   | Removing the export functionality for the current CRUD. |
| [unsetFields](/v2.x/docs/unset-fields)   | Unset (do not display) the specified fields for insert, update, clone and view form. This method is simply combining the methods: unsetAddFields, unsetEditFields, unsetCloneFields, unsetReadFields. |
| [unsetJquery](/v2.x/docs/unset-jquery)   | Do not load jQuery. This is used when jQuery is already loaded at the template. |
| [unsetJqueryUi](/v2.x/docs/unset-jquery-ui)   | Do not load jQuery UI. This is used when the jQuery UI (CSS and JS) is already loaded at the template. |
| [unsetOperations](/v2.x/docs/unset-operations)  | Removing all the permissions for any operation (expect print and export) for the end-user. |
| [unsetPrint](/v2.x/docs/unset-print)   | The method unsetPrint is removing completely the Print operation for the end-user. |
| [unsetRead](/v2.x/docs/unset-read)   | The method unsetRead is removing completely the Read operation for the end-user. |
| [unsetReadFields](/v2.x/docs/unset-read-fields)   | Unset (do not display) the specified fields for the view (read only) form. |
| [unsetTexteditor](/v2.x/docs/unset-texteditor)  |  Unsets the texteditor for the selected fields. This function is really rare to use as by default there is not any load of the texteditor for optimising purposes. |
| [where](/v2.x/docs/where)  | Filter the queries with an extra where statement. |

## Callback Functionality

| Function name  | Small description |
| ------------- | ------------- |
| [callbackAddField](/v2.x/docs/callback-add-field)   |  A callback that is used in case you need to create a custom field for the add form. |
| [callbackAfterDelete](/v2.x/docs/callback-after-delete)   |  The callback that will be used right after the delete. |
| [callbackAfterInsert](/v2.x/docs/callback-after-insert)   | The callback that will be used right after the insert of the data. |
| [callbackAfterUpdate](/v2.x/docs/callback-after-update)   |  The callback that will be used right after the update of the data. |
| [callbackBeforeDelete](/v2.x/docs/callback-before-delete)   |  The callback will be triggered before the delete functionality. |
| [callbackBeforeInsert](/v2.x/docs/callback-before-insert)   |  The callback is used in cases we need to add or change data before the insert functionality. |
| [callbackBeforeUpdate](/v2.x/docs/callback-before-update)   | The callback is used in cases we need to add or change data before the update functionality. |
| [callbackCloneField](/v2.x/docs/callback-clone-field)   | A callback that is used in case you need to create a custom field for the clone form. |
| [callbackColumn](/v2.x/docs/callback-column)   | The method callbackColumn is the transformation of the data for a column at the datagrid. |
| [callbackDelete](/v2.x/docs/callback-delete)   | The basic usage of callbackDelete is when we want to replace the default delete functionality. |
| [callbackEditField](/v2.x/docs/callback-edit-field)   | A callback that is used in case you need to create a custom field for the edit/update form. |
| [callbackInsert](/v2.x/docs/callback-insert)   | The callback is used when we need to replace the default functionality of the insert. |
| [callbackReadField](/v2.x/docs/callback-read-field)   | This is a callback in order to create a custom field at the read/view form. |
| [callbackUpdate](/v2.x/docs/callback-update)   | The callback is used when we need to replace the default update functionality. |

## Grocery CRUD Enterprise

| Function name  | Small description |
| ------------- | ------------- |
| [defaultOrdering](/v2.x/docs/default-ordering)  |The default ordering that the datagrid will have before the user will press any button to order by column.  |
| [setRules](/v2.x/docs/set-rules)  | setRules method combines multiple setRule methods into one.  |
| [setActionButtonMultiple](/v2.x/docs/set-action-button-multiple)  | Action button for multiple selections with checkboxes.  |
| [setSkin](/v2.x/docs/set-skin)  | Choose between two skins: Bootstrap v3 and Bootstrap V4.  |
| [unsetFilters](/v2.x/docs/unset-filters)  | Removing the "Filters" button from the datagrid. |
| [unsetSearchColumns](/v2.x/docs/unset-search-columns)  | Unset the search on the datagrid from quick column search and from filtering. |
| [unsetSettings](/v2.x/docs/unset-settings)  | Removing the "Settings" button from the datagrid. |
| [callbackAfterDeleteMultiple](/v2.x/docs/callback-after-delete-multiple)  | The callback that will be used right after the multiple delete functionality. |
| [callbackBeforeDeleteMultiple](/v2.x/docs/callback-before-delete-multiple)  | Similar functionality with callbackBeforeDelete it is just that this callback will be used for the delete multiple functionality. |
| [callbackDeleteMultiple](/v2.x/docs/callback-delete-multiple)  | Replaces the default multiple delete functionality with the callback specified. |
| [callbackReadForm](/v2.x/docs/callback-read-form)  | A callback to change the read data that will display at the read/view modal. |
| [callbackEditForm](/v2.x/docs/callback-edit-form)  | This callback is used in case we need to append, filter or change the data that are going to appear on the edit form. |
| [setDeleteMultiple](/v2.x/docs/set-delete-multiple)  | The setDeleteMultiple method is rarely used as the multiple delete functionality is enabled by default. |
| [unsetDeleteMultiple](/v2.x/docs/unset-delete-multiple)  | This function is used when you don't want the user to have the ability to batch remove too many records at once. Have in mind that the user can remove rows one by one. |
| [readOnlyAddFields](/v2.x/docs/read-only-add-fields)  | There are cases, that we need some fields to be read only but only to the add form modal.|
| [readOnlyCloneFields](/v2.x/docs/read-only-clone-fields)  | There are cases, that we need some fields to be read only but only to the clone form modal. |
| [readOnlyEditFields](/v2.x/docs/read-only-edit-fields)  | There are cases, that we need some fields to be read only but only to the edit form modal. |
| [readOnlyFields](/v2.x/docs/read-only-edit-fields)  | Specifying the fields that can't be edited and will only be viewed. |
| [callbackAfterUpload](/v2.x/docs/callback-after-upload)  | The callback that will be triggered right after the upload. |
| [callbackAfterUpload](/v2.x/docs/callback-after-upload)  | The callback that will be triggered right after the upload. |
| [callbackBeforeUpload](/v2.x/docs/callback-before-upload)  | The callback is used in cases we need to filter the uploaded data before the upload functionality. |
| [callbackUpload](/v2.x/docs/callback-upload)  | The callbackUpload is used when we need to replace the default upload functionality of Grocery CRUD Enterprise. |
| [setFieldUpload](/v2.x/docs/set-field-upload)  | There is a special type of field for uploading data or images and in order to trigger this type, you will need to use the setFieldUpload method. |
| setFieldUploadMultiple | Multiple Uploads functionality in one field with comma separated values. |
| [setCsrfTokenName](/v2.x/docs/set-csrf-token-name)  | Specify the token name for CSRF protection. |
| [setCsrfTokenValue](/v2.x/docs/set-csrf-token-value)  | Specify the token value for CSRF protection. |
| [setDatabaseSchema](/v2.x/docs/set-database-schema)  | Set the database schema (currently only tested on PostgresSQL databases). |
| [setDependentRelation](/v2.x/docs/set-dependent-relation)  | There are cases that dropdown list that was built from setRelation has dependencies between them. |
| [setSequenceName](/v2.x/docs/set-sequence-name)  | Postgres database is recognising the insert id with a sequence key. |
| [fieldTypeAddForm](/v2.x/docs/field-type-add-form)  | This function is used for cases that you need to change the field type but only for the add/insert form. |
| [fieldTypeCloneForm](/v2.x/docs/field-type-clone-form)  | This function is used for cases that you need to change the field type but only for the Clone form. |
| [fieldTypeColumn](/v2.x/docs/field-type-column)  | This function is used for cases that you need to change the field type but only for the datagrid column. |
| [fieldTypeEditForm](/v2.x/docs/field-type-edit-form)  | This function is used for cases that you need to change the field type but only for the edit/update form. |
| [fieldTypeFormFields](/v2.x/docs/field-type-form-fields)  | This function is really just a facade function to call all the functions of field-types for the form data. |
| [fieldTypeReadForm](/v2.x/docs/field-type-read-form)  | This function is used when you need to change the field type but only for the read/view form. |
| [setFieldBlob](/v2.x/docs/set-field-blob)  | Enable the upload functionality for Blob field type. |
| [setConfig](/v2.x/docs/set-config)  | Quickly set a configuration name that will be specific for your CRUD. |
| [setLanguagePath](/v2.x/docs/set-language-path)  | setLanguagePath is used in order to change the default path of the language folder. |
| [setThemePath](/v2.x/docs/set-theme-path)  | The method setThemePath is used when we want to change the folder of the theme. |