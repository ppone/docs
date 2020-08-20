# Custom Fields

With custom fields you can store arbitrary business data on customer accounts and invoices. That data can then be displayed on the invoice presented to your customer.

Custom fields have many uses. Here's just a few scenarios where custom fields can help:

- Keeping track of the sales representative for customer accounts
- Segmenting receivables by department
- Adding purchase order numbers to invoices
- Internal tracking purposes

## Usage

### Creating a custom field

You can set up custom fields in **Settings** &rarr; **Custom Fields**. Then click on **New Custom Field** to add a custom field.

It's as simple as entering in the name of your custom field and clicking **Save**. This step only needs to be done once for each custom field your business uses.

#### Limitations

- The custom field ID must be unique and cannot be changed later.
- Only 10 custom fields can be created.
- Custom field titles are limited to **40 characters**.
- Values set on customer accounts and invoices are limited to **255 characters**.

### Using custom fields

Now when you are creating a new customer account or drafting an invoice you will see your newly created custom field as an option when creating a customer account or drafting a new invoice.

And that's all it takes to setup and deploy custom fields. Any non-empty, customer-visible custom field will be displayed on the invoice presented to your customer. If the custom field is empty on the invoice then it will inherit its value from the customer account (when that has been set).

[![Custom Field Invoice](/docs/img/custom-field-invoice.png)](/docs/img/custom-field-invoice.png)

### Filtering

When browsing customers, invoices, estimates, subscriptions, and payments inside of the dashboard you can filter the results by custom field values. This setting is available within the **Filter** menu. Any results return will exactly match the filter you have built.

### Reporting

Custom fields enhance your reporting by making additional filtering and grouping options available.

#### Report Filtering

You can filter reports to only include invoices that exactly match a custom field value. Want to see how a specific region or department is performing?

#### Report Grouping

Any of the invoice reports can be grouped by custom field values using the **Group By** option. The custom field must have been set up with a pre-defined list of choices in order to support grouping. This might be useful for building a sales by rep report.

The resulting report will look like this:

[![Custom Field Report Group By](/docs/img/custom-field-grouped-report-sales.png)](/docs/img/custom-field-grouped-report-sales.png)

### Importing

Custom field values can be set when [importing](/resources/docs/guides/importing-data) customers and invoices.