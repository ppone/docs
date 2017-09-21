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

##Quickbooks Online Syncing Nuances 
- QBO sync will create items in QBO unless the item is blank and then it will the default Invoiced item.

- Synced QBO Invoices are marked with the invoice number having the format of INVD-{Invoice Number in Invoiced}.  So a invoice in Invoiced with number "INV-004" would be "INVD-INV-004" in QBO.

- Unless you change this in the settings, QBO sync will create a default account, discount account, and tax code.

- QBO sync factors your time-zone when calculating the invoice date and due date.

- Only non-draft invoices from Invoiced will be synced.

- Line item descriptions over 4000 characters are truncated.

- Sync handles bad debt invoices which are invoices in Invoiced that are closed and do not have a payment against them.

- Customer names directly map to QBO display names, to avoid any collisions we append your invoiced customer number after your customer name.

- Customer names are truncated to 100 characters and that is inclusive of your customer number.

- Only invoices updated in Invoiced since the last time you ran the sync will be synced.

- If a line item has a catalog item then the item created on QuickBooks will have its SKU set to the catalog item ID.

## Troubleshooting

If the sync fails first try to reconnect your Quickbooks Online account and try again.  If it still fails please contact [support@invoiced.com](mailto:support@invoiced.com) for further assistance.