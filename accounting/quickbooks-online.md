# QuickBooks Online

Invoiced integrates with QuickBooks Online out of the box to extend the billing capabilities of QuickBooks. This document describes how to set up the integration and how it works in detail.

## Overview

The QuickBooks Online integration ships with the following capabilities:

- Importing outstanding invoices from QuickBooks Online
- Importing contacts from QuickBo   oks Online
- Writing invoices generated on Invoiced to QuickBooks Online
- Reconciling payments received on Invoiced to QuickBooks Online

[![QuickBooks Online Data Flow](../img/qbo-object-mapping.png)](../img/qbo-object-mapping.png)

## Setup

1. In order to begin syncing with QuickBooks Online first go to **Settings** > **Integrations**.  

   [![Integration Settings](../img/integration-settings.png)](../img/integration-settings.png)

2. Click on **Connect to QuickBooks**. You will be redirected to QuickBooks. You will need to sign in to QuickBooks, if you are not already signed in.

   [![QuickBooks Online Login](../img/qbo-login.png)](../img/qbo-login.png)

3. Next you will be prompted to authorize Invoiced access to your QuickBooks Online organization.  Click on **Authorize**.

   [![QuickBooks Online Authorize](../img/qbo-connect-authorize.png)](../img/qbo-connect-authorize.png)

4. You will be redirected back to Invoiced. QuickBooks Online is now connected!

   [![QuickBooks Online Connected to Invoiced](../img/qbo-connected.png)](../img/qbo-connected.png)

5. Next you should click **Configure** in order to configure the integration. Invoiced by default creates several default accounts in your G/L. You can change the account mapping as you see fit.

   [![QuickBooks Online Settings](../img/qbo-settings.png)](../img/qbo-settings.png)

## Usage

In this section you will learn how to use the QuickBooks Online integration.

### Enabling Auto-Sync

Auto-sync will run accounting syncs automatically for you on an ongoing basis. Once auto-sync is enabled, accounting syncs will happen approximately once per hour. Here's how you can enable auto-sync:

1. Go to **Settings** > **Accounting Sync**.

   [![QuickBooks Online Connected](../img/accounting-sync-qbo-connected.png)](../img/qbo-connected.png)

2. Click **Enable Auto-Sync** next to the *QuickBooks Online* integration. You can periodically check back here to see activity in the *Recent Syncs* table.

   [![QuickBooks Online Invoice Sync](../img/quickbooks-online-invoice-sync.png)](../img/quickbooks-online-invoice-sync.png)

### Running Syncs Manually

If you want control over when your books are synced then you can manually trigger accounting syncs. You can run an accounting sync by following these steps:

1. Go to **Settings** > **Accounting Sync**.

   [![QuickBooks Online Connected](../img/accounting-sync-qbo-connected.png)](../img/qbo-connected.png)

2. Click **Sync Now** underneath *QuickBooks Online* any time you want to run an accounting sync. When the job is finished you will see it in the *Recent Syncs* table.

   [![QuickBooks Online Invoice Sync](../img/quickbooks-online-invoice-sync.png)](../img/quickbooks-online-invoice-sync.png)

## Edge Cases

Here we have documented all of the limitations, nuances, and edge cases to be aware of when using the QuickBooks Online integration.

- Customers on Invoiced are mapped to customers on QuickBooks by the name. Please keep in mind that QuickBooks does not allow multiple customers with the same name, but Invoiced does allow duplicates.

- Customer names are truncated to 100 characters due to a character limitation in QuickBooks.

- Unless you change this in the settings, the sync will create a default account, discount account, and tax code.

- Only non-draft invoices on Invoiced that have been updated since the last sync will be synced. On your first sync this means that all non-draft invoices will be synced.

- The sync will create an item in QuickBooks for each line item. If the line item name is blank then a generic Invoiced item will be used.

- Line item descriptions over 4,000 characters are truncated due to a character limit in QuickBooks.

- The invoice sync will correctly reconcile bad debt, which are invoices in Invoiced that are closed and do not have a payment against them.

- Any changes to invoices imported from QuickBooks that are later modified on Invoiced will not be synced to QuickBooks. However, any payments received for imported invoices will be synced.

- If a line item on Invoiced has a catalog item attached, then the item created on QuickBooks will have its SKU set to the catalog item ID.

## Troubleshooting

When a sync fails you will be able to see the error message in the *Recent Syncs* section in **Settings** > **Accounting Sync**. Normally the error message will include the invoice # that failed and a detailed reason why it could not be synced. Oftentimes there is a manual action required on your end.

Below we have documented commonly encountered errors and recommended resolutions. If you are still unable to get your books synced then please contact [support@invoiced.com](mailto:support@invoiced.com) for further assistance.

### Account period has closed

> The account period has closed and the account books cannot be updated through through the QBO Services API. Please use the QBO website to make these changes.

When you see this error message then it means that Invoiced is trying to sync an invoice or payment during a time period that you have already closed. One way you can fix this is by re-opening your books for that time period and running the sync once more. When the sync finishes you can close the books again.

Another solution is to change the date range that Invoiced will sync to QuickBooks. You can tell Invoiced to not sync any invoices before the time period when you closed the books. The sync date range can be set up in the QuickBooks settings at **Settings** > **Integrations** > **Configure** (in the *QuickBooks Online* section).

### You can only add or edit one name at a time

> Business Validation Error: You can only add or edit one name at a time. Please try again.

Often this error means that an accounting sync was running while someone was working in the books. This can be fixed by signing out of the QuickBooks Online interface and re-trying the sync.