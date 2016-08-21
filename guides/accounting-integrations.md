#Accounting Integrations Guide

The guide will go over how to use accounting integrations, and the technical nuances with each integration.  Invoiced currently supports a accounting integration with [Xero](#xero) and [Quickbooks Online](#quickbooks-online).

##Xero

The Xero integration lets you sync data by pushing invoices from Invoiced into Xero.  The integration will also push the corresponding contacts, and payments from Invoiced into Xero.

###Usage

In order to begin syncing with Xero first go to **Settings** > **Accounting Sync**.  

![Settings Page](../img/all-settings-accounting-sync.png)

Then click on **Connect to Xero**.

![Xero Connect](../img/accounting-sync-settings.png)

You will get redirected to Xero for authentication. Input your Xero email address and password.

![Xero Authorize](../img/xero-screen-3.png)

Next you will be prompted to authorize your Xero organization to Invoiced.  Click on **Authorize**.

![Xero Settings](../img/xero-screen-4.png)

You will be redirected back to Invoiced. You can now start syncing your data with Xero by clicking **Synchronize**.

![Xero Connected](../img/accounting-sync-xero-connected.png)

No further action is required. You will be able to monitor the progress of your sync once it has started and view the results of past syncs.

![Xero Invoice Sync](../img/xero-invoice-sync.png)

Any time you want to sync your data with Xero just return to the **Accounting Sync** page and click **Synchronize**.

###Xero Syncing Nuances 

- Currently you are only authenticated for 30 minutes.  You should get a prompt to reconnect when you are Xero Integration page if your authentication has expired. 

- If you have changed your Xero organization you will need to reconnect your xero account by clicking on the link in the Xero Integration Page.

- Invoices are batch processed and around 50 invoices are batched at a time.

- The sync is one way and changes you make in Xero with synced invoices, payments may get overwritten or deleted.

- The Xero sync will only process newly updated invoices in Invoiced.  If a Invoiced payment is updated, than the Invoiced Invoice is considered updated as well.

- Synced Xero Invoices are marked with the invoice number having the format of INVD-{Invoice Number in Invoiced}.  So a invoice in Invoiced with number "INV-004" would be "INVD-INV-004" in Xero.  

- Synced Xero Contacts are marked with the customer name equal to {customer name in Invoiced} {customer number in Invoiced}.  So a customer in Invoiced with name "John Doe" and number "Cust-001" would have a name in Xero of "John Doe Cust-001". 

- Currently we auto-create 2 Invoiced Accounts in Xero.  The accounts that will be created, is a Invoiced Sales Account and Invoiced Bank Account.  The Invoiced Bank Account will be the account for all of your Invoiced payments and the Invoiced Sales Account for all of your invoices and line items.

- Even though line items are carried over through Invoices, they are not explicitly created in Xero.  Invoiced Catalog Items are not migrated over.

- A default Invoiced Tax Rate is created and applied to all synced Invoices.

- Taxes are computing by adding all the invoice taxes + line item taxes.  They are added as 2 line items. The first line item will have a tax amount = 1 * unit price. The unit price will be the total computed tax.  The second line item will have a negative unit price equal to -1 * total computed tax; this will cancel the first line item and leave the tax amount = total computed tax. 

- Discounts are added as a negative line item.  Discounts are first computed by adding all the invoice discounts + line item discounts on invoiced.

- Invoices without the due date in Invoiced, will be set to the Invoice date.

- All synced invoices in Xero are Tax Exclusive

###Xero Troubleshooting

- If the sync fails first try to reconnect the Xero organization and try again.  If it still fails please contact [support@invoiced.com](mailto:support@invoiced.com) for further assistance.


##Quickbooks Online

The QuickBooks Online integration lets you sync data by pushing invoices from Invoiced into Quickbooks Online (QBO).  Invoiced will also create the accompanying customers, payments, line items, tax, and discount associated with the invoice in QBO.

There is also another sync which lets you download customers from QBO into Invoiced.

###Usage

In order to begin syncing with QuickBooks Online first go to **Settings** > **Accounting Sync**.  

![Settings Page](../img/all-settings-accounting-sync.png)

Then click on **Connect to QuickBooks**.

![QuickBooks Online Connect](../img/accounting-sync-settings.png)

Next you will be prompted to authorize your QuickBooks company to Invoiced. Once you do this you will be redirected back to Invoiced. You can now start syncing your data with QuickBooks Online by clicking **Synchronize**.

![QuickBooks Online Connected](../img/accounting-sync-quickbooks-online-connected.png)

No further action is required. You will be able to monitor the progress of your sync once it has started and view the results of past syncs.

![QuickBooks Online Invoice Sync](../img/quickbooks-online-invoice-sync.png)

Any time you want to sync your data with Xero just return to the **Accounting Sync** page and click **Synchronize**.

###Quickbooks Online Syncing Nuances 
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



###Quickbooks Online Troubleshooting

- If the sync fails first try to reconnect your Quickbooks Online account and try again.  If it still fails please contact [support@invoiced.com](mailto:support@invoiced.com) for further assistance.