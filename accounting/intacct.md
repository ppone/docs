# Sage Intacct

Invoiced integrates with Sage Intacct out of the box, a best-in-class cloud ERP. This document outlines how to setup and use the Intacct integration.

## Overview

The Intacct integration ships with the following capabilities:

- Importing outstanding invoices from Intacct
- Importing customers from Intacct
- Writing invoices generated on Invoiced to Intacct
- Reconciling payments received on Invoiced to Intacct
- Syncing payments recorded on Intacct to Invoiced

[![Intacct Data Flow](../img/intacct-object-mapping.png)](../img/intacct-object-mapping.png)

## Setup

In order to set up the Intacct integration you first need these pieces of information:
- Intacct Company ID
- Web services user

Below we will show you how to connect Intacct with Invoiced, step-by-step.

### Setting Up a Web Services User

The next step is to set up a web services user for Invoiced on Intacct. It is recommended that you use a dedicated web services user for Invoiced in order to ensure it has the correct permissions. We also recommend against using a non-web services user because any password changes would break the integration.

1. You need to ensure that your company has web services enabled on Intacct in **Company** > **Subscriptions**.

2. Within the Intacct application, hover over the **Company** tab and click the **+** button next to *Users*.

3. You will want to set up a user similar to the screenshot below with the following settings:

   - User ID: "invoiced"
   - First Name / Last Name: "Invoiced"
   - Email address: your shared accounting team email
   - User type: "Business"
   - Admin privileges: "Full"
   - Status: "Active"
   - Keep password until admin resets it: check this box
   - Restrict user access to web services only: check this box
   
   [![Intacct Web Services User Setup](../img/intacct-web-services-user.png)](../img/intacct-web-services-user.png)

4. Next you need to configure permissions for the Invoiced user. On the subscriptions page check the **Accounts Receivable** and **General Ledger** modules.

   [![Intacct Subscriptions Setup](../img/intacct-web-services-user-subscriptions.png)](../img/intacct-web-services-user-subscriptions.png)

5. Click on the **Permissions** button next to the Accounts Receivable module. Select the **All** radio in the top right. Click **Save**.

   [![Intacct Permissions Setup](../img/intacct-web-services-user-permissions.png)](../img/intacct-web-services-user-permissions.png)

6. Click on the **Permissions** button next to the General Ledger module. Select the **Read only** radio in the top right. Click **Save**.

7. Click **Save** on the subscriptions page. You should have received an email with the company ID, username, and password information.

### Connecting Intacct on Invoiced

1. Go to **Settings** > **Integrations** in the Invoiced dashboard.

   [![Integration Settings](../img/integration-settings.png)](../img/integration-settings.png)

2. Click on **Connect** on the Intacct integration.

   [![Connect Intacct](../img/connect-intacct.png)](../img/connect-intacct.png)

3. Enter in the Intacct company ID, username, and password for your Invoiced web services user created earlier. If you are using a shared multi-entity account then you can also enter in the entity ID you would like the connection to use.

4. Click **Save**. Intacct is now connected! Next you will want to configure the integration before using it.

   [![Intacct Integration Settings](../img/intacct-integration-settings.png)](../img/intacct-integration-settings.png)

5. You can customize the integration, including the account mapping into your general ledger and enabling automatic reconciliation. You can optionally enter in location ID and/or department ID dimensions if you want to tag the line items on Intacct that are created by the Invoiced sync with these dimensions. If you are importing invoices from Intacct then the dimension settings are irrelevant. Click **Save** to finish setting up the Intacct integration.

## Usage

In this section you will learn how to use the Intacct integration.

### Enabling Auto-Sync

Auto-sync will run accounting syncs automatically for you on an ongoing basis. Once auto-sync is enabled, accounting syncs will happen approximately once per hour. Here's how you can enable auto-sync:

1. Go to **Settings** > **Accounting Sync**. Click **Configure** on the Intacct integration.

   [![Intacct Accounting Sync](../img/intacct-accounting-sync-connected.png)](../img/intacct-accounting-sync-connected.png)

2. Enable the *Reconcile to Intacct* option.

   [![Intacct Integration Settings Enable Auto-Sync](../img/intacct-integration-settings.png)](../img/intacct-integration-settings.png)

3. Click **Save**. You can periodically check back here to see when the next sync run is scheduled or see past activity in the *Recent Syncs* table.

   [![Intacct Auto-Sync Enabled](../img/intacct-auto-sync-enabled.png)](../img/intacct-auto-sync-enabled.png)

### Running Syncs Manually

If you want control over when your books are synced then you can manually trigger accounting syncs. You can run an accounting sync by following these steps:

1. Go to **Settings** > **Accounting Sync**.

   [![Intacct Accounting Sync](../img/intacct-accounting-sync-connected.png)](../img/intacct-accounting-sync-connected.png)

2. Click **Sync Now** underneath *Intacct* any time you want to run an accounting sync. When the job is finished you will see it in the *Recent Syncs* table.

   [![Intacct Accounting Sync](../img/intacct-accounting-sync.png)](../img/intacct-accounting-sync.png)

### Manual Invoice Imports

You can import outstanding invoices from the Intacct Order Entry module using our Intacct invoice importer.

Instructions:

1. Go to the **Invoices** tab in the Invoiced dashboard. Click on the **Import** button in the top-right.

   [![Invoices Page](../img/invoices-header.png)](../img/invoices-header.png)

