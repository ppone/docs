# Moneris Integration

This document details how to connect the [Moneris](https://moneris.com) payment gateway to accept payments and how our integration works.

## Capabilities

The Moneris payment gateway on Invoiced supports the following features:

- [Credit card payments](/docs/payments/card)
- [ACH payments](/docs/payments/ach)
- Vaulting payment information (credit card and ACH)
- [AutoPay](/docs/payments/autopay)

## Setup

Connecting Moneris is a straightforward process. Follow these steps to start accepting payments through Moneris in minutes. These steps assume you already have a Moneris account.

1. From the Invoiced dashboard go to **Settings** > **Payments**.

   [![Payment Settings](../img/payment-settings.png)](../img/payment-settings.png)

2. Click **Setup** on the payment method you want to accept.

   [![Credit Card Payments Setup](../img/credit-card-payment-setup.png)](../img/credit-card-payment-setup.png)

3. Select **Moneris** as the payment gateway.

   [![Moneris Payments Setup](../img/moneris-setup.png)](../img/moneris-setup.png)

4. Click **Connect to Moneris**.

   [![Moneris Settings Page](../img/moneris-connect.png)](../img/moneris-connect.png)

5. Enter in your Moneris **Store ID**, **API Token**, and **Processing Country** and click **Save**. Then click **Enable** and the payment method you selected should be enabled.

   [![Moneris Payments Enabled](../img/moneris-enabled.png)](../img/moneris-enabled.png)

## Client Workflow

### Credit Cards

Paying with credit or debit card is fairly straightforward for customers. They simply enter in their cardholder information and click **Pay**. We give receipts to your customers after a successful payment.

[![Pay Invoice with Credit Card](/docs/img/pay-invoice-credit-card.png)](/docs/img/pay-invoice-credit-card.png)

### ACH

Customers can pay with ACH just as easily as with credit cards. The key difference is that ACH payments will take several business days to clear. When customers are on a payment form they will select ACH as the payment information and then enter in their bank account and routing number.

[![Pay Invoice with ACH](/docs/img/pay-invoice-ach.png)](/docs/img/pay-invoice-ach.png)

## Support

Need help with your Moneris account? You can get help by contacting your Moneris account representative.