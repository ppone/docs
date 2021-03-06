# QuickBooks Online

Invoiced integrates with QuickBooks Online out of the box to extend the billing capabilities of QuickBooks. This document describes how to set up the integration and how it works in detail.

## Overview

The QuickBooks Online integration ships with the following capabilities:

- Importing outstanding invoices from QuickBooks Online
- Importing contacts from QuickBooks Online
- Writing invoices generated on Invoiced to QuickBooks Online
- Reconciling payments received on Invoiced to QuickBooks Online
- Syncing payments recorded on QuickBooks Online to Invoiced
- Most data flows happen in real-time

[![QuickBooks Online Data Flow](/docs/img/qbo-object-mapping.png)](/docs/img/qbo-object-mapping.png)

## Setup

1. In order to begin syncing with QuickBooks Online first go to **Settings** &rarr; **Integrations**.  

2. Click on **Connect to QuickBooks**. You will be redirected to QuickBooks. You will need to sign in to QuickBooks, if you are not already signed in.

   [![QuickBooks Online Login](/docs/img/qbo-login.png)](/docs/img/qbo-login.png)

3. Next you will be prompted to authorize Invoiced access to your QuickBooks Online organization.  Click on **Authorize**.

   [![QuickBooks Online Authorize](/docs/img/qbo-connect-authorize.png)](/docs/img/qbo-connect-authorize.png)

4. You will be redirected back to Invoiced. QuickBooks Online is now connected! Now you can configure the accounting sync in order to tell Invoiced how to map the data into your general ledger.

5. Change the account mapping and other settings. Click **Save**.

### Account Mapping

Invoiced will create the following accounts in your G/L if you do not specify an account:

- "Invoiced Account" - income account for new Products/Services created on QuickBooks from Invoiced line items
- "Invoiced Discount" - income account for discounts
- "Imported Invoiced Tax Code" - tax code for taxes received on Invoiced

## Usage

In this section you will learn how to use the QuickBooks Online integration.

### Field Mapping

We support setting several optional fields on QuickBooks Online that do not have a standard Invoiced field. This can be useful if you are first creating invoices on Invoiced and posting to QuickBooks Online.
 
The mappings happen automatically when a record on Invoiced has a custom field with a specific ID that corresponds to a specific field on QuickBooks Online. This gives you granular control of the data sent to QuickBooks Online.

Object Type | Invoiced Custom Field ID    | QuickBooks Field
------------|-----------------------------|------------------
Invoice     | `qbo_location`              | Location
Line Item   | `qbo_class`                 | Class

#### Income Account Mapping

The *Income Account* for any line item in QuickBooks Online is derived from the associated Product or Service on QuickBooks. Our integration will match the Product or Service on QuickBooks based on the line item name.

When creating an invoice, if a Product or Service with a matching name cannot be found on QuickBooks, then our integration will create a new Product or Service. The name of the Product or Service will be the line item name. The *Income Account* for the newly created Product or Service will be the default income account you have selected in the integration settings.

You can change the *Income Account* for any line item in the **Products and Services** page on QuickBooks. This will work for any Product or Service, regardless of whether it was created by the Invoiced integration. If you find that a line item created by the Invoiced integration does not have the correct *Income Account* then it can still be changed through the **Products and Services** page.

Please consult the QuickBooks documentation for more details on how to configure Products and Services.

### Enabling Auto-Sync

Auto-sync will run accounting syncs automatically for you on an ongoing basis. Once auto-sync is enabled, accounting syncs will happen once per day. If you enable invoice and payment importing, those will happen in near real-time as those invoices and payments are created on QuickBooks.

Here's how you can enable auto-sync:

1. Go to **Settings** &rarr; **Accounting Sync**. Click **Configure** on the QuickBooks Online integration.

2. Enable the *Reconcile to QuickBooks* option.

3. Click **Save**. You can periodically check back here to see when the next sync run is scheduled or see past activity in the *Recent Syncs* table.

### Running Syncs Manually

If you want control over when your books are synced then you can manually trigger accounting syncs. You can run an accounting sync by following these steps:

1. Go to **Settings** &rarr; **Accounting Sync**.

2. Click **Sync Now** underneath *QuickBooks Online* any time you want to run an accounting sync. When the job is finished you will see it in the *Recent Syncs* table.

### Manual Invoice Imports

You can import outstanding invoices from QuickBooks Online using the Invoice Importer located in the top right corner of the Invoice detail page. If you are using the accounting sync, then the auto-sync will continually pass payment information as well as invoices created in Invoiced. You will need to import invoices created in Quickbooks Online manually. 