2. Select **Intacct**.

   [![Invoice Importer](../img/invoice-importer.png)](../img/invoice-importer.png)

3. Select the sales document type you would like to import, and when ready, click **Start**.

   [![Start Intacct Invoice Import](../img/intacct-invoice-importer-options.png)](../img/intacct-invoice-importer-options.png)

4. The importer will begin working. You are free to leave the page once the import starts. If you leave you will get an email afterwards with the result.

   [![Intacct Invoice Import Started](../img/intacct-invoice-importer-pending.png)](../img/intacct-invoice-importer-pending.png)

5. Once the import is finished you will see the newly imported invoices on the **Invoices** page.

   [![Intacct Invoice Import Finished](../img/intacct-invoice-importer-finished.png)](../img/intacct-invoice-importer-finished.png)

### Manual Customer Imports

You can import customers from Intacct into Invoiced as a one-time import. Why might you use this? The accounting sync will only import customers that have invoices, whereas a manual import will bring in your entire A/R customer list.

Instructions:

1. Go to the **Customers** tab in the Invoiced dashboard. Click on the **Import** button in the top-right.

   [![Customers Page](../img/customers-header.png)](../img/customers-header.png)

2. Select **Intacct**.

   [![Customer Importer](../img/customer-importer.png)](../img/customer-importer.png)

3. Click **Start**.

   [![Start Intacct Customer Import](../img/intacct-customer-importer.png)](../img/intacct-customer-importer.png)

4. The importer will begin working. You are free to leave the page once the import starts. If you leave you will get an email afterwards with the result.

   [![Intacct Customer Import Started](../img/intacct-customer-importer-pending.png)](../img/intacct-customer-importer-pending.png)

5. Once the import is finished you will see the newly imported invoices on the **Customers** page.

   [![Intacct Customer Import Finished](../img/intacct-customer-importer-finished.png)](../img/intacct-customer-importer-finished.png)

## Edge Cases

Here we have documented all of the limitations, nuances, and edge cases to be aware of when using the Intacct integration.

- Customers on Invoiced are mapped to customers on Intacct by the customer name.

- Only non-draft invoices on Invoiced that have been updated since the last sync will be synced. On your first sync this means that all non-draft invoices will be synced.

- Any changes to invoices imported from Intacct that are later modified on Invoiced will not be synced to Intacct. Payments processed through Invoiced for imported invoices will still be synced.

- Editing invoices imported from the Intacct Order Entry module, after they have been imported, can cause sync errors and might need to be reconciled by hand.

- When importing bill to contacts instead of customers, the customer on Invoiced will use the information from the bill to contact instead of the Intacct customer. This means the name and details will match the bill to contact, and will result in multiple Invoiced customers for a single Intacct customer. The customer number on Invoiced will be auto-generated and will not match the one on Intacct because there are multiple Invoiced customers that could have the same account number.

- If a credit is applied to an invoice in Invoiced to pay the entire invoice, the credit information will not be synced to Intacct.

- Applying a credit note to an invoice in Intacct to pay the entire invoice will not sync the credit payment to Invoiced.

- Applying a partial credit to an invoice in Intacct will sync as a partial payment to the invoice on Invoiced as other. Applying a partial credit in Intacct will sync to the invoice in Invoiced as a partial credit applied.

## Troubleshooting

When a sync fails you will be able to see the error message in the *Recent Syncs* section in **Settings** > **Accounting Sync**. Normally the error message will include the invoice # that failed and a detailed reason why it could not be synced. Oftentimes there is a manual action required on your end.

Below we have documented commonly encountered errors and recommended resolutions. If you are still unable to get your books synced then please contact [support@invoiced.com](mailto:support@invoiced.com) for further assistance.

### Finding Your Intacct Company ID

Your Intacct company ID is required in order to connect the integration. You can obtain your company ID from Intacct with these steps:

1. Within the Intacct application, hover over the **Company** tab and click **Company Info**.

2. You should see an *ID* field. This is the company ID that you will use in the connection steps.

### 401 Error

> non-200 status code: 401

We could not connect to Intacct using the credentials you provided. Please make sure the Intacct company ID, username, and password are correct.

### Numbering collision

> A transaction with the number 'XXX' already exists.

If you see this error message then there is already a different invoice with the same number on Intacct. It is recommended that you choose a unique invoice # for the invoice that is being synced.

### Please provide a payment batch key

> Please provide a payment batch key.

Change the Payments Summary frequency to either Daily or Monthly. To do so, complete the following steps in Intacct:

1. Hover over the Accounts Receivable tab
2. Click Configure Accounts Receivable
3. Scroll down to Summary Frequency in the Accounting Settings section
4. Change the Payments field to either Daily or Monthly and Save the changes
5. Retry the sync

### DL02000001 error

When an import fails with a `DL02000001` error code then that means the importer was trying to retrieve a field that did not exist on an Intacct object. This could happen if you have modified an object definition to remove or modify a standard field that our importer requests, or if you have configured the importer to pull in a custom field that does not exist on Intacct.

### Imported Intacct invoice no longer exists

> Intacct invoice with recordno = XXX, does not exist even though it was imported

When you see this error message then that means the original A/R invoice that was imported to Invoiced has been deleted on Intacct. In order to continue syncing payments please make sure not to remove imported invoices on Intacct. If the invoice no longer exists on Intacct then you can skip the invoice in future syncs and reconcile any payments received for the invoice by hand.