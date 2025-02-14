---
id: field-type
title: fieldType
description: Changing the default field type from the database to fit to our needs. 
canonical: docs/field-type
previous:
next: field-type-add-form
---

# fieldType

<pre><code class="language-php">fieldType(string $fieldName, string|ModelFieldType $fieldType[, array $permittedValues[, array $options]])</code></pre>

The are many cases that the default field type of the database is not the required or that the field type is a simple varchar although we need to have a specific type for add/edit/view. In that case you can use the function <code>fieldType</code> to force the field as that kind of type. Have in mind that this function was renamed from <code>changeFieldType </code>for simplicity.

Below you can see some examples of how you can use the <code>fieldType</code> function:

<strong>Example 1:</strong>
<pre><code class="language-php">$crud->fieldType('website_url', GroceryCrud::FIELD_TYPE_NUMERIC);</code></pre>

<strong>Example 2:</strong>
<pre><code class="language-php">$crud->fieldType('website_url', 'numeric');</code></pre>

<strong>Example 3:</strong> 
<pre><code class="language-php">
// At the beginning of the file
use GroceryCrud\Core\Model\ModelFieldType;
...
$myField = new ModelFieldType();
$myField->setDataType(GroceryCrud::FIELD_TYPE_NUMERIC);
$crud->fieldType('date_birth_year', $myField);</code></pre>

You can find all the types that exists from grocery crud by typing <code>GroceryCrud:FIELD_</code> if you are using an editor that it is recognizing the field types then you should see all the list of available fields. To make things more simple to you we have the full list (that will be always up to date) in case you need to copy-paste it really fast. Although it is strongly suggested to use the constants of GroceryCrud class for that:

<pre><code class="language-php">'boolean'
'color'
'date'
'datetime'
'dropdown'
'dropdown_search'
'email'
'enum'
'enum_searchable'
'float' 
'hidden'
'int'
'invisible'
'multiselect_native' 
'multiselect_searchable' 
'native_date'
'native_datetime'
'native_time' 
'numeric'
'password'
'password_toggle'
'relational_native'
'string'
'text' 
'timestamp'
</code></pre>

<div class="grocery-crud page-dynamic-content">
<h2>Examples</h2>


<h3 id="boolean">
  <a href="#boolean">boolean</a>
</h3>

<p>Input type for boolean (0 or 1) values.</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('active', 'boolean');</code></pre>

<p>Preview:</p>

<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Active</label>
  <div class="col-sm-9 dynamic-content-input">
    <InputBoolean
      register={register}
      setValue={setValue}
      class={classes["form-checkbox"]}
      name="boolean"
      value="1"
    />
  </div>
</div>
<br />


<h3 id="color">
  <a href="#color">color</a>
</h3>

<p>Input type for HEX color values.</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('background_color', 'color');</code></pre>

<p>Preview:</p>

<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Background Color</label>
  <div class="col-sm-9 dynamic-content-input">
    <InputColor
      control={control}
      class="form-control"
      name="color"
      value="#ff0000"
    />
  </div>
</div>

<br />


<h3 id="date">
  <a href="#date">date</a>
</h3>
<p>Input type for date values.</p>
<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('inserted_date', 'date');</code></pre>
<p>Preview:</p>

<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Inserted Date</label>
  <div class="col-sm-9">
    <InputDate
      control={control}
      class="form-control"
      name="date"
      value="2021-12-31"
    />
  </div>
</div>

<br />


<h3 id="datetime">
  <a href="#datetime">datetime</a>
</h3>
<p>Input type for date and time values at the same input.</p>
<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'datetime');</code></pre>
<p>Preview:</p>

<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Inserted Datetime</label>
  <div class="col-sm-9">
    <InputDateTime
      control={control}
      class="form-control"
      name="datetime"
      value="2021-12-31 23:59:59"
    />
  </div>
</div>

<br />


<h3 id="dropdown">
  <a href="#dropdown">dropdown</a>
</h3>

<p>Native dropdown list input type with predefined options.</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'dropdown', ['123' => 'Option 1', '456' => 'Option 2']);</code></pre>
<p>Preview:</p>

