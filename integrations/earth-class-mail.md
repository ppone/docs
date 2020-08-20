# Earth Class Mail Integration

With Earth Class Mail you can add an integrated virtual lockbox to Invoiced. Earth Class Mail's CheckStream product gives you a physical address where customers can send checks. As checks are received they will be automatically opened, scanned, deposited, and added to Invoiced as a customer payment.

[![Earth Class Mail Integration](/docs/img/ecm-integration.png)](/docs/img/ecm-integration.png)

## Setup

We are going to walk you through setting up the Earth Class Mail integration. This assumes you have already signed up for an Earth Class Mail account. If not, you may [sign up here](https://www.earthclassmail.com/invoiced/).

1. Get your Lob API key from the Lob dashboard. This will be the *Secret API Key* for the *Live Environment*.

   [![Obtaining Earth Class Mail API Key](/docs/img/ecm-settings.png)](/docs/img/ecm-settings.png)

2. Go to **Settings** &rarr; **Integrations** of the Invoiced application. Click **Connect** underneath the *Earth Class Mail* integration.

3. Enter in your Earth Class Mail API key. Click **Save** to enable the integration. You are now ready to start receiving checks!

## Receiving checks

Checks received through your Earth Class Mail mailbox will appear within Invoiced. We check for new check deposits once per day. When a check is detected we will add it to Invoiced as an unapplied payment. All of the known metadata (amount, payer, check #) and the check image will be added to the payment. These will inform the cash application system to help you match the payment to an invoice.