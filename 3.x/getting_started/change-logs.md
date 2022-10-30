---
id: change-logs
title: Change Logs
description: All the changes for each new version in one page.
canonical: docs/change-logs
previous:
next:
---

# Change Logs

All the changes for each new version in one page for Grocery CRUD Community edition. 

<blockquote>Please have in mind that the change logs for Grocery CRUD Enterprise will be available only after the purchase.</blockquote>

v2.0.1
- <a href="https://github.com/scoumbourdis/grocery-crud-codeigniter-4/issues/38" target="_blank">#11</a> - Default language should be with uppercase at the first letter as it is causing issues on UNIX based systems

v2.0.0
- Creation of a stable release

v2.0.0-BETA.1
- <a href="https://github.com/scoumbourdis/grocery-crud-codeigniter-4/issues/38" target="_blank">#8</a>: Fixing issue with languages forced to be lowercase

v2.0.0-BETA
- <a href="https://github.com/scoumbourdis/grocery-crud-codeigniter-4/issues/38" target="_blank">#1</a>: Codeigniter 4 compatibility

<p>
v 1.6.3
</p><ul>
   <li><a href="https://github.com/scoumbourdis/grocery-crud/issues/38" target="_blank">#38</a>: Bug fix: required_fields doesn't work for relation_n_n fields</li>
   <li><a href="https://github.com/scoumbourdis/grocery-crud/pull/465" target="_blank">#465</a>: Translation for Spanish Uruguay by @mlopezcoria</li>
   <li><a href="https://github.com/scoumbourdis/grocery-crud/issues/468" target="_blank">#468</a>: Remove PHP 7.3 warnings</li>
   <li><a href="https://github.com/scoumbourdis/grocery-crud/issues/469" target="_blank">#469</a>: datatables theme - update table fails after delete</li>
   <li><a href="https://github.com/scoumbourdis/grocery-crud/pull/470" target="_blank">#470</a>: Update Polish translation by @tikky</li>
</ul>
<p></p>
<p>
	v 1.6.2
	</p><ul>
	    <li><a href="https://github.com/scoumbourdis/grocery-crud/pull/442" target="_blank">#442</a>: Searching in grid with value 0 is not working</li>
	    <li><a href="https://github.com/scoumbourdis/grocery-crud/pull/458" target="_blank">#458</a>: Updated Lithuanian language by @dgvirtual</li>
	    <li><a href="https://github.com/scoumbourdis/grocery-crud/pull/463" target="_blank">#463</a>: Updated Spanish language by @CarlosPinedaT</li>
	    <li>Security fix</li>
	</ul>
<p></p>
<p>
    v 1.6.1
    </p><ul>
         <li><a href="https://github.com/scoumbourdis/grocery-crud/issues/211" target="_blank">#441</a> Adding clone functionality - contribution from @portapipe</li>
    </ul>
<p></p>
<p>v 1.6.0
</p><ul>
    <li><a href="https://github.com/scoumbourdis/grocery-crud/issues/211" target="_blank">#211</a>: Bug if use where clause and try to "search all" the fields</li>
    <li><a href="https://github.com/scoumbourdis/grocery-crud/issues/432" target="_blank">#432</a>: Bootstrap Theme issues with filtering when we are using set_relation with multiple fields</li>
    <li><a href="https://github.com/scoumbourdis/grocery-crud/issues/353" target="_blank">#353</a>: Adding callback_read_field function</li>
    <li><a href="https://github.com/scoumbourdis/grocery-crud/issues/433" target="_blank">#433</a>: Preview click with fancybox to work the same across all the themes</li>
</ul>
<p></p>
<p>
v 1.5.9
</p><ul>
	<li><a href="https://github.com/scoumbourdis/grocery-crud/issues/420" target="_blank">#420</a>: set_relation with brackets is causing ambiguous column name when the field name exists at the basic table</li>
	<li><a href="https://github.com/scoumbourdis/grocery-crud/issues/420" target="_blank">#413</a>: Unexpected error when there are non english chars and a datetime field as column</li>
	<li><a href="https://github.com/scoumbourdis/grocery-crud/issues/420" target="_blank">#406</a>: Export button to work without the need of a popup window or new tab</li>
	<li>Clean-up redundant JavaScript load if it is not required.</li>
	<li>Remove Export as a flash plugin for security reasons and instead add a download link</li>