<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Contact Preferences</label>
  <div class="col-sm-9">
    <InputDropdown
      control={control}
      class="form-control form-select"
      name="dropdown"
      value="email"
      permittedValues={MOCK_PERMITTED_VALUES_SHORT_LIST}
    />
  </div>
</div>
<br />


<h3 id="dropdown_search">
  <a href="#dropdown_search">dropdown_search</a>
</h3>

<p>
  Dropdown list with text search input type with predefined options.
</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'dropdown_search', ['123' => 'Option 1', '456' => 'Option 2']);</code></pre>

<p>Preview:</p>

<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Job position</label>
  <div class="col-sm-9">
    <InputDropdownSearch
      control={control}
      name="dropdown_search"
      value="software_engineer"
      permittedValues={MOCK_PERMITTED_VALUES}
    />
  </div>
</div>
<br />



<h3 id="email">
  <a href="#email">email</a>
</h3>
<p>
  Input type for email. This is using the native <code>email</code>{" "}
  input type. The validation is triggered when you submit the form.
</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('email_address', 'email');</code></pre>

<p>Preview:</p>

<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Email Address</label>
  <div class="col-sm-9">
    <InputEmail
      control={control}
      class="form-control"
      name="email"
      value="test@example.com"
    />
  </div>
</div>


<h3 id="enum">
  <a href="#enum">enum</a>
</h3>

<p>
  Input dropdown list with predefined options. The main difference with
  `dropdown` is that the values of the arrays are also the ones that
  will be used as keys into the dropdown list.
</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'enum', ['Option 1', 'Option 2', 'Option 3', 'Option 4']);</code></pre>
<p>Preview:</p>
<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Contact Preferences</label>
  <div class="col-sm-9">
    <InputEnum
      control={control}
      class="form-control form-select"
      value="Postal Mail"
      name="enum"
      permittedValues={MOCK_PERMITTED_VALUES_FOR_ENUM}
    />
  </div>
</div>
<br />


<h3 id="enum_searchable">
  <a href="#enum_searchable">enum_searchable</a>
</h3>

<p>
  Input dropdown list with predefined options with a text search. The
  main difference with `dropdown_search` is that the values of the
  arrays are also the ones that will be used as keys into the dropdown
  list.
</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'enum_searchable', ['Option 1', 'Option 2', 'Option 3']);</code></pre>

<p>Preview:</p>
<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Contact Preferences</label>
  <div class="col-sm-9">
    <InputEnumSearchable
      control={control}
      value="Postal Mail"
      name="enum_searchable"
      permittedValues={MOCK_PERMITTED_VALUES_FOR_ENUM}
    />
  </div>
</div>

<br />


<h3 id="float">
  <a href="#float">float</a>
</h3>

<p>
  Input type for numeric values. This is using the native{" "}
  <code>number</code> input type with <code>step=.01</code>
</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('total_distance', 'float');</code></pre>

<p>Preview:</p>
<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Total Distance</label>
  <div class="col-sm-9">
    <InputFloat
      control={control}
      class="form-control"
      name="total_distance"
      value="100.52"
    />
  </div>
</div>

<br />



<h3 id="hidden">
  <a href="#hidden">hidden</a>
</h3>

<p>
  Input type which is not visible in the form. Hidden fields are useful
  when there is a need to pass a value to the form data without the user
  being able to see or change it. For example a category id which is
  passed by session. The main difference with the `invisible` field type
  is that `hidden` field type is having an HTML input with type{" "}
  <code>hidden</code>
  in the form so it will send a value from the add and edit form. You
  can set the value of the hidden field by using the functions{" "}
  <code>callbackAddForm</code> or <code>callbackEditForm</code>.
</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('category_id', 'hidden');</code></pre>

<p>
  Preview: (the only way to see the output of this field type is to
  inspect the below element)
</p>
<div class="mb-3 row dynamic-content-preview">
  <InputHidden
    control={control}
    class="form-control"
    name="category_id"
    value="45"
  />
</div>

<br />


<h3 id="int">
  <a href="#int">int</a>
</h3>

<p>
  Input type for numeric values. Same as `numeric` field type. This is
  using the native <code>number</code> input type.
