# ACH Payments

[ACH](https://en.wikipedia.org/wiki/Automated_Clearing_House) payments allow customers to pay online using a bank account. Payments happen through the ACH network, an electronic network for financial transactions in the United States. The primary benefit of ACH payments is the low transaction fee, particularly on larger transactions.

The tradeoff with ACH payments is that payments do not happen instantly like with credit card payments. ACH payments take 3-7 business days to clear through the ACH network.

## Prerequisites

You must have an account with a payment processor that supports one of these [payment gateways](gateways) and ACH payments. If you do not see your gateway listed then please contact us at [support@invoiced.com](mailto:support@invoiced.com) to discuss getting it added.

## Setup

Once you are established with a payment processor, setting up ACH payments is easy! Follow these steps to start accepting ACH payments in minutes.

1. From the Invoiced dashboard go to **Settings** &rarr; **Payments**.

   [![Payment Settings](/docs/img/payment-settings.png)](/docs/img/payment-settings.png)

2. Click **Setup** on the *ACH* payment method.

  [![ACH Setup](/docs/img/ach-setup.png)](/docs/img/ach-setup.png)

3. Select your payment gateway and follow the on-screen instructions to connect your payment gateway.

## Client Workflow

Customers can select the **ACH** payment method from payment forms. Most payment gateways will require the customer's bank account and routing number. This can be found on the bottom of a check. Some payment gateways, like Stripe, might require customers to verify their bank account once before they can make payments to you.

[![Pay Invoice with ACH](/docs/img/pay-invoice-ach.png)](/docs/img/pay-invoice-ach.png)

## Virtual Terminal

Like customers, internal Invoiced users have the ability to apply a payment to an account with an ACH payment method on an invoice. Whether a customer has saved an ACH payment method on file or has provided the user with the information, easily access the virtual terminal for payments by navigating to the invoice and selecting receive payment -> charge. From there, you can select the saved ACH payment method or enter a new ACH method.

[![Pay Invoice with ACH](/docs/img/ach-terminal-payment.gif)](/ach-terminal-payment.gif)

## AutoPay

ACH payments work with [AutoPay](/resources/docs/payments/autopay) when your customer has a saved bank account on file.