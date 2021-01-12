---
id: theme-installation
title: How to install a theme
permalink: docs/theme-installation
previous: 
next:
---

# How to install a theme

To install a new theme it is fairly easy. Usually the theme is in a folder structure to just copy it to your project. For example <a href="http://www.grocerycrud.com/bootstrap-theme/">Bootstrap theme</a> has the below folder structure:
<pre>assets/
––– grocery_crud/
––––––– themes/
––––––––––– bootstrap/
–––––––––––––––– css
–––––––––––––––– fonts
–––––––––––––––– images
–––––––––––––––– index.html
–––––––––––––––– js
–––––––––––––––– ...
</pre>

So you just need to copy the folders into your already existing codeigniter and grocery CRUD project. If you don't know how to install grocery CRUD to your project then you can see <a href="/documentation/codeigniter_installation">installation guide for grocery CRUD</a>

Once you actually copy the folder to your project the bootstrap theme is installed. 

<strong>Note:</strong> Be aware that the bootstrap theme <strong>is mobile and tablet</strong> compatible so you will need to add the below code at the <head> tags in your template file (e.g. <code>application/views/example.php</code>) in order to make it work for mobile and tablet devices:

<pre><code class="language-html">&lt;meta name="viewport" content="width=device-width, initial-scale=1.0" /&gt;</code></pre>

If you already done that, the only remaining thing that you need to do is to set the theme. You can do that but adding this line below at your basic controller functions (e.g. <code>application/controllers/example.php</code>):

[code]$crud = new grocery_CRUD();
$crud->set_theme('bootstrap');
...
[/code]
<br/>
<h2>Adding a default theme at the config file</h2>
If you are sure that this theme is your favorite one, then you can also add it to your configuration file as a default theme. More specifically if you go at the file: <code>application/config/grocery_crud.php</code> and change the below line:

[code]// Default theme for grocery CRUD
$config['grocery_crud_default_theme'] = 'bootstrap';[/code]

You will not need to add the same line again and again to your CRUD functions!
<br/>

<h2>A full working example</h2>
A full working example can be find below:

<pre><code class="language-php">$crud->setTable('customers');
$crud->setSubject('Customer', 'Customers');
$crud->columns(['customerName','phone','addressLine1','creditLimit']);

$crud->setTheme('bootstrap-v4');</code></pre>

It is that simple! You don't need to configure anything else in order to make it work.