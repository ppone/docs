# NetSuite

Invoiced integrates with NetSuite out of the box, a cloud-based ERP system. This document outlines how to setup and use the NetSuite integration.

## Overview

The NetSuite integration ships with the following capabilities:

- Importing outstanding invoices from NetSuite
- Importing customers from NetSuite
- Reconciling payments received on Invoiced to NetSuite
- Syncing payments recorded on NetSuite to Invoiced

[![NetSuite Data Flow](../img/netsuite-object-mapping.png)](../img/netsuite-object-mapping.png)

## Setup

In order to set up the NetSuite integration you first need these pieces of information:
- NetSuite Account ID
- OAuth Access Token

Below we will show you how to connect NetSuite with Invoiced, step-by-step.

### Install The Invoiced SuiteBundle
First we need to install the Invoiced SuiteBundle, which will install an **INVOICED** integration and a **Webservices-Invoiced** role.

1. On NetSuite, go to **Customization** &rarr; **SuiteBundler** &rarr; **Search & Install Bundles**.

   [![Bundles Navigation](../img/netsuite-suite-bundle.png)](../img/netsuite-suite-bundle.png)

2. In the keyword box, type in *Invoiced* and click **Search**.  Select the bundle with a bundle ID of *265184*.
 
   [![Search Bundle](../img/netsuite-choose-invoiced.png)](../img/netsuite-choose-invoiced.png)

3. Click **Install** to install the bundle.

   [![Install Bundle](../img/netsuite-bundle-install.png)](../img/netsuite-bundle-install.png)

4. Once the bundle is installed, go to **Setup** &rarr; **Company** &rarr; **General Preferences**. Select the **Custom Preferences** tab.

   [![Custom Preferences](../img/netsuite-custom-preferences.png)](../img/netsuite-custom-preferences.png)

5. Obtain an API key in **Settings** &rarr; **Developers** &rarr; **New API Key** in the Invoiced application.

   [![New API Key](../img/netsuite-new-api-key.png)](../img/netsuite-new-api-key.png)

6. Paste the API key into the **Invoiced API Key** field on NetSuite and click **Save**.

### Setting Up an OAuth Access Token

The next step is to create an OAuth Access Token for Invoiced on NetSuite. To do that there are few steps you need to follow.

#### Assign the Webservices-Invoiced role to a user

You will need to pick a user that will that the access token will be based on and assign the **Webservices-Invoiced** role to that user.

1. Go to **Setup** &rarr; **Users/Roles** &rarr; **Manage Users**.

   [![Integration Settings](../img/netsuite-manage-users.png)](../img/netsuite-manage-users.png)

2.  Select the user you plan to use for the integration and add the **Webservices-Invoiced** role to that user.

   [![Integration Settings](../img/netsuite-user-add-webservices.png)](../img/netsuite-user-add-webservices.png)

#### Create the access token

1. Go to **Setup** &rarr; **Users/Roles** &rarr; **Access Tokens** &rarr; **New**

   [![Integration Settings](../img/netsuite-create-accesstoken.png)](../img/netsuite-create-accesstoken.png)

2. Select *INVOICED* as the application name, the user from the previous step as the user, and *Webservices-Invoiced* as the role.

   [![Integration Settings](../img/netsuite-add-access-token.png)](../img/netsuite-add-access-token.png)

3. Copy-paste the token ID and token secret values into a text editor. NetSuite will not display this information again.

### Connecting NetSuite on Invoiced

1. On Invoiced, go to **Settings** &rarr; **Integrations** in the Invoiced dashboard.

   [![Integration Settings](../img/integration-settings.png)](../img/integration-settings.png)

2. Click on **Connect** on the NetSuite integration.

   [![Connect NetSuite](../img/connect-netsuite.png)](../img/connect-netsuite.png)

3. Enter in the NetSuite account ID, token, and token secret for the Invoiced integration created earlier.

4. Click **Save**. NetSuite is now connected! Next you will want to configure the integration before using it.

   [![NetSuite Integration Settings](../img/netsuite-integration-settings.png)](../img/netsuite-integration-settings.png)

5. After you customize the integration, click **Save** to finish setting up the NetSuite integration.

## Usage

Once the integration is configured and the bundle is installed, new transactions will begin to sync with NetSuite automatically. If you wish to import existing customers or invoices please continue reading.

### Import Existing Invoices

You can import outstanding invoices from NetSuite using the invoice importer. This is useful after setting up the integration to pull in invoices that were created before the integration was installed.

Instructions:

1. Go to the **Invoices** tab in the Invoiced dashboard. Click on the **Import** button in the top-right.

   [![Invoices Page](../img/invoices-header.png)](../img/invoices-header.png)

2. Select **NetSuite**.

   [![Invoice Importer](../img/invoice-importer.png)](../img/invoice-importer.png)

3. When ready to import, click **Start**.

   [![Start NetSuite Invoice Import](../img/netsuite-invoice-importer-options.png)](../img/netsuite-invoice-importer-options.png)

4. The importer will begin working. You are free to leave the page once the import starts. If you leave you will get an email afterwards with the result.

   [![NetSuite Invoice Import Started](../img/netsuite-invoice-importer-pending.png)](../img/netsuite-invoice-importer-pending.png)

5. Once the import is finished you will see the newly imported invoices on the **Invoices** page.

   [![NetSuite Invoice Import Finished](../img/netsuite-invoice-importer-finished.png)](../img/netsuite-invoice-importer-finished.png)

### Import Entire Customer List

You can import customers from NetSuite into Invoiced as a one-time import. Why might you use this? The sync process will only import customers that have invoices, whereas a manual import will bring in your entire A/R customer list.

Instructions:

1. Go to the **Customers** tab in the Invoiced dashboard. Click on the **Import** button in the top-right.

   [![Customers Page](../img/customers-header.png)](../img/customers-header.png)

2. Select **NetSuite**.

   [![Customer Importer](../img/customer-importer.png)](../img/customer-importer.png)

3. Click **Start**.

   [![Start NetSuite Customer Import](../img/netsuite-customer-importer.png)](../img/netsuite-customer-importer.png)

4. The importer will begin working. You are free to leave the page once the import starts. If you leave you will get an email afterwards with the result.

   [![NetSuite Customer Import Started](../img/netsuite-customer-importer-pending.png)](../img/netsuite-customer-importer-pending.png)

5. Once the import is finished you will see the newly imported invoices on the **Customers** page.

   [![NetSuite Customer Import Finished](../img/netsuite-customer-importer-finished.png)](../img/netsuite-customer-importer-finished.png)

## Edge Cases

Here we have documented all of the limitations, nuances, and edge cases to be aware of when using the NetSuite integration.

- Customers on Invoiced are mapped to customers on NetSuite by the customer name.

## Troubleshooting

When a sync fails you can check the SuiteScript logs in NetSuite.

If you are still unable to get your data synced then please contact [support@invoiced.com](mailto:support@invoiced.com) for further assistance.

### Finding Your NetSuite Account ID

Your NetSuite account ID is required in order to connect the integration. You can obtain your account ID from NetSuite with these steps:

1. Within the NetSuite application, hover over the **Setup** tab and click **Company** &rarr; **Company Information**.

   [![Integration Settings](../img/netsuite-account-id.png)](../img/netsuite-account-id.png)

2. You should see an *Account ID* field. This is the account ID that you will use in the connection steps.