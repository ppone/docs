#Customers	

Invoiced makes it easy to add and update customers. While a customer can be added when creating an invoice, a customer can also be created simply by selecting:

Customers &rarr; New Customer

You will be prompted to add a name, account number (this will generate if left blank), and an email address. On the New customer set up, you can also add a payment method, billing address, specify allowed payment methods, and allow chasing on the customers profile. If you do not know this information, you can leave these items blank. 

[![Creating a Customer](/docs/img/create-a-customer.gif)](/docs/img/create-a-customer.gif)

Once a customer is created, you can apply invoices, pending line items, and subscriptions to the customers account.

## Adding a Payment Method

Customer records also allows you to store a payment method on the customer's account. Simply access the customer by finding the customer in Invoiced. 

Under the *Payment Method* section, you can add a payment method to use for the customer. 

[![Add a Payment Method](/docs/img/add-payment-source.png)](/docs/img/add-payment-source.png)

## Additional Contacts

Want to add more contacts to a customers account to receive invoice notifications? Simply access the customer account that needs additional contacts added and press the "Add" button. Add the contact and check the box for *copy on account communications*. 

[![Add a Contact](/docs/img/add-contacts.png)](/docs/img/add-contacts.png)

## Merging Customers

When utilizing Invoiced you might find youself in a situation where there is a duplicate customer account. Duplicate customers can happen due to a third-party integration, a customer signing up from a sign up form when they already exist on Invoiced, or due to a clerical error. The problem becomes magnified when there is stored payment information on file that should belong to an existing customer account. Invoiced allows you to merge two customer accounts in order to remedy duplicate customer accounts. Please be warned that merging customers is a powerful and permanent action. A merged customer cannot be reversed.

<p class="alert alert-warning">Merging customers is currently a beta feature.</p>

How to merge customers:
1. Open the customer account that you want to keep in the Invoiced dashboard.
2. Click **Actions** &rarr; **Merge Customer**.
3. Search for and select the customer you want to merge into this customer.
4. Click **Preview** to see a preview of the resulting customer. The customer that you selected in the previous step will have all of their transactions, payment information, and history merged into the customer from the first step. The profile for the customer being merged in will be deleted after all of the associated data has been moved to the resulting customer.
   [![Merging a Customer](/docs/img/merge-customer.png)](/docs/img/merge-customer.png)
5. Click **Merge** to finalize the process.