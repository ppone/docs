# Salesforce Integration

The Invoiced for Salesforce app adds accounts receivable automation capabilities to Salesforce. Installing the native Salesforce app allows you to sync Invoiced billing data with Salesforce.

[![Invoiced Salesforce Integration](docs/blob/master/img/salesforce-integration.png)](docs/blob/master/img/salesforce-integration.png)

## Capabilities

The Salesforce integration can synchronize the following data with Invoiced. Since most of these are not standard Salesforce objects, our app will install the custom objects and custom fields needed to give you these new capabilities. 
- Accounts (Customers)
- Contacts
- Invoices
- Credit Notes
- Estimates
- Subscriptions
- Payments
- Payment Methods (Credit Cards and Bank Accounts)
- Notes
- Emails

## Setup

The package can be installed in any Salesforce org, including Developer and Sandbox editions

1. [Install the package here](https://login.salesforce.com/packaging/installPackage.apexp?p0=04t1U000007LnPq)

   Note: If you are installing into a sandbox organization you must replace the initial portion of the URL with https://test.salesforce.com

   [![Salesforce App Install](/docs/img/salesforce-app-install.png)](/docs/img/salesforce-app-install.png)

2. Obtain an API key from the Invoiced dashboard. You can do this in **Settings** &rarr; **Developers** &rarr; **New API Key**.

   [![Salesforce API Key](/docs/img/salesforce-api-key.png)](/docs/img/salesforce-api-key.png)

3. Now you need to add your Invoiced API key to the package. Go to the Invoiced application from the Salesforce app launcher. Click on the **Settings** page at the top of the screen. Click on the **Connection** tab.

   [![Salesforce Connection Setup](/docs/img/salesforce-connection-setup.png)](/docs/img/salesforce-connection-setup.png)

4. Enter in the secret of the API key that you just created into the API Key field on Salesforce. If you are connecting to an Invoiced sandbox account then check the *Use Invoiced Sandbox* option.

   If you have an Invoiced multi-entity setup then check the *Enable Multi-Entity Support* checkbox.

5. Click **Save Settings** to enable the Salesforce integration.

6. Click on the **Sync** tab. Check the syncs you want to enable and click **Save Settings**.

   [![Salesforce Connection Setup](/docs/img/salesforce-sync-settings.png)](/docs/img/salesforce-sync-settings.png)

7. Then click **Enable Syncing** at the top of the screen.

   [![Salesforce Enable Sync](/docs/img/salesforce-enable-sync.png)](/docs/img/salesforce-enable-sync.png)

8. Add customizations to Account Layout to add fields you wish to see:
   - Account Balance
   - Create on Invoiced
   - Billing Email
   - Invoiced Entity

9. Add related lists to Account Layout you wish to see:
   - Invoices
   - Estimates
   - Credit Notes
   - Payments
   - Subscriptions
   - Credit Cards
   - Bank Accounts

10. Now you will start to see data syncing between the two systems.