</ul>
<p></p>
<p>
v 1.5.8
</p><ul>
   <li><a href="https://github.com/scoumbourdis/grocery-crud/pull/382" target="_blank">#382</a>: Adding custom error message for set_rules()</li>
    <li>Two new language strings for the multiple delete confirmation</li>
    <li><a href="https://github.com/scoumbourdis/grocery-crud/issues/388" target="_blank">#388</a>: Chosen select have 100% width at flexigrid theme</li>
</ul>
<p></p>
<p>
v 1.5.7
</p><ul>
   <li><a href="https://github.com/scoumbourdis/grocery-crud/issues/331" target="_blank">#331</a> - Have a configurable XSS clean option to prevent XSS attacks</li>
   <li><a href="https://github.com/scoumbourdis/grocery-crud/issues/370" target="_blank">#370</a> - A faster way to calculate the totals</li>
</ul>
<p></p>
<p>v 1.5.6
   </p><ul>
       <li>Unset bootstrap with more CSS unsets</li>
       <li>Languages updates (Portuguese, Italian, Spanish)</li>
       <li><a href="https://github.com/scoumbourdis/grocery-crud/issues/367" target="_blank">#367</a> - Missing translation for Search {column_name}</li>
   </ul>
<p></p>
<p>v 1.5.5
   </p><ul>
       <li>Add Croatian language - translated by: Siniša Dragičević Martinčić</li>
       <li>Small CSS fixes: Datetime and date picker was overflowing in some languages</li>
       <li>Removing uniform.js</li>
   </ul>
<p></p>
<p>v 1.5.4
    </p><ul>
         <li>Changes for compatibility without the need of jQuery Migrate.</li>
   </ul>
<p></p>
<p>v 1.5.3
    </p><ul>
         <li><a href="https://github.com/scoumbourdis/grocery-crud/issues/141" target="_blank">#141</a> - Max length for decimal numbers (pull request from @dodge107)</li>
         <li><a href="https://github.com/scoumbourdis/grocery-crud/issues/335" target="_blank">#335</a> - Unable to locate the model you have specified: grocery_crud_model (pull request: #336 from @P8H)</li>
   </ul>
<p></p>

<p>v 1.5.2
	</p><ul>
		<li>Add Lithuanian language - translated by alex@gnosi.lt</li>
   		<li>Fix compatibility issues with Codeigniter 3</li>
   		<li>Add "More" lang string for the datagrid listing</li>
	</ul>
<p></p>

<p>v 1.5.1
</p><ul>
	<li><a href="https://github.com/scoumbourdis/grocery-crud/pull/290" target="_blank">#290</a> - Added functionality to define upload file types per field (pull request from @syrys)</li>
	<li><a href="https://github.com/scoumbourdis/grocery-crud/pull/305" target="_blank">#305</a> - Update french.php and add translation for date format (pull request from @bvrignaud)</li>
	<li>New function unset_bootstrap that removes JS and CSS of the new bootstrap theme</li>
</ul>
<p></p>
<p>v 1.5.0
</p><ul>
	<li>#211 - Bug if use where clause.</li>
	<li>#197 - Properly sanitise filenames for uploads.</li>
	<li>#237 - Set Timepicker to 24 hour format.</li>
	<li>#294 - Javascript bug with set_subject().</li>
	<li>Add a new method unset_view that is just an alias to unset_read method.</li>
	<li>Multiple delete fields for flexibility for future themes.</li>
	<li>Fixing the bug of jquery form plugin with returning the textarea as required.</li>
	<li>Add $subject_plural as a second parameter to the set_subject method.</li>
	<li>Multiple search fields for flexibility for future themes:
		<ul>
			<li>Multiple simple search</li>
			<li>Multiple relation search</li>
			<li>Multiple relation_n_n search</li>
		</ul>
	</li>
	<li>More configuration preferences
		<ul>
			<li>Setting environment (e.g. production)</li>
			<li>Setting default theme (e.g. datatables)</li>
		</ul>
	</li>
	<li>Add 2 new functions:
		<ul>
			<li>unset_read_fields</li>
			<li>set_read_fields</li>
		</ul>
	</li>
