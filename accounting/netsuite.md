# NetSuite

Invoiced integrates with NetSuite out of the box, a cloud-based ERP system. This document outlines how to setup and use the NetSuite integration.

## Overview

The NetSuite integration ships with the following capabilities:

- Importing outstanding invoices from NetSuite
- Importing customers from NetSuite
- Reconciling payments received on Invoiced to NetSuite
- Syncing payments recorded on NetSuite to Invoiced

[![NetSuite Data Flow](/docs/img/netsuite-object-mapping.png)](/docs/img/netsuite-object-mapping.png)

## Setup

In order to set up the NetSuite integration you first need these pieces of information:
- NetSuite Account ID
- OAuth Access Token

Below we will show you how to connect NetSuite with Invoiced, step-by-step.

### Install The Invoiced SuiteBundle
First we need to install the Invoiced SuiteBundle, which will install an **Invoiced** integration and an **Invoiced Integration** role.

1. On NetSuite, go to **Customization** &rarr; **SuiteBundler** &rarr; **Search & Install Bundles**.

   [![Bundles Navigation](/docs/img/netsuite-suite-bundle.png)](/docs/img/netsuite-suite-bundle.png)

2. In the keyword box, type in *Invoiced* and click **Search**.  Select the bundle with a bundle ID of *265184*.
 
   [![Search Bundle](/docs/img/netsuite-choose-invoiced.png)](/docs/img/netsuite-choose-invoiced.png)

3. Click **Install** to install the bundle.

   [![Install Bundle](/docs/img/netsuite-bundle-install.png)](/docs/img/netsuite-bundle-install.png)

4. Once the bundle is installed, go to **Setup** &rarr; **Company** &rarr; **General Preferences**. Select the **Custom Preferences** tab.

   [![Custom Preferences](/docs/img/netsuite-custom-preferences.png)](/docs/img/netsuite-custom-preferences.png)

5. Obtain an API key in **Settings** &rarr; **Developers** &rarr; **New API Key** in the Invoiced application.

   [![New API Key](/docs/img/netsuite-new-api-key.png)](/docs/img/netsuite-new-api-key.png)

6. Paste the API key into the **Invoiced API Key** field on NetSuite and click **Save**.

### Setting Up an OAuth Access Token

The next step is to create an OAuth Access Token for Invoiced on NetSuite. To do that there are few steps you need to follow.

#### Assign the Invoiced Integration role to a user

You will need to pick a user that will that the access token will be based on and assign the **Invoiced Integration** role to that user.

1. Go to **Setup** &rarr; **Users/Roles** &rarr; **Manage Users**.

   [![Integration Settings](/docs/img/netsuite-manage-users.png)](/docs/img/netsuite-manage-users.png)

2.  Select the user you plan to use for the integration and add the **Invoiced Integration** role to that user.

   [![Integration Settings](/docs/img/netsuite-user-add-webservices.png)](/docs/img/netsuite-user-add-webservices.png)

#### Create the access token

1. Go to **Setup** &rarr; **Users/Roles** &rarr; **Access Tokens** &rarr; **New**

   [![Integration Settings](/docs/img/netsuite-create-accesstoken.png)](/docs/img/netsuite-create-accesstoken.png)

2. Select *Invoiced* as the application name, the user from the previous step as the user, and *Invoiced Integration* as the role.

   [![Integration Settings](/docs/img/netsuite-add-access-token.png)](/docs/img/netsuite-add-access-token.png)

3. Copy-paste the token ID and token secret values into a text editor. NetSuite will not display this information again.

### Connecting NetSuite on Invoiced

1. On Invoiced, go to **Settings** &rarr; **Integrations** in the Invoiced dashboard.

2. Click on **Connect** on the NetSuite integration.

   [![Connect NetSuite](/docs/img/connect-netsuite.png)](/docs/img/connect-netsuite.png)

3. Enter in the NetSuite account ID, token, and token secret for the Invoiced integration created earlier.

4. Click **Save**. NetSuite is now connected!

## Usage

Once the integration is configured and the bundle is installed, new transactions will begin to sync with NetSuite automatically. If you wish to import existing customers or invoices please continue reading.

### Import Existing Invoices

You can import outstanding invoices from NetSuite using the invoice importer. This is useful after setting up the integration to pull in invoices that were created before the integration was installed.

Instructions:

1. Go to the **Invoices** tab in the Invoiced dashboard. Click on the **Import** button in the top-right.

   [![Invoices Page](/docs/img/invoices-header.png)](/docs/img/invoices-header.png)

2. Select **NetSuite**.

   [![Invoice Importer](/docs/img/invoice-importer.png)](/docs/img/invoice-importer.png)

3. When ready to import, click **Start**.

   [![Start NetSuite Invoice Import](/docs/img/netsuite-invoice-importer-options.png)](/docs/img/netsuite-invoice-importer-options.png)

4. The importer will begin working. You are free to leave the page once the import starts. If you leave you will get an email afterwards with the result.

   [![NetSuite Invoice Import Started](/docs/img/netsuite-invoice-importer-pending.png)](/docs/img/netsuite-invoice-importer-pending.png)

5. Once the import is finished you will see the newly imported invoices on the **Invoices** page.

   [![NetSuite Invoice Import Finished](/docs/img/netsuite-invoice-importer-finished.png)](/docs/img/netsuite-invoice-importer-finished.png)

### Import Entire Customer List

You can import customers from NetSuite into Invoiced as a one-time import. Why might you use this? The sync process will only import customers that have invoices, whereas a manual import will bring in your entire A/R customer list.

Instructions:

1. Go to the **Customers** tab in the Invoiced dashboard. Click on the **Import** button in the top-right.

   [![Customers Page](/docs/img/customers-header.png)](/docs/img/customers-header.png)

2. Select **NetSuite**.

   [![Customer Importer](/docs/img/customer-importer.png)](/docs/img/customer-importer.png)

3. Click **Start**.

   [![Start NetSuite Customer Import](/docs/img/netsuite-customer-importer.png)](/docs/img/netsuite-customer-importer.png)

4. The importer will begin working. You are free to leave the page once the import starts. If you leave you will get an email afterwards with the result.

   [![NetSuite Customer Import Started](/docs/img/netsuite-customer-importer-pending.png)](/docs/img/netsuite-customer-importer-pending.png)

5. Once the import is finished you will see the newly imported invoices on the **Customers** page.

   [![NetSuite Customer Import Finished](/docs/img/netsuite-customer-importer-finished.png)](/docs/img/netsuite-customer-importer-finished.png)

## Edge Cases

Here we have documented all of the limitations, nuances, and edge cases to be aware of when using the NetSuite integration.

- Customers on Invoiced are mapped to customers on NetSuite by the customer name.

## Troubleshooting

When a sync fails you can check the SuiteScript logs in NetSuite.

If you are still unable to get your data synced then please contact [support@invoiced.com](mailto:support@invoiced.com) for further assistance.

### Finding Your NetSuite Account ID

Your NetSuite account ID is required in order to connect the integration. You can obtain your account ID from NetSuite with these steps:

1. Within the NetSuite application, hover over the **Setup** tab and click **Company** &rarr; **Company Information**.

   [![Integration Settings](/docs/img/netsuite-account-id.png)](/docs/img/netsuite-account-id.png)

2. You should see an *Account ID* field. This is the account ID that you will use in the connection steps.