</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'numeric');</code></pre>

<p>Preview:</p>
<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Total Distance</label>
  <div class="col-sm-9">
    <InputNumeric
      control={control}
      class="form-control"
      name="total_distance"
      value="100"
    />
  </div>
</div>
<br />


<h3 id="invisible">
  <a href="#invisible">invisible</a>
</h3>

<p>
  Input type which is not visible at all in the add/edit form or in
  datagrid. Invisible fields are useful when you would like to pass a
  value to the insert or update with <code>callbackBeforeInsert</code>{" "}
  or
  <code>callbackBeforeUpdate</code> or to add a value to an input that
  was generated with JavaScript. The main reason to use it is in order
  to not be filtered out by the validation rules.
</p>

<p>
  Another useful case to use `invisible` field type is when you would
  like to use the data with <code>callbackColumn</code>. Please note
  that if the `invisible` field type is used on datagrid then although
  the column will not be visible the JSON response will include the
  field.
</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('category_id', 'invisible');</code></pre>

<p>
  There is no example for this field type because it is literally not a
  visible HTML element.
</p>

<br />


<h3 id="multiselect_native">
  <a href="#multiselect_native">multiselect_native</a>
</h3>

<p>Multiselect list input type using the native HTML multiselect.</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('name', 'multiselect_native', ['123' => 'Option 1', '456' => 'Option 2']);</code></pre>

<p>Preview:</p>
<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Contact Preferences</label>
  <div class="col-sm-9">
    <InputMultiselectNative
      control={control}
      class="form-control"
      name="multiselect_native"
      permittedValues={MOCK_PERMITTED_VALUES_SHORT_LIST}
    />
  </div>
</div>
<br />

<h3 id="multiselect_searchable">
  <a href="#multiselect_searchable">multiselect_searchable</a>
</h3>

<p>Multiselect list input type with text search.</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('name', 'multiselect_searchable', ['123' => 'Option 1', '456' => 'Option 2']);</code></pre>

<p>Preview:</p>
<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Contact Preferences</label>
  <div class="col-sm-9">
    <InputMultiselectSearchable
      control={control}
      name="multiselect_searchable"
      permittedValues={MOCK_PERMITTED_VALUES_SHORT_LIST}
    />
  </div>
</div>
<br />


<h3 id="native_date">
  <a href="#native_date">native_date</a>
</h3>

<p>
  Input type for date values, with a browser/device native date picker.
</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'native_date');</code></pre>

<p>Preview:</p>
<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Date</label>
  <div class="col-sm-9">
    <InputNativeDate
      control={control}
      class="form-control"
      name="native_date"
      value="2021-12-31"
    />
  </div>
</div>
<br />


Input type for date values, with a browser/device native date picker.

Example: `$crud->fieldType('field_name', 'native_date');`

<Story name="NativeDate" of={InputTypeNativeDate} />*/}

<h3 id="native_date">
  <a href="#native_date">native_date</a>
</h3>

<p>
  Input type for date values, with a browser/device native date picker.
</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'native_date');</code></pre>

<p>Preview:</p>
<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Date</label>
  <div class="col-sm-9">
    <InputDate
      control={control}
      class="form-control"
      name="native_date"
      value="2021-12-31"
    />
  </div>
</div>
<br />


<h3 id="native_datetime">
  <a href="#native_datetime">native_datetime</a>
</h3>

<p>
  Input type for date and time values at the same input, with a
  browser/device native date and time picker.
</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'native_datetime');</code></pre>

<p>Preview:</p>
<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Date and Time</label>
  <div class="col-sm-9">
    <InputNativeDateTime
      control={control}
      class="form-control"
      name="native_datetime"
      value="2021-12-31 23:59:59"
    />
  </div>
</div>
<br />


<h3 id="native_time">
  <a href="#native_time">native_time</a>
</h3>

<p>
  Input type for time values with native browser/device time picker.
</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'native_time');</code></pre>

<p>Preview:</p>
<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Time</label>
  <div class="col-sm-9">
    <InputNativeTime
      control={control}
      class="form-control"
      name="native_time"
      value="23:59:59"
    />
  </div>
