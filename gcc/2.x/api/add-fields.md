# addFields

    addFields(array $addFields)

The fields that will be visible to the end user for add/insert form. For example:

    $crud->addFields(['first_name', 'last_name', 'fullname', 'address'])

## Full Example

    $crud->setTable('customers');
    $crud->setSubject('Customer', 'Customers');
    $crud->addFields(['customerName','phone','addressLine1','creditLimit']);
    
    $output = $crud->render();

You can see the result of the above code below.The main difference that you will notice is that when you will press the “Add customer” button. The fields are less when you add one (these are the fields that was specified at the addFields functions) than by pressing the edit button.