Instructions:

1. Go to the **Invoices** tab in the Invoiced dashboard. Click on the **Import** button in the top-right.

2. Select **QuickBooks**.

3. Click **Start**.

4. The importer will begin working. You are free to leave the page once the import starts. If you leave you will get an email afterwards with the result.

5. Once the import is finished you will see the newly imported invoices on the **Invoices** page.

### Manual Customer Imports

You can import customers from QuickBooks into Invoiced as a one-time import. Why might you use this? The accounting sync will only import customers that have invoices, whereas a manual import will bring in your entire A/R customer list.

Instructions:

1. Go to the **Customers** tab in the Invoiced dashboard. Click on the **Import** button in the top-right.

2. Select **QuickBooks**.

3. Click **Start**.

4. The importer will begin working. You are free to leave the page once the import starts. If you leave you will get an email afterwards with the result.

5. Once the import is finished you will see the newly imported invoices on the **Customers** page.

## Edge Cases

Here we have documented all of the limitations, nuances, and edge cases to be aware of when using the QuickBooks Online integration.

- Customers on Invoiced are mapped to customers on QuickBooks by the name. Please keep in mind that QuickBooks does not allow multiple customers with the same name, but Invoiced does allow duplicates.

- Customer names are truncated to 100 characters due to a character limitation in QuickBooks.

- Only non-draft invoices on Invoiced that have been updated since the last sync will be synced. On your first sync this means that all non-draft invoices will be synced.

- The sync will create an item in QuickBooks for each line item. If the line item name is blank then a generic Invoiced item will be used.

- Line item descriptions over 4,000 characters are truncated due to a character limit in QuickBooks.

- Any changes to invoices imported from QuickBooks that are later modified on Invoiced will not be synced to QuickBooks. However, any payments received for imported invoices will be synced.

- If a line item on Invoiced has an item attached, then the product created on QuickBooks will have its SKU set to the Invoiced item ID.

- If a synced payment is refunded on Invoiced, the refund amount will be deducted from the original payment on QuickBooks.

- Payments applied to invoices on QuickBooks will be synced to Invoiced instantly. You must have auto-sync enabled for 2-way payment sync to work.

- Adding a credit note to the invoice on Invoiced that marks the invoice as paid will not sync the payment to Quickbooks Online.

- Adding a credit note to the invoice on Invoiced to partially pay the invoice will show in Quickbooks as undesposited funds.

- Credit balances from Invoiced do not sync to Quickbooks Online.

- Invoices created in Invoiced will not update in Quickbooks Online if the invoice has date that is in a accounting period closed range. No error will be thrown. 

- Payments created in Invoiced will not update in Quickbooks Online if the payment has date that is in a accounting period closed range. No error will be thrown. 

## Troubleshooting

When a sync fails you will be able to see the error message in the *Recent Syncs* section in **Settings** &rarr; **Accounting Sync**. Normally the error message will include the invoice # that failed and a detailed reason why it could not be synced. Oftentimes there is a manual action required on your end.

Below we have documented commonly encountered errors and recommended resolutions. If you are still unable to get your books synced then please contact [support@invoiced.com](mailto:support@invoiced.com) for further assistance.

### Account period has closed

> The account period has closed and the account books cannot be updated through through the QBO Services API. Please use the QBO website to make these changes.

When you see this error message then it means that Invoiced is trying to sync an invoice or payment during a time period that you have already closed. One way you can fix this is by re-opening your books for that time period and running the sync once more. When the sync finishes you can close the books again.

Another solution is to change the date range that Invoiced will sync to QuickBooks. You can tell Invoiced to not sync any invoices before the time period when you closed the books. The sync date range can be set up in the QuickBooks settings at **Settings** &rarr; **Integrations** &rarr; **Configure** (in the *QuickBooks Online* section).

### You can only add or edit one name at a time

> Business Validation Error: You can only add or edit one name at a time. Please try again.

Often this error means that an accounting sync was running while someone was working in the books. This can be fixed by signing out of the QuickBooks Online interface and re-trying the sync.

### QuickBooks Online could not authenticate

> QuickBooks Online could not authenticate.

If you see this error message then our access token to your QuickBooks account has expired. You need to go to **Settings** &rarr; **Integrations** in order to reconnect QuickBooks.

### Subscription period has ended

> Subscription period has ended or canceled or there was a billing problem : You can't add data to QuickBooks Online Plus because your trial or subscription period ended, you cancelled your subscription, or there was a billing problem. To update your subscription, click the gear icon and view your account information.

Your QuickBooks subscription has expired. Please sign into QuickBooks in order to address the issue.