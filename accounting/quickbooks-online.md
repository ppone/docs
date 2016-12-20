#Quickbooks Online

The QuickBooks Online integration lets you sync data by pushing invoices from Invoiced into Quickbooks Online (QBO).  Invoiced will also create the accompanying customers, payments, line items, tax, and discount associated with the invoice in QBO.

There is also another sync which lets you download customers from QBO into Invoiced.

##Usage

In order to begin syncing with QuickBooks Online first go to **Settings** > **Accounting Sync**.  

[![Settings Page](../img/all-settings-accounting-sync.png)](../img/all-settings-accounting-sync.png)

Then click on **Connect to QuickBooks**.

[![QuickBooks Online Connect](../img/accounting-sync-settings.png)](../img/accounting-sync-settings.png)

Next you will be prompted to authorize your QuickBooks company to Invoiced. Once you do this you will be redirected back to Invoiced. You can now start syncing your data with QuickBooks Online by clicking **Synchronize**.

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

- If you need to re-sync all of your invoices please contact support@invoiced.com

##Quickbooks Online Troubleshooting

- If the sync fails first try to reconnect your Quickbooks Online account and try again.  If it still fails please contact [support@invoiced.com](mailto:support@invoiced.com) for further assistance.