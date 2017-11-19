# Chase Paymentech Integration

This document details how to connect the [Chase Paymentech](https://www.chasepaymentech.com/) payment gateway to accept payments and how our integration works.

## Capabilities

The Chase Paymentech Orbital payment gateway on Invoiced supports the following features:

- [Credit card payments](/docs/payments/card)
- [ACH payments](/docs/payments/ach) (U.S. only)
- Vaulting payment information (credit card and ACH)
- [AutoPay](/docs/guides/autopay)

## Prerequisite

The Chase Paymentech integration uses the Orbital gateway with the Stratus Platform (BIN 000001). You need to make sure your gateway account is set up to process transactions for the right host platform.

## Setup

Connecting Chase Paymentech Orbital is a straightforward process. Follow these steps to start accepting payments through Chase Paymentech Orbital in minutes. These steps assume you already have a Chase Paymentech account.

1. From the Invoiced dashboard go to **Settings** > **Payments**.

   [![Payment Settings](../img/payment-settings.png)](../img/payment-settings.png)

2. Click **Setup** on the payment method you want to accept.

   [![Credit Card Payments Setup](../img/credit-card-payment-setup.png)](../img/credit-card-payment-setup.png)

3. Select **Chase Paymentech Orbital** as the payment gateway.

   [![Chase Paymentech Orbital Payments Setup](../img/chase-paymentech-setup.png)](../img/chase-paymentech-setup.png)

4. Click **Connect to Chase Paymentech Orbital**.

   [![Chase Paymentech Orbital Settings Page](../img/chase-paymentech-connect.png)](../img/chase-paymentech-connect.png)

5. Enter in your Chase Paymentech Orbital **Account ID** and **API Secret** and click **Save**. Then click **Enable** and the payment method you selected should be enabled.

   [![Chase Paymentech Orbital Payments Enabled](../img/chase-paymentech-enabled.png)](../img/chase-paymentech-enabled.png)

## Client Workflow

### Credit Cards

Paying with credit or debit card is fairly straightforward for customers. They simply enter in their cardholder information and click **Pay**. We give receipts to your customers after a successful payment.

[![Pay Invoice with Credit Card](/docs/img/pay-invoice-credit-card.png)](/docs/img/pay-invoice-credit-card.png)

### ACH

Customers can pay with ACH just as easily as with credit cards. The key difference is that ACH payments will take several business days to clear. When customers are on a payment form they will select ACH as the payment information and then enter in their bank account and routing number.

[![Pay Invoice with ACH](/docs/img/pay-invoice-ach.png)](/docs/img/pay-invoice-ach.png)

## Support

Need help with your Chase Paymentech Orbital account? You can get help by contacting your Chase account representative.