# Salesforce Integration

We have built an integration with the Salesforce CRM in order to provide a complete order-to-cash workflow.

## Setup

Below we will walk you through how to set up the Salesforce integration on Invoiced.

1. Go to **Settings** > **Integrations** in the Invoiced dashboard.

   [![Integration Settings](../img/integration-settings.png)](../img/integration-settings.png)

2. Click **Connect to Salesforce**. You should be taken to a Salesforce login screen.

   [![Salesforce Login](../img/salesforce-connect-login.png)](../img/salesforce-connect-login.png)

3. Sign into Salesforce if you are not signed in already.

   [![Authorize Invoiced app](../img/salesforce-connect-authorization.png)](../img/salesforce-connect-authorization.png)

4. Next authorize the Invoiced application access to your Salesforce account by clicking **Allow**.

5. Salesforce is now connected! You will be redirected to the **Sync Manager** tab.

## Usage

The Salesforce integration works by importing non-draft orders from Salesforce and converting them into invoices.

1. Go to the **Sync Manager** tab in the Invoiced dashboard.

   [![Sync Manager](../img/salesforce-sync-manager.png)](../img/salesforce-sync-manager.png)

2. Click **Run** next to the **Salesforce Orders** section.

   [![Salesforce Import Pending](../img/salesforce-import-pending.png)](../img/salesforce-import-pending.png)

3. Wait for the import to finish.

   [![Salesforce Import Finished](../img/salesforce-import-finished.png)](../img/salesforce-import-finished.png)

4. Once the import is finished you can go to the **Invoices** tab to see the invoices for the imported orders.

   [![Salesforce Imported Invoice](../img/salesforce-imported-invoice.png)](../img/salesforce-imported-invoice.png)

## Help

Please contact [support@invoiced.com](mailto:support@invoiced.com) if you have any questions or feedback on the Salesforce integration.