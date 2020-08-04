# ChartMogul Integration

Add subscription analytics to Invoiced with the ChartMogul integration. ChartMogul is the world's first subscription data platform that provides valuable insights into your billing data.

## How It Works

The ChartMogul integration will sync your billing data with ChartMogul on an ongoing basis. The integration syncs the following data:
* Customers
* Customer metadata
* Plans
* Invoices (recurring and one-off)
* Credit notes
* Payments
* Cancellations (canceled and finished subscriptions)

## Setup

The ChartMogul integration can be set up by following these steps:

1. Create a custom data source on ChartMogul.

2. Go to **Settings** &rarr; **Integrations** of the Invoiced application. Click **Connect** underneath the *ChartMogul* integration.

3. Enter in your ChartMogul Account Token, Secret Key, and UUID of the data source that was created in step 1. Click **Save** to finish the connection.

Once you have connected ChartMogul the application will begin syncing immediately. Depending on how much data you have, the first sync might take a long time to complete. You can check the sync status at any time by going to the ChartMogul integration settings. If there are any sync errors they will be presented here.

After the initial sync, the integration will send data to ChartMogul about once per hour.

## Limitations

* The integration does not sync refunds or failed payments.

* Only invoices paid in full will be marked as paid on ChartMogul. Partial payments are not supported by ChartMogul.

* Updates to invoices are not synced to ChartMogul. If you need to modify an invoice and wish to see it reflected in ChartMogul then you must delete it on ChartMogul first, or perform the edit on ChartMogul also.

* If you wish to change the billing interval of an existing plan then you must create a new plan with a new ID. Otherwise, the plan will continue to exist on ChartMogul with the old billing interval.