---
id: callback-before-delete
title: callbackBeforeDelete
permalink: docs/callback-before-delete
previous: callback-after-upload
next: callback-before-delete-multiple
---

# callbackBeforeDelete


<pre><code class="language-php">callbackBeforeDelete(callable $callback)</code></pre>
The callback that will be used right before the delete. The only parameter that the state will have is the primary key value. 

Example:
<pre><code class="language-php">$crud->callbackBeforeDelete(function ($stateParameters) {
    // Your code here    

    return $stateParameters;
});</code></pre>

The <code>$stateParameters</code> variable is at the below form:

<pre><code class="language-php">$stateParameters = (object)[
    'primaryKeyValue' => '1234'
];</code></pre>

Below there is a working example of the <code>callbackBeforeDelete</code> method. As we also wanted to skip the delete so we can update the record, we are also using the <code>callbackDelete</code> at the example just for the demonstration to skip the delete.

<code>Notice:</code> At the below example we are using the database from Codeigniter as this website is built in Codeigniter framework. At your project of course you can use your framework's database queries to get some manual parameters.

<pre><code class="language-php">$crud->setTable('offices');
        $crud->setSubject('Office', 'Offices');
        $crud->columns(['city','country','phone','addressLine1','postalCode']);
        $crud->callbackDelete(function ($stateParameters) {
            return $stateParameters;
        });

        $crud->callbackBeforeDelete(function ($stateParameters) {
            $this->db->where('officeCode', $stateParameters->primaryKeyValue);
            $customer = $this->db->get('offices')->row();

            if (!empty($customer)) {
                $this->db->update('offices',
                    ['city' => '[BEFORE_DELETE]' . $customer->city],
                    ['officeCode' => $stateParameters->primaryKeyValue]);
            }

            return $stateParameters;
        });

        $output = $crud->render();
</code></pre>

[demo]demo_callback_before_delete[/demo]