</ul>

<p></p>

<p>v 1.4.1
</p><ul>
	<li>#231 - Read page not showing relations.</li>
	<li>#233 - File upload uniqueid not unique.</li>
</ul><p></p>
<p>v 1.4.0
</p><ul>
	<li>#170 - Problem with more than one date inputs at the dialog.</li>
	<li>#148 - New theme twitter-bootstrap [BETA]</li>
	<li>#150 - Optimising the SELECT statement for counting rows.</li>
	<li>#144 - Unique fields as new functionality for unique fields in the database.</li>
	<li>#129 - Small bug uploading images.</li>
	<li>#142 - Extras doesn't work properly when the field doesn't exist in the database</li>
	<li>#158 - New method name set_crud_url_path. This method is useful when the path is not specified correctly.</li>
	<li>#163 - Custom field type label for true_false. Like hidden, enum and set.</li>
	<li>Noty Jquery Plugin to load when you delete a record.</li>
	<li>Upgrading Jquery to Jquery 1.10.2</li>
	<li>Multiple grids in one page.</li>
	<li>New language: Catalan.</li>
	<li>Add "view" as new action.</li>
	<li>Small bug fixes:
		<ul>
			<li>#165 - add_action "url_has_http" issue</li>
			<li>#166 - Improved file upload error handling</li>
			<li>#167 - add_action method in Twitter_Bootstrap theme, doesn't update the dropdown properly</li>
		</ul>
	</li>
</ul>
<p></p>
<p>
v 1.3.3
</p><ul>
<li>#102 - Unsigned field type bug.</li>
<li>#103 - Multiple columns search filtering at datatables.</li>
<li>#113 - Relation n_n missing when unset field.</li>
<li>Adding languages: Bengali, Slovak, Korean.</li>
<li>Stop supporting Codeigniter version 2.1.1 with ugly workarounds.</li>
<li>Use fancybox for previewing the thumbnails at the list page.</li>
<li>Transliteration characters for uploaded files.</li>
<li>Updating jQuery Plugins and third party add-ons:
	<ul>
		<li>Updating jQuery to version 1.8.2</li>
		<li>jQuery UI Library to v1.9.0.</li>
		<li>Timepicker Addon for jQuery UI Datepicker to v1.0.5.</li>
		<li>jQuery UI Multiselect and adding localisation files for it.</li>
		<li>jQuery Numeric plugin to v1.3.1.</li>
		<li>jQuery Chosen plugin to v0.9.8.</li>
		<li>Updating CKEditor to v3.6.5 with minimum setup.</li>
		<li>Updating TinyMCE to v3.5.7. </li>
	</ul>
</li>
</ul>
<p></p>
<p>
v 1.3.2
</p><ul>
	<li>#98 - Add more field types.
		<ul>
			<li>Dropdown field type.</li>
			<li>Multiselect field type.</li>
		</ul>
	</li>
	<li>#101 - Size of a request header field exceeds server limit for datatables.</li>
	<li>#97 - Add new method and functionality - unset_jquery_ui</li>
	<li>#46 - Supporting IE7.</li>
	<li>#95 - Export and print doesn't remove the html tags.</li>
</ul>
<p></p>
<p>
v 1.3.1
</p><ul>
	<li>Updating "Export","Print" and "Minimise/Maximise" lang strings</li>
	<li>Renewing to the latest tinymce version</li>
	<li>Jquery version 1.8.1</li>
	<li>Fixing small bugs</li>
