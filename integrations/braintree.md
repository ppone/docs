# Braintree Integration

This document details how to connect the [Braintree](https://braintreepayments.com) payment gateway to accept payments and how our integration works.

## Capabilities

The Braintree payment gateway on Invoiced supports the following features:

Capability | Supported
-----------|------------
[Credit card payments](/resources/docs/payments/card) | &#10003;
[ACH payments](/resources/docs/payments/ach) | &mdash;
Vaulting cards | &#10003;
[AutoPay](/resources/docs/payments/autopay) | &#10003;
Level 3 Processing | &mdash;
Apple Pay | &mdash;
Multi-currency | &#10003;
Refunds | &#10003;

## Setup

Connecting Braintree is a straightforward process. Follow these steps to start accepting payments through Braintree in minutes. These steps assume you already have a Braintree account.

1. From the Invoiced dashboard go to **Settings** &rarr; **Payments**.

2. Click **Setup** on the *Credit Card* payment method.

3. Select **Braintree** as the payment gateway.

4. Click **Connect to Braintree**.

5. Enter in your Braintree **Merchant ID**, **Merchant Account ID**, **Public Key**, and **Private Key** and click **Save**. Then click **Enable** and the credit card payments should be enabled.

## Client Workflow

Paying with credit or debit card is fairly straightforward for customers. They simply enter in their cardholder information and click **Pay**. We give receipts to your customers after a successful payment.

[![Pay Invoice with Credit Card](/docs/img/pay-invoice-credit-card.png)](/docs/img/pay-invoice-credit-card.png)

## Support

Need help with your Braintree account? You can get help by visiting the [Braintree support site](https://www.braintreepayments.com/contact).