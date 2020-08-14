---
id: add_action
title: add_action
permalink: docs/1.x/add_action
next: add_fields
---
# add_action

    void add_action( string $label,  string $image_url , string $link_url , string $css_class ,  mixed $url_callback)
    
Add an action/operation to the list table. The way to do that its simple:

1. Add the label of your subject, for example "Photo Gallery".
2. Add an image url . Notice that in the flexigrid theme is a required field.
3. Add your custom url. This url will be connected with the `site_url` function and the primary key. For example if you add `'my_controller/photo/'` then it will transform to `site_url('my_controller/photo/'.$primary_key_for_each_row)`
4. Add a CSS class. Remember that at the theme of datatables a CSS class includes images , for example :  `ui-icon-image`, `ui-icon-plus`, e.t.c.
5. You can even add your own url callback. If you don't want the default transformation of the url, you can use this paremeter to add your own algorithm of the url transformation.

> One of the most common usages of add_action method is the combination of [Image CRUD](/image-crud).
>
> Image CRUD is a Photo Gallery generator and is created by John Skoumbourdis by having in mind the simplicity of usage of Grocery CRUD.

## Theme specific icons

Please notice that there is a small difference between themes for the 4th parameter (CSS class) that you can use in action buttons that's why we've listed the CSS class names that you can use for each theme:

- **Flexigrid**: For the flexigrid theme the 3rd parameter is not in use as we haven't include any CSS icon library at the theme. If you need to add an extra icon your can add your own images from the 2nd parameter
- **Datatables**: For the datatables theme the 3rd parameter is using the jQuery UI icons. For a full list of the icons that you can use please check: Jquery UI icons. There is also an example that you can check below with a CSS icon.
- **Bootstrap Theme version 3** is using by default the icons of font awesome. An example usage is: 'fa-book'
- **Bootstrap Theme version 4** is using by default the icons of Elusive icons. An example usage is: 'el-book'

Below we have 3 examples of usage for each theme:

**Bootstrap theme version 3**

    $crud->add_action('Books', '', 'admin/book', 'fa-book');

**Bootstrap theme version 4**

    $crud->add_action('Books', '', 'admin/book', 'el-book');
    
**Datatables theme**

Below you can see a full working example with 3 different types of usage for datatables theme:

    function offices_management_with_actions()
    {
        $crud = new grocery_CRUD();
     
        $crud->set_theme('datatables');
        $crud->set_table('offices');
        $crud->set_subject('Office');
        $crud->required_fields('city');
        $crud->columns('city','country','phone');
     
        $crud->add_action('More', '', 'demo/action_more','ui-icon-plus');
        $crud->add_action('Photos', '', '','ui-icon-image',array($this,'just_a_test'));
        $crud->add_action('Smileys', '/assets/uploads/general/smiley.png', 'demo/action_smiley');
     
        $output = $crud->render();
     
        $this->_example_output($output);
    }
     
    function just_a_test($primary_key , $row)
    {
        return site_url('demo/action/action_photos').'?country='.$row->country;
    }
    
And the result will be:

`embed:demo_add_action`
    