</ul>
<p></p>
<p>v 1.3
</p><ul>
	<li>#73 - Jquery version 1.8.0</li>
	<li>#88 - Where clause in set_relation_n_n.</li>
	<li>#87 - Templating system to the  set_relation_n_n method.</li>
	<li>#82 - Have a thumbnail after uploading an image.</li>
	<li>Adding Czech Language.</li>
	<li>Internationalisation for datepicker ui and datetime picker.</li>
	<li>#86 - Print functionality to both flexigrid and datatables theme.</li>
	<li>#85 - Export functionality to both flexigrid and datatables theme.</li>
	<li>Print functionality to datatables theme.</li>
	<li>Having CKEditor as the default texteditor for grocery CRUD.</li>
	<li>Adding Markitup texteditor. Really useful editor for developers.</li>
	<li>#68 - set_relation doesn't work as expected when the third field (title name) is the same on two or more set_relation methods.</li>
	<li>#80 - method order_by doesn't work correctly on datatables theme.</li>
	<li>More configuration values:
		<ul>
<li>Choose text-editor between 'ckeditor','tinymce' or 'markitup'.</li>
<li>Choose text-editor type between 'minimal' or 'full'.</li>
<li>Character limiter at the columns of the list page.</li>
</ul>
</li>
</ul>
<p></p>
<p>
v 1.2.3
</p><ul>
	<li>Compatible with Codeigniter version 2.1.1</li>
	<li>Adding Hungarian language.</li>
	<li>Adding new method: field_type. For now it is just an alias to the change_field_type method.</li>
	<li>#49 - Adding new method: set_primary_key.</li>
	<li>#27 - Adding value to enum and set of the change_field_type method.</li>
	<li>#44 - Changing the date format at the list table. For example the 10 Jan 2003 has to be 10/01/2003.</li>
	<li>#56 - Field type true_false now uses default value.</li>
	<li>#42 - Insert ids to all the inputs for easy Javascript changes.</li>
	<li>
		Bug fixes:
		<ul>
			<li>#30 - Change field type doesn't work if the field is not at the table.</li>
			<li>#38 - required_field doesn't work for relation_n_n fields.</li>
		</ul>		
	</li>
</ul>
<p></p>
<p>
v 1.2.2
</p><ul>
	<li>Adding Dutch language.</li>
	<li>Adding a new method "unset_back_to_list".  Unsets everything that has to do with buttons or links with go back to list message.</li>
	<li>#28 - Change the hardcoded JavaScripts and CSS with variables.</li>
	<li>#25 - Adding a new method "unset_list".  Unsets the first list and the ajax_list and gives an exception error for the user that tries to access it.</li>
	<li>Adding a new button/feature "save and go back to list". When a user press the button "save and go back to list" it is automatically redirect you to the list page when a successful save is done. </li>
	<li>Adding the default_per_page at the config file. This specifies the first visit per page that a user should see at the list page. For example 25 rows per page.</li>
	<li>#13 - The list search and ordering is not working with the n-n relation columns.</li>
	<li>Small bug fixes:
<ul>
		<li>#20 - Pressing tab and enter after adding a date or a datetime field it clears the date.</li>
		<li>#21 - By default the texteditor transform the utf8 to html entities.</li>
		<li>#22 - Doesn't recognise that a tinyint 1 or int 1 can just take a numeric value more than 1.</li>
	<li>#23 - When we use $crud-&gt;where() method it doesn't work as expected with the flexigrid search.</li>
</ul>
</li>
</ul>
<p></p>
<p>
v 1.2.1.1
</p><ul>
	<li>#18 - Returning $this to all the callbacks methods.</li>
	<li>"set" type doesn't work properly.</li>
</ul>
<p></p>
<p>v.1.2.1
</p><ul>
	<li>Adding languages: Afrikaans, Danish, Japanese, Romanian.</li>
	<li>Adding 3 new methods. unset_fields, unset_add_fields and unset_edit_fields.</li>
	<li>Renewing Javascripts: tinymce.</li>
	<li>Issue #14 - In firefox browser if you add more than one textarea. Only the last textarea works properly.</li>
	<li>Issue #16 - Flexigrid's Search string get garbled with multibyte string.</li>
	<li>Adding the "set" field type.</li>
	<li>Adding the "readonly" field type.</li>
	<li>Adding lang strings: "set_relation_title", "list_record", "form_inactive", "form_active";</li>
