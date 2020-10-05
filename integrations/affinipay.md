# AffiniPay Integration

This document details how to connect the [AffiniPay](https://affinipay.com) payment gateways (including CPACharge and LawPay) to accept payments and how our integration works.

## Capabilities

The AffiniPay payment gateway on Invoiced supports the following features:

Capability | Supported
-----------|------------
[Credit card payments](/resources/docs/payments/card) | &#10003;
[ACH payments](/resources/docs/payments/ach) | &#10003;
Vaulting cards | &#10003;
Vaulting bank accounts | &#10003;
[AutoPay](/resources/docs/payments/autopay) | &#10003;
Level 3 Processing | &mdash;
Apple Pay | &mdash;
Multi-currency | USD and CAD only
Refunds | &#10003;

## Supported Gateways

The AffiniPay integration works with each AffiniPay brand, including:

- [AffiniPay](https://affinipay.com)
- [CPACharge](https://cpacharge.com)
- [LawPay](https://lawpay.com)

## Setup

Connecting AffiniPay is a straightforward process. Follow these steps to start accepting payments through AffiniPay in minutes. These steps assume you already have a AffiniPay account.

1. From the Invoiced dashboard go to **Settings** &rarr; **Payments**.

2. Click **Setup** on the payment method you want to accept

3. Click **Connect Payment Gateway**.

4. Select **AffiniPay**, **CPACharge**, or **LawPay** as the payment gateway. We will select LawPay in this example.

5. Click **Connect to LawPay**. You will be taken to a screen to sign into your LawPay account, if you are not already signed in. Enter in your LawPay username and password and click **Sign In**.

6. You then need to authorize the Invoiced application by clicking  **Authorize**.

7. Your LawPay account is now connected and the payment method is enabled.

8. You might need to change the default AffiniPay account that will be used to receive payments. We will select the operating account by default, however, you may wish to receive payments in a different account.

## Using Multiple Accounts (Trust or Operating)

We support working with multiple merchant accounts on LawPay for the purpose of trust accounting. The default is for invoice payments to go to your operating account, however, you can also choose on the invoice level whether received payments should go in your trust or operating account. Please follow the instructions below to use this feature:

1. Go to the new invoice screen.

2. Click **Options** in the top right. You should see a *Merchant Account* option if you have multiple LawPay accounts. Select the account where payment should go for this invoice.

4. Finish creating your invoice as normal.

## Client Workflow

### Credit Cards

Paying with credit or debit card is fairly straightforward for customers. They simply enter in their cardholder information and click **Pay**. We give receipts to your customers after a successful payment.

[![Pay Invoice with Credit Card](/docs/img/pay-invoice-credit-card.png)](/docs/img/pay-invoice-credit-card.png)

### ACH

Customers can pay with ACH just as easily as with credit cards. The key difference is that ACH payments will take several business days to clear. When customers are on a payment form they will select ACH as the payment information and then enter in their bank account and routing number.

[![Pay Invoice with ACH](/docs/img/pay-invoice-ach.png)](/docs/img/pay-invoice-ach.png)

## Support

Need help with your AffiniPay account? You can get help through the [AffiniPay support center](https://affinipay.com/support/) or by calling 1-855-656-4685.