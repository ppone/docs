# Intuit QuickBooks Payments Integration

This document details how to connect the [Intuit QuickBooks](https://payments.intuit.com) payment gateway to accept payments and how our integration works.

## Capabilities

The Intuit QuickBooks Payments payment gateway on Invoiced supports the following features:

- [Credit card payments](/resources/docs/payments/card)
- [ACH payments](/resources/docs/payments/ach) (U.S. only)
- Vaulting payment information (credit card and ACH)
- [AutoPay](/resources/docs/payments/autopay)

## Setup

Connecting Intuit QuickBooks Payments is a straightforward process. Follow these steps to start accepting payments through Intuit QuickBook Payments in minutes. These steps assume you already have a Intuit QuickBooks Payments account.

1. From the Invoiced dashboard go to **Settings** &rarr; **Payments**.

   [![Payment Settings](/docs/img/payment-settings.png)](/docs/img/payment-settings.png)

2. Click **Setup** on the payment method you want to accept.

   [![Credit Card Payments Setup](/docs/img/credit-card-payment-setup.png)](/docs/img/credit-card-payment-setup.png)

3. Select **Intuit Payments** as the payment gateway.

   [![Intuit Payments Payments Setup](/docs/img/intuit-payments-setup.png)](/docs/img/intuit-payments-setup.png)

4. Click **Connect to QuickBooks**. 

   [![Intuit Payments Connection](/docs/img/intuit-payments-connect.png)](/docs/img/intuit-payments-connect.png)

5. Click **Authorize** to connect Invoiced. You should see that credit card and ACH payments are enabled.

   [![Intuit Payments Payments Enabled](/docs/img/intuit-payments-enabled.png)](/docs/img/intuit-payments-enabled.png)

## Client Workflow

### Credit Cards

Paying with credit or debit card is fairly straightforward for customers. They simply enter in their cardholder information and click **Pay**. We give receipts to your customers after a successful payment.

[![Pay Invoice with Credit Card](/docs/img/pay-invoice-credit-card.png)](/docs/img/pay-invoice-credit-card.png)

### ACH

Customers can pay with ACH just as easily as with credit cards. The key difference is that ACH payments will take several business days to clear. When customers are on a payment form they will select ACH as the payment information and then enter in their bank account and routing number.

[![Pay Invoice with ACH](/docs/img/pay-invoice-ach.png)](/docs/img/pay-invoice-ach.png)

## Support

Need help with your Intuit QuickBooks Payments account? You can get help on the [QuickBooks Payments support site](https://community.intuit.com/browse/quickBooks-online-payments).