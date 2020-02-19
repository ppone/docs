# Authorize.Net Integration

This document details how to connect the [Authorize.Net](https://authorize.net) payment gateway to accept payments and how our integration works.

## Capabilities

The Authorize.Net payment gateway on Invoiced supports the following features:

- [Credit card payments](/resources/docs/payments/card)
- [ACH payments](/resources/docs/payments/ach) (U.S. only)
- Vaulting payment information (credit card and ACH)
- [AutoPay](/resources/docs/payments/autopay)

## Setup

Connecting Authorize.Net is a straightforward process. Follow these steps to start accepting payments through Authorize.Net in minutes. These steps assume you already have a Authorize.Net account.

1. From the Invoiced dashboard go to **Settings** &rarr; **Payments**.

   [![Payment Settings](/docs/img/payment-settings.png)](/docs/img/payment-settings.png)

2. Click **Setup** on the payment method you want to accept.

   [![Credit Card Payments Setup](/docs/img/credit-card-payment-setup.png)](/docs/img/credit-card-payment-setup.png)

3. Select **Authorize.Net** as the payment gateway.

   [![Authorize.Net Payments Setup](/docs/img/authorizenet-setup.png)](/docs/img/authorizenet-setup.png)

4. Click **Connect to Authorize.Net**.

   [![Authorize.Net Settings Page](/docs/img/authorizenet-connect.png)](/docs/img/authorizenet-connect.png)

5. Enter in your Authorize.Net **API Login ID** and **Transaction Key**. You can find your API credentials from the Authorize.Net Merchant Interface by following [these instructions](https://support.authorize.net/s/article/How-do-I-obtain-my-API-Login-ID-and-Transaction-Key).

6. Click **Save**. Then click **Enable** and the payment method you selected should be enabled.

   [![Authorize.Net Payments Enabled](/docs/img/authorizenet-enabled.png)](/docs/img/authorizenet-enabled.png)

## Client Workflow

### Credit Cards

Paying with credit or debit card is fairly straightforward for customers. They simply enter in their cardholder information and click **Pay**. We give receipts to your customers after a successful payment.

[![Pay Invoice with Credit Card](/docs/img/pay-invoice-credit-card.png)](/docs/img/pay-invoice-credit-card.png)

### ACH

Customers can pay with ACH just as easily as with credit cards. The key difference is that ACH payments will take several business days to clear. When customers are on a payment form they will select ACH as the payment information and then enter in their bank account and routing number.

[![Pay Invoice with ACH](/docs/img/pay-invoice-ach.png)](/docs/img/pay-invoice-ach.png)

## Support

Need help with your Authorize.Net account? You can get help through the [Authorize.Net support center](http://www.authorize.net/support/) or by calling 1-877-447-3938.