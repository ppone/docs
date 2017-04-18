# Payeezy Integration

This document details how to connect the [First Data Payeezy](https://payeezy.com) payment gateway to accept payments and how our integration works.

## Capabilities

The Payeezy payment gateway on Invoiced supports the following features:

- [Credit card payments](/docs/payments/card)
- [ACH payments](/docs/payments/ach) (U.S. only)
- Vaulting payment information (credit card only)
- [AutoPay](/docs/guides/autopay) (credit card only)

## Setup

Connecting Payeezy is a straightforward process. Follow these steps to start accepting payments through Payeezy in minutes. These steps assume you already have a Payeezy account.

1. From the Invoiced dashboard go to **Settings** > **Payments**.

   [![Payment Settings](../img/payment-settings.png)](../img/payment-settings.png)

2. Click **Setup** on the payment method you want to accept.

   [![Credit Card Payments Setup](../img/credit-card-payment-setup.png)](../img/credit-card-payment-setup.png)

3. Select **Payeezy** as the payment gateway.

   [![Payeezy Payments Setup](../img/payeezy-setup.png)](../img/payeezy-setup.png)

4. Click **Connect your Payeezy account**.

   [![Payeezy Settings Page](../img/payeezy-connect.png)](../img/payeezy-connect.png)

5. Enter in your Payeezy **Account ID** and **API Secret** and click **Save**. Then click **Enable** and the payment method you selected should be enabled.

   [![Payeezy Payments Enabled](../img/payeezy-enabled.png)](../img/payeezy-enabled.png)

## Client Workflow

### Credit Cards

Paying with credit or debit card is fairly straightforward for customers. They simply enter in their cardholder information and click **Pay**. We give receipts to your customers after a successful payment.

[![Pay Invoice with Credit Card](/docs/img/pay-invoice-credit-card.png)](/docs/img/pay-invoice-credit-card.png)

### ACH

Customers can pay with ACH just as easily as with credit cards. The key difference is that ACH payments will take several business days to clear. When customers are on a payment form they will select ACH as the payment information and then enter in their bank account and routing number.

[![Pay Invoice with ACH](/docs/img/pay-invoice-ach.png)](/docs/img/pay-invoice-ach.png)

## Support

Need help with your Payeezy account? You can get help by contacting your First Data account representative.