</div>
<br />


<h3 id="numeric">
  <a href="#numeric">numeric</a>
</h3>

<p>
  Input type for numeric values. This is using the native `number` input
  type.
</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'numeric');</code></pre>

<p>Preview:</p>
<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Total Distance</label>
  <div class="col-sm-9">
    <InputNumeric
      control={control}
      class="form-control"
      name="total_distance"
      value="100"
    />
  </div>
</div>
<br />


<h3 id="password">
  <a href="#password">password</a>
</h3>

<p>Input type for password values.</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'password');</code></pre>

<p>Preview:</p>
<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Password</label>
  <div class="col-sm-9">
    <InputPassword
      control={control}
      class="form-control"
      name="password"
      value="password"
    />
  </div>
</div>
<br />


<h3 id="password_toggle">
  <a href="#password_toggle">password_toggle</a>
</h3>

<p>
  Input type for password values with a toggle to show/hide the
  password.
</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'password_toggle');</code></pre>

<p>Preview:</p>
<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Password</label>
  <div class="col-sm-9">
    <InputPasswordToggle
      control={control}
      class="form-control"
      name="password_toggle"
      value="password"
    />
  </div>
</div>
<br />


<h3 id="string">
  <a href="#string">string</a>
</h3>

<p>Input type for any text value.</p>

<p>Code example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'string');</code></pre>

<p>Preview:</p>
<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Text</label>
  <div class="col-sm-9">
    <InputText
      control={control}
      class="form-control"
      name="text"
      value="Hello, World!"
    />
  </div>
</div>
<br />


<h3 id="relational_native">
  <a href="#relational_native">relational_native</a>
</h3>

<p>
  There are cases that people do not need to have a searchable
  setRelation. As by default however the selection is searchable since
  this is the most common usage. For that reason, we did create a
  different field type that we can easily switch the setRelation to a
  native select input.
</p>

<p>Example:</p>
<pre class="language-php"><code class="language-php">$crud->setRelation('office_city', 'offices', 'city');
$crud->fieldType('office_city', 'relational_native');</code></pre>

<p>
  The above code will simply transform the select input to a native one.
</p>

<p>Preview:</p>

<div class="mb-3 row dynamic-content-preview">
  <label class="col-sm-3 col-form-label">Office City</label>
  <div class="col-sm-9">
    <InputRelationalNative
      control={control}
      class="form-control form-select"
      name="relation_native"
      value="london"
      permittedValues={MOCK_PERMITTED_VALUES_SET_RELATION}
    />
  </div>
</div>

<br />

<h3 id="virtual">
    <a href="#virtual">virtual</a>
</h3>

<p>
    This field type is a special field type that is not stored in the
    database. You can use this type when you would like to use callbacks
    to manipulate the data. This is in order to not break the queries in
    the database since any field that is defined need to be in the
    database or mapped in normal cases. In case this field type is used
    without a callback then it will appear as column or a form field as
    a `string` field type with an empty value. Also it is very important
    to understand that if the data from the form will not be filtered by
    an insert or update callback then it will throw a database error
    since the specific field is not in the database.
</p>

<p>Example:</p>
<pre class="language-php"><code class="language-php">$crud->fieldType('field_name', 'virtual');</code></pre>

<p>Preview:</p>

<div class="mb-3 row dynamic-content-preview">
    <label class="col-sm-3 col-form-label">Virtual Field</label>
    <div class="col-sm-9">
    <InputText
        control={control}
        class="form-control"
        name="virtual"
        value=""
    />
    </div>
</div>
<br />
</div>

<h2 id="demo">Full Example</h2>
You can find also full example below:

<pre><code class="language-php">$crud->setTable('orders');
$crud->setSubject('Order', 'Orders');

$crud->fieldType('orderDate', 'datetime');
$crud->fieldType('requiredDate', 'datetime');
$crud->fieldType('shippedDate', 'datetime');

$crud->setRelation('customerNumber','customers','contactLastName');
$crud->fieldType('customerNumber', 'relational_native');

$output = $crud->render();</code></pre>

`embed:demo_field-type`
 