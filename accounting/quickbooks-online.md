# Quickbooks Online

Invoiced integrates with QuickBooks Online out of the box to extend the billing capabilities of QuickBooks. This document describes how to set up the integration and how it works in detail.

## Overview

The QuickBooks Online integration ships with the following capabilities:

- Importing outstanding invoices from QuickBooks Online
- Importing contacts from QuickBooks Online
- Writing invoices generated on Invoiced to QuickBooks Online
- Reconciling payments received on Invoiced to QuickBooks Online

[![QuickBooks Online Data Flow](../img/qbo-object-mapping.png)](../img/qbo-object-mapping.png)

## Setup

In order to begin syncing with QuickBooks Online first go to **Settings** > **Accounting Sync**.  

[![Settings Page](../img/all-settings-accounting-sync.png)](../img/all-settings-accounting-sync.png)

Then click on **Connect to QuickBooks**.

[![QuickBooks Online Connect](../img/accounting-sync-settings.png)](../img/accounting-sync-settings.png)

Next you will be prompted to authorize your QuickBooks company to Invoiced. Once you do this you will be redirected back to Invoiced.

## Usage

You can now start syncing your data with QuickBooks Online by clicking **Synchronize**.

[![QuickBooks Online Connected](../img/accounting-sync-quickbooks-online-connected.png)](../img/accounting-sync-quickbooks-online-connected.png)

No further action is required. You will be able to monitor the progress of your sync once it has started and view the results of past syncs.

[![QuickBooks Online Invoice Sync](../img/quickbooks-online-invoice-sync.png)](../img/quickbooks-online-invoice-sync.png)

Any time you want to sync your data with Xero just return to the **Accounting Sync** page and click **Synchronize**.

## Edge Cases

Here we have documented all of the limitations, nuances, and edge cases to be aware of when using the QuickBooks Online integration.

- Customers on Invoiced are mapped to customers on QuickBooks by the name. Please keep in mind that QuickBooks does not allow multiple customers with the same name, but Invoiced does allow duplicates.

- Customer names are truncated to 100 characters due to a character limitation in QuickBooks.

- Unless you change this in the settings, QBO sync will create a default account, discount account, and tax code.

- Only non-draft invoices from Invoiced will be synced. Also, only invoices updated since the last sync will be synced. On your first sync this means that all non-draft invoices will be synced.

- QBO sync will create items in QBO unless the item is blank and then it will the default Invoiced item.

- Line item descriptions over 4,000 characters are truncated due to a character limit in QuickBooks.

- The invoice sync does correctly handle bad debt invoices, which are invoices in Invoiced that are closed and do not have a payment against them.

- Invoices imported from QuickBooks that were later modified on Invoiced will not be synced to QuickBooks, however, any payments received for that invoice on Invoiced will be synced.

- If a line item on Invoiced has a catalog item attached, then the item created on QuickBooks will have its SKU set to the catalog item ID.

## Troubleshooting

If the sync fails first try to reconnect your Quickbooks Online account and try again.  If it still fails please contact [support@invoiced.com](mailto:support@invoiced.com) for further assistance.