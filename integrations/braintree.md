# Braintree Integration

This document details how to connect the [Braintree](https://braintreepayments.com) payment gateway to accept payments and how our integration works.

## Capabilities

The Braintree payment gateway on Invoiced supports the following features:

- [Credit card payments](/resources/docs/payments/card)
- Vaulting payment information
- [AutoPay](/resources/docs/payments/autopay)

## Setup

Connecting Braintree is a straightforward process. Follow these steps to start accepting payments through Braintree in minutes. These steps assume you already have a Braintree account.

1. From the Invoiced dashboard go to **Settings** &rarr; **Payments**.

   [![Payment Settings](/docs/img/payment-settings.png)](/docs/img/payment-settings.png)

2. Click **Setup** on the *Credit Card* payment method.

   [![Credit Card Payments Setup](/docs/img/credit-card-payment-setup.png)](/docs/img/credit-card-payment-setup.png)

3. Select **Braintree** as the payment gateway.

   [![Braintree Payments Setup](/docs/img/braintree-setup.png)](/docs/img/braintree-setup.png)

4. Click **Connect to Braintree**.

   [![Braintree Settings Page](/docs/img/braintree-connect.png)](/docs/img/braintree-connect.png)

5. Enter in your Braintree **Merchant ID**, **Merchant Account ID**, **Public Key**, and **Private Key** and click **Save**. Then click **Enable** and the credit card payments should be enabled.

   [![Braintree Payments Enabled](/docs/img/braintree-enabled.png)](/docs/img/braintree-enabled.png)

## Client Workflow

Paying with credit or debit card is fairly straightforward for customers. They simply enter in their cardholder information and click **Pay**. We give receipts to your customers after a successful payment.

[![Pay Invoice with Credit Card](/docs/img/pay-invoice-credit-card.png)](/docs/img/pay-invoice-credit-card.png)

## Support

Need help with your Braintree account? You can get help by visiting the [Braintree support site](https://www.braintreepayments.com/contact).