# Worldpay Integration

This document details how to connect the [Worldpay](https://worldpay.com) payment gateway to accept payments and how our integration works.

## Capabilities

The Worldpay payment gateway on Invoiced supports the following features:

- [Credit card payments](/docs/payments/card)
- [ACH payments](/docs/payments/ach) (U.S. only)
- Vaulting payment information (credit card and ACH)
- [AutoPay](/docs/guides/autopay)

## Setup

Connecting Worldpay is a straightforward process. Follow these steps to start accepting payments through Worldpay in minutes. These steps assume you already have a Worldpay account.

1. From the Invoiced dashboard go to **Settings** > **Payments**.

   [![Payment Settings](../img/payment-settings.png)](../img/payment-settings.png)

2. Click **Setup** on the payment method you want to accept.

   [![Credit Card Payments Setup](../img/credit-card-payment-setup.png)](../img/credit-card-payment-setup.png)

3. Select **Worldpay** as the payment gateway.

   [![Worldpay Payments Setup](../img/worldpay-setup.png)](../img/worldpay-setup.png)

4. Click **Connect your Worldpay account**.

   [![Worldpay Settings Page](../img/worldpay-connect.png)](../img/worldpay-connect.png)

5. Enter in your Worldpay **Account ID**, **Sub ID**, and **Merchant PIN** and click **Save**. Then click **Enable** and the payment method you selected should be enabled.

   [![Worldpay Payments Enabled](../img/worldpay-enabled.png)](../img/worldpay-enabled.png)

## Client Workflow

### Credit Cards

Paying with credit or debit card is fairly straightforward for customers. They simply enter in their cardholder information and click **Pay**. We give receipts to your customers after a successful payment.

[![Pay Invoice with Credit Card](/docs/img/pay-invoice-credit-card.png)](/docs/img/pay-invoice-credit-card.png)

### ACH

Customers can pay with ACH just as easily as with credit cards. The key difference is that ACH payments will take several business days to clear. When customers are on a payment form they will select ACH as the payment information and then enter in their bank account and routing number.

[![Pay Invoice with ACH](/docs/img/pay-invoice-ach.png)](/docs/img/pay-invoice-ach.png)

## Support

When you signed up for Worldpay you should have received an onboarding packet. This will contain the contact information for getting swift help from Worldpay.