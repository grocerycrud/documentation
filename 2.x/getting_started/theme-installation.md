---
id: theme-installation
title: How to install a theme
description: To install a new theme it is fairly easy. Usually the theme is in a folder structure to just copy it to your project.
permalink: docs/theme-installation
previous: 
next:
---

# How to install a theme

To install a new theme it is fairly easy. Usually the theme is in a folder structure to just copy it to your project. For example <a href="http://www.grocerycrud.com/bootstrap-theme/">Bootstrap theme</a> has the below folder structure:
<pre>assets/
––– grocery_crud/
––––––– themes/
––––––––––– bootstrap-v4/
–––––––––––––––– css
–––––––––––––––– fonts
–––––––––––––––– images
–––––––––––––––– index.html
–––––––––––––––– js
–––––––––––––––– ...
</pre>

So you just need to copy the folders into your already existing Codeigniter and Grocery CRUD project. 
If you don't know how to install grocery CRUD to your project then you can see the [installation guide](/docs/installation) for Grocery CRUD

After you've copied the folder to your project, the bootstrap theme will be installed. 

**Important notice:️** Be aware that the bootstrap theme is mobile and tablet compatible so you will need to add the below code at the <code>&lt;head&gt;</code> tag in your template file in order to make it work for mobile and tablet devices:

<pre><code class="language-html">&lt;meta name="viewport" content="width=device-width, initial-scale=1.0" /&gt;</code></pre>

If you've already done that, the only remaining thing that you need to do is to set the theme. 
You can do that by adding the below line at your basic Controller functions

<pre><code class="language-php">$crud = new GroceryCrud();
$crud->setTheme('bootstrap-v4');
</code></pre>

## Adding a default theme at the config file

If you are sure that this theme is your favorite one, then you can also add it to your configuration file as a default theme. 
More specifically if you go at the file: <code>app/Config/GroceryCrud.php</code> and change the below line:

<pre><code class="language-php">public $default_theme = 'flexigrid';</code></pre>

to:

<pre><code class="language-php">public $default_theme = 'bootstrap-v4';</code></pre>

With that change the final file of <code>app/Config/GroceryCrud.php</code> will look like this:

<pre><code class="language-php">&lt;?php
namespace Config;

class GroceryCrud
{
    /**
     * For view all the languages go to the folder assets/grocery_crud/languages/
     * @var string
     */
    public $default_language = 'English';

    /**
     * There are only three choices: "uk-date" (dd/mm/yyyy), "us-date" (mm/dd/yyyy) or "sql-date" (yyyy-mm-dd)
     * @var string
     */
    public $date_format = 'uk-date';

    /**
     * The default per page when a user firstly see a list page
     * @var int
     */
    public $default_per_page = 10;

    /**
     * You can choose between 'ckeditor','tinymce' or 'markitup'
     * @var string
     */
    public $default_text_editor = 'ckeditor';

    /**
     * You can choose 'minimal' or 'full'
     * @var string
     */
    public $text_editor_type = 'full';

    /**
     * The character limiter at the list page, zero(0) value if you don't want character limiter at your list page
     * @var int
     */
    public $character_limiter = 30;

    /**
     * Having some options at the list paging. This is the default one that all the websites are using.
     * Make sure that the number of default_per_page variable is included to this array.
     * @var array
     */
    public $paging_options = ['10','25','50','100'];

    /**
     * Default theme for grocery CRUD. You can choose between 'flexigrid', 'datatables', 'bootstrap', 'bootstrap-v4'
     * @var string
     */
    public $default_theme = 'bootstrap-v4';

    /**
     * The environment is important so we can have specific configurations for specific environments
     * @var string
     */
    public $environment = 'production';

    /**
     * Turn XSS clean into true in case you are exposing your CRUD into public. Please be aware that this is
     * stripping all the HTML and do not just trim the extra javascript
     * @var bool
     */
    public $xss_clean = false;

}</code></pre>

With the above change you will not need to add the same extra line at all your functions. Easy-peasy 😃
<br/>

## Example

A full working example can be find below:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->setTheme('bootstrap-v4');</code></pre>

It is that simple! You don't need to configure anything else in order to make it work.