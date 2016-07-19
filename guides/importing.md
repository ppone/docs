# Importing

It's easy to import customers, invoices, payments, and catalog items into Invoiced. This guide shows you how to import data into Invoiced using our importer.

## Usage

The import tool works by letting you build a spreadsheet where each line contains a record that you want to import. Once you have your spreadsheet ready to go, you simple copy the contents and paste it into the textbox on the new import page. In the next step we will help you match each column to a field in Invoiced. Finally, just click the button to start the import and we will notify you when it's finished.

We recommend using the first line to specify which field on Invoiced the line matches up with. It's not required, however, it makes the import process quicker. You can get the field names from the sample import templates below for the type of record you are trying to import. Invoiced will automatically match the columns after the first step. 

A few notes:

- All dates must be entered using this format: `Aug-06-2015`
- Any unused, optional fields can be removed or left blank
- If there's a failure in your import we will show you each line that failed with the reason on the import page.
- All importers support setting metadata on imported objects for any columns with a title following the pattern: `metadata.key` where `key` is the name of the metadata property. For example, you could add a `sales-rep` metadata value by adding a `metadata.sales-rep` column.

### Customers

Steps to import Customers:

1. Go to the **Customers** section

2. Click the **Import** link to the right of the page

3. Build your import spreadsheet, select all the contents, and paste it into the textbox. [Download](https://dashboard.invoiced.com/files/customers-import-template.csv) a sample customers import template to get started.

4. Click **Go to Next Step**

5. Match each column to a field in Invoiced. You can tell us to skip a column too if needed.

6. Click **Start Import**. That's it. We will notify you when the import finishes.

#### Tips

- The only required field is the customer's name.
- Customers are identified by their account number first, and if that's not given then customers are identified by their name. If a customer with the same account number (or name if account # was not given) has already been created in Invoiced then a new customer will not be created.
- You can supply a customer # or if left empty we will generate one for you.
- The *Type* field can only be one of `person`, `company`, or blank.
- The *Collection Mode* field can only be one of `manual`, `auto`, or blank.

### Invoices

Steps to import Invoices:

1. Go to the **Invoices** section

2. Click the **Import** link to the right of the page

3. Build your import spreadsheet, select all the contents, and paste it into the textbox. [Download](https://dashboard.invoiced.com/files/invoices-import-template.csv) a sample invoices import template to get started.

4. Click **Go to Next Step**

5. Match each column to a field in Invoiced. You can tell us to skip a column too if needed.

6. Click **Start Import**. That's it. We will notify you when the import finishes.

#### Tips

- The *Customer* field is the only required field.
- Each line represents an invoice AND a corresponding line item.
If an invoice has multiple line items then you would have multiple lines for the same invoice. Only the first line needs to include the invoice's information. Subsequent lines must have the same invoice #, however only need to have the line item fields filled in (*Item*, *Description*, *Quantity*, *Unit Cost*, *Tax*, and *Discounts*).
- You can supply an invoice # or leave it blank. If left blank we will generate one for you.
- Customers are identified by their account number, or name if the account number is not given. If that account number or name matches an existing customer then we will use that. Otherwise, a new customer profile will be created. You can optionally provide an address if you intend to create a new customer profile.
- The *Currency* field should use an [ISO-4217](https://en.wikipedia.org/wiki/ISO_4217) currency code. Otherwise, we will use your default currency.
- The *Type* field can be one of `product`, `service`, `expense`, `hours`, `days`, or blank

### Payments

Steps to import Payments:

1. Go to the **Payments** section

2. Click the **Import** link to the right of the page

3. Build your import spreadsheet, select all the contents, and paste it into the textbox. [Download](https://dashboard.invoiced.com/files/payments-import-template.csv) a sample payments import template to get started.

4. Click **Go to Next Step**

5. Match each column to a field in Invoiced. You can tell us to skip a column too if needed.

6. Click **Start Import**. That's it. We will notify you when the import finishes.

#### Tips

- The required fields are one of *Amount* and one of *Invoice #* or *Invoice ID* or *Customer*.
- The payment method can be one of `credit_card`, `ach`, `bitcoin`, `paypal`, `check`, `wire_transfer`, `cash`, `other`
- When the payment method is `check` you can pass in a check # with the *Gateway ID* field
- The *Gateway* field should only be used when tracking electionic payments

### Catalog Items

1. Go to **Settings** > **Catalog**

2. Click **Import**

3. Build your import spreadsheet, select all the contents, and paste it into the textbox. [Download](https://dashboard.invoiced.com/files/catalog_items-import-template.csv) a sample catalog items import template to get started.

4. Click **Go to Next Step**

5. Match each column to a field in Invoiced. You can tell us to skip a column too if needed.

6. Click **Start Import**. That's it. We will notify you when the import finishes.

#### Tips

- The required fields are *ID* and *Name*
- The *ID* field must be at least 2 characters long and can only be alphanumeric, dashes, or underscores
- The *Type* field can be one of `product`, `service`, `expense`, `hours`, `days`, `month`, `year`, `shipping`, or blank

### Rolling back imports

Did your import not turn out the way you expected? Not a problem! You can rollback any import with the click of a button provided it happened within the last 3 days. Simply open the import in the dashboard and click the red **Rollback Import** button.