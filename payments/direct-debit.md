# Direct Debit Payments

[Direct debit payments](https://en.wikipedia.org/wiki/Direct_debit) allow customers to pay invoices with their bank account. Currently companies can process direct debits on Invoiced using these banking schemes:

- Bacs debits (UK)
- SEPA debits (EU)
- BECS debits (Australia)
- Autogiro debits (Sweden)
- ACH (US)

Please note, if you are looking for the U.S. equivalent of direct debit then please take a look at our [ACH documentation](/docs/payments/ach).

## Prerequisites

You must have an account with a payment processor that allows direct debit payment processing. We recommend [GoCardless](/docs/integrations/gocardless) for direct debit payments.

## Setup

Setting up direct debit payments is a straightforward process.

1. From the Invoiced dashboard go to **Settings** > **Payments**.

   [![Payment Settings](../img/payment-settings-eu.png)](../img/payment-settings-eu.png)

2. Click **Setup** on the *Direct Debit* payment method. Continue following the instructions to configure your payment gateway. For example, if you are using GoCardless then you can see the [setup process here](/docs/integrations/gocardless#setup).

## Client Workflow

Paying with direct debit has been made as straightforward as possible for customers. When a customer goes to make their first payment they must first accept the direct debit mandate. In order to kick off the process your customer will click **Setup Direct Debit**.

[![Pay Invoice with Direct Debit](/docs/img/pay-invoice-direct-debit.png)](/docs/img/pay-invoice-direct-debit.png)

Once the direct debit mandate has been completed then your customer can now use their bank account to pay any invoice from you by returning to the invoice payment page and selecting their bank account as the payment method.

[![GoCardless Direct Debit Payment](../img/pay-invoice-direct-debit-2.png)](../img/pay-invoice-direct-debit-2.png)

New direct debit payments will have a pending status. Direct debit payments generally take 4-5 business days to complete. Once the transaction succeeds or fails we will update the invoice and send the customer a receipt. In the event of a failure we will create an event in the dashboard.

Subsequent payments from the same customer will not require the customer to go complete another mandate.

## AutoPay

Direct debit payments work with [AutoPay](/docs/payments/autopay) when your customer completes a direct debit mandate.

## Learn More

If you want to learn more about setting up the GoCardless integration for direct debit payments then please head over to our [GoCardless documentation](/docs/integrations/gocardless).