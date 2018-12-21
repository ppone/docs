# Customizing Templates

<p class="alert alert-warning">This document is for our legacy templating system. If you are using the legacy system and want to move to the new templating system then please contact support@invoiced.com.</p>

Invoiced ships with default templates for invoices, statements, and receipts, however, it's possible these templates do not match your business or branding needs. In this guide we will show you how to change the layout and appearance of the default templates.

The underlying templates are HTML and CSS. Both the layout and styling can be customized. The first step is to head over to **Settings** > **Appearance** > **Layout**. Then turn on the switch next to **Use Custom Layout**.

[![Customizable Invoice Templates](../img/customizable-invoice-templates.png)](../img/customizable-invoice-templates.png)

[Mustache](https://mustache.github.io/mustache.5.html) is the templating language used to power templates on Invoiced, including the HTML for custom templates.

### Testing

After saving any changes you can download a PDF preview by clicking the **Preview** button near the top right of the page. You can also see the generated HTML on a live invoice that has your customizations applied by opening the client view and appending `/html` to the URL, i.e. `https://dundermifflin.invoiced.com/invoices/IZmXbVOPyvfD3GPBmyd6FwXX/html`.

## Resetting a Template

If you want to reset any of the specific templates to the default then simply delete all of the text for that template and click **Save**. This will revert that template back to the default value.

## Variable Reference

These variables can be used in the Mustache templates.

### Invoices

- `company` - A hash representing the business. See [Company Object](#company-object).
- `customer` - A hash representing the customer. See [Customer Object](#customer-object).
- `invoice` - A hash representing the invoice. See [Invoice Object](#invoice-object).

### Receipts

- `company` - A hash representing the business. See [Company Object](#company-object).
- `customer` - A hash representing the customer. See [Customer Object](#customer-object).
- `transaction` - A hash representing the transaction. See [Transaction Object](#transaction-object).

### Statements

- `company` - A hash representing the business. See [Company Object](#company-object).
- `customer` - A hash representing the customer. See [Customer Object](#customer-object).
- `statement` - A hash representing the statement. See [Statement Object](#statement-object).

***

## Objects

### Company Object

A hash containing these properties:

- `name`
- `address`
- `email`
- `logo`
- `url`

### Customer Object

A hash containing the same properties as the [Customer object](/docs/api/#customer-object) in the API.

### Invoice Object

A hash containing these properties:

- `status` - Could be `draft`, `not_sent`, `sent`, `viewed`, `past_due`, `pending`, `paid`, `bad_debt`
- `url` - Client view URL
- `payment_url` - URL for the payment page in the customer portal
- `number`
- `date`
- `due_date`
- `autopay`
- `payment_terms`
- `purchase_order`
- `items` - An array of line items. See [Line Item Object](#line-item-object).
- `show_subtotal` - True when there are one or more discounts or taxes applied to the invoice.
- `subtotal`
- `rates` - An array of discounts and taxes applied to the invoice. See [Rate Object](#rate-object).
- `total`
- `amount_paid`
- `balance`
- `terms` - Terms and conditions
- `notes` - Invoice notes
- `customFields` - An array of custom fields. See [Custom Field Object](#custom-field-object)
- `metadata` - object containing any key-value metadata

### Line Item Object

A hash containing these properties:
- `name`
- `unit_cost`
- `amount`
- `description`
- `billing_period`
- `rates` - summary of any line item discounts/taxes (string)
- `metadata` - object containing any key-value metadata

### Rate Object

Summary of a discount or tax applied to an invoice. A hash containing these properties:
- `name`
- `total`

### Custom Field Object

A hash containing these properties:
- `name`
- `value`

### Transaction Object

A hash containing these properties:
- `date`
- `amount`
- `invoices`
- `credit_notes`
- `amount_refunded`
- `amount_credited`
- `method`
- `payment_source`
- `check_no`
- `metadata` - object containing any key-value metadata

### Statement Object

A hash containing these properties:
- `start`
- `end`
- `previousBalance`
- `totalInvoiced`
- `totalPaid`
- `totalOverpaid`
- `totalAdjustments`
- `balance`
- `accountDetail` - array of hashes with each these properties:
   - `date`
   - `number`
   - `invoiced`
   - `paid`
- `hasCredits`
- `previousCreditBalance`
- `totalCreditsIssued`
- `totalCreditsSpent`
- `creditDetail`
- `creditBalance` - array of hashes with each these properties:
   - `date`
   - `description`
   - `issued`
   - `charged`
   - `balance`