</ul>
<p></p>
<p>v.1.2
</p><ul>
	<li>Adding languages: Arabic, Chinese, European Portuguese, German , Persian, Polish, Indonesian, Turkish, Ukrainian and Vietnamese.</li>
	<li>Adding date format to the auto date fields. The format can be dd/mm/yyyy or mm/dd/yyyy or the old-one yyyy-mm-dd.</li>
	<li>Adding date-time format to the auto date-time fields. The format is chosen by the default date format (uk-date , us-date or sql-date).</li>
	<li>Adding a new uploader. Works with the most common browsers. Internet Explorer 8+, Mozilla Firefox, Google Chrome, Opera, Safari.</li>
	<li>Changing the interface of the form inputs. Now all the text inputs looks like bootstrap's inputs.</li>
	<li>Adding a where clause at the 4th argument to the simple set_relation method.</li>
	<li>Adding order by clause at the 5th argument to the simple set_relation method.</li>
	<li>Adding 3 new callbcaks, callback_upload, callback_before_upload, callback_after_upload.</li>
	<li>BUG fix - unset_jquery function now works properly.</li>
	<li>BUG fix #9 (The form's clear functionality don't work properly after the insert). </li>
	<li>RENAMING METHODS:
		<ul>
			<li>callback_escape_insert to callback_insert</li>
			<li>callback_escape_update to callback_update</li>
			<li>callback_escape_delete to callback_delete</li>
		</ul>
	</li>
	<li>RENAMING CLASSES:
		<ul>
			<li>grocery_Model to grocery_CRUD_Model	</li>
			<li>grocery_Field_Types to grocery_CRUD_Field_Types</li>
			<li>grocery_Form_validation to grocery_CRUD_Form_validation</li>
			<li>grocery_Layout to grocery_CRUD_Layout</li>
			<li>grocery_States to grocery_CRUD_States</li>
		</ul>
	</li>
</ul>
<p></p>
<p>v.1.1.8
</p><ul>
	<li>Add new jquery version 1.7.1</li>
	<li>Changing the drop-down list of the set_relation. Now the drop-down list has unique design for all the browsers, is searchable and also can be empty.</li>
	<li>Changing the layout or relation n-n (only without the ordering field). The new one, is much more user friendly and easier to handle lot of data. </li>

	<li>Adding languages: Italian, Russian.</li>
	<li>Small BUG fixes: <br>
		- Auto-recognize enum fields for CI 2.1<br>
		- Don't print "&nbsp;" if a value is empty, is useless<br>
		- Smal but important CSS Fixes.<br>
		- #7 set_relation BUG conflict when a field name appears twice.<br>

	</li>
	<li>Manipulating NULL data. Automatically add NULL to a NULL-able field when it's empty.</li>
</ul>
<p></p>
<p>v.1.1.7
</p><ul>
	<li>Multilingual functionality, adding languages: Bulgarian, French, Portuguese, Spanish,  Thai.</li>
	<li>Fixing issue #3, replace mysql_escape_string() with str_replace. This function has been DEPRECATED as of PHP 5.3.0.</li>
	<li>Fixing issue #5, set_relation with multiple fields don't work with NULL-able fields.</li>
	<li>Fixing issue #6, unique_hash issue (not unique when having same method name in 2 diff. controllers).</li>
	<li>Changing license. Grocery CRUD is released with dual licensing, using the <a href="https://github.com/scoumbourdis/grocery-crud/blob/master/license-gpl3.txt" target="_blank">GPL v3</a> and the <a href="https://github.com/scoumbourdis/grocery-crud/blob/master/license-mit.txt" target="_blank">MIT license</a>. For more about the licenses read : <a href="https://github.com/scoumbourdis/grocery-crud/blob/master/license-grocery-crud.txt" target="_blank">Grocery CRUD licence</a>.</li>
</ul>
<p></p>
<p>v.1.1.6
</p><ul>
	<li>New feature: Multilingual functionallity.</li>
	<li>Remember the search text and the field name at the list that user had insert.</li>
	<li>Method set_relation - New feature to add more than one fields to the title of the related table.</li>
	<li>Adding Timestamp as an automatic date and time field.</li>
	<li>Change the business logic of adding js and css files. This is really useful for a FUTURE feature with multiple tables in the same view.</li>
	<li>A temporary solution for the search for All that have a relation_n_n.</li>
	<li>Small Bug fix - adding tinyint as a type to autogenerate the true_false type (active-inactive) for tinyint at CI 2.1</li>
	<li>Fixing issue #1 - flexigrid width was always 960px. Now has always 100% width.</li>
</ul>
<p></p>
<p>
v.1.1.4
</p><ul>
	<li>Bug Fix - When you have unset edit and unset delete in your actions and also you have insert one or more add_action, the column Actions disappeared.</li>
	<li>Adding a new field type named "password". This is a simple transformation of the field input from text to password and it hides the password from the list grid.</li>
	<li>Changing state name insert and update to... "insert" and "update" and not "add" and "edit" that was till this revision.</li>
	<li>Fully compatible with codeigniter 2.1 - Changing the library of CI_Form_Validation and adding it into the library of grocery CRUD for stability.</li>
</ul>	
<p></p>
<p>
v.1.1.3
</p><ul>
	<li>Changing the functionality of the private method _theme_view. Now it's not dependent with the Loader of codeigniter.So every template controller, HMVC, e.t.c. can work well with grocery CRUD now.</li>
	<li>Changing the library core and make it more minimal and more powerful.</li>
	<li>New method unset_jquery. Very useful, if you already have the jquery library at your basic template.This is good to avoid jquery conflicts.</li>
	<li>BUG fix. No more conflicts between flexigrid tables. There was a cookie conflict between different lists.</li>
	<li>BUG fix. The set relation now works if you add the same table name twice.</li>
	<li>Renaming the folder public to assets.</li>
	<li>Grocery CRUD is now ready to be a spark.</li>
	<li>Changing the functionality and the javascript of the uploader. There is no need to have $config['enable_query_strings'] set to true anymore.</li>
</ul>
<p></p>
<p>v.1.1.2
</p><ul>
	<li>Renaming the label "Tools" to "Actions".</li>
	<li>Creation of new field type : "hidden" to add hidden fields. You can also add a value to the hidden field.</li>
	<li>Updating Javascripts: datatables, file_uploader.</li>
	<li>Disable sorting of the row "Actions" on datatables theme and fix the actions hover on paging that didn't work.</li>
	<li>Adding new feature/function add_action. Adds icons and urls for custom "actions".</li>
	<li>Adding .htaccess files to the views of themes for security reasons.</li>
</ul>
<p></p>
<p>v.1.1
	</p><ul>
		<li>Bug Fix - Datetime picker now works fine to an empty input. It also works fine to the add operation.</li>
		<li>When the edit and the delete is unset then disappear the column Tools.</li>
		<li>The default library/model is not in a third party but has been moved in the main codeigniter foldering for better functionality and to use it in both CI 1.7.x and CI 2.0.x .</li>
		<li>Delete the grocery Exceptions Library. Everyone can create his own exception library. It was just an example.</li>
		<li>Add new jquery version 1.6.2 and renewing some plugins.</li>
		<li>Remove php short tags.</li>
		<li>No direct script access allowed on the views.</li>
		<li>Renaming function set_relation_1_n to set_relation_n_n. The functionality has not change.</li>
		<li>Removing the libraries MY_Output.php and MY_Loader.php from the core folder.</li>
		<li>Removing the folder template. The template was just an example and confused lot of people.</li>
		<li>Fully compatible with Codeigniter versions 1.7.x , 2.0.0 - 2.0.3.</li>
		<li>Creation of new field type : "invisible". Very useful if you use callbacks.</li>
	</ul>
<p></p>                





