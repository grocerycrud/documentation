---
id: callback-after-delete
title: callbackAfterDelete
permalink: docs/callback-after-delete
previous: callback-add-form
next: callback-after-delete-multiple
---

# callbackAfterDelete


<pre><code class="language-php">callbackAfterDelete(callable $callback)</code></pre>
The callback that will be used right after the delete. The only parameter that the state will have is the primary key value. 

<code>Important:</code> It is important to mention here that the callbackAfterDelete is called only for the Delete button of the row. The callback <strong>will not</strong> be called for the multiple delete functionality. If you need to use a callback for multiple delete rows, you should use <a href="/enterprise/api-and-function-list/callbackAfterDeleteMultiple">callbackAfterDeleteMultiple</a> instead and keep the callbackAfterDelete for the one-row delete button.
<code>Notice:</code> Have in mind that if you haven't replaced the actual delete functionality (e.g. with a callback), it will be impossible to retrieve the data of the deleted row. If the last phrase doesn't make much sense to you we have an example below to understand exactly what we mean.

Example:
<pre><code class="language-php">$crud->callbackAfterDelete(function ($stateParameters) {
    // Your code here    

    return $stateParameters;
});</code></pre>

The <code>$stateParameters</code> variable is at the below form:

<pre><code class="language-php">$callbackAfterDelete = (object)[
    'primaryKeyValue' => '1234'
];</code></pre>

Below there is a working example of the <code>callbackAfterDelete</code> method. As we also wanted to skip the delete so we can update the record, we are also using the <code>callbackDelete</code> at the example just for the demonstration to skip the delete.

<code>Notice:</code> At the below example we are using the database from Codeigniter as this website is built in Codeigniter framework. At your project of course you can use your framework's database queries to get some manual parameters.

<pre><code class="language-php">$crud->setTable('offices');
        $crud->setSubject('Office', 'Offices');
        $crud->columns(['city','country','phone','addressLine1','postalCode']);
        $crud->callbackDelete(function ($stateParameters) {
            return $stateParameters;
        });

        $crud->callbackAfterDelete(function ($stateParameters) {
            $this->db->where('officeCode', $stateParameters->primaryKeyValue);
            $customer = $this->db->get('offices')->row();

            if (!empty($customer)) {
                $this->db->update('offices',
                    ['city' => '[DELETED]' . $customer->city],
                    ['officeCode' => $stateParameters->primaryKeyValue]);
            }

            return $stateParameters;
        });

        $output = $crud->render();
</code></pre>

[demo]demo_callback_after_delete[/demo]