# PayPal Payments

[PayPal](https://paypal.com) is an online wallet that lets anyone securely pay merchants online without sharing payment information with the merchant.

## Setup

Setting up PayPal payments is easy! Follow these steps to start accepting PayPal payments in minutes.

1. From the Invoiced dashboard go to **Settings** > **Payments**.

   [![Online Payments](../img/invoice-online-payments.png)](../img/invoice-online-payments.png)

2. Click **PayPal** and enter in your PayPal email address. You can click on learn more to register for a PayPal account.

   [![PayPal Enabled](../img/invoice-enable-paypal.png)](../img/invoice-enable-paypal.png)

3. Click **Save** to enable PayPal.

## Client Workflow

On the payment page we will generate a **Pay with PayPal** button that takes your customer to PayPal's checkout process. There they will be able to pay using a PayPal account or submit a payment as a guest.

We will reconcile payments and refunds submitted through PayPal using the PayPal's [IPN](https://www.paypal.com/us/cgi-bin/webscr?cmd=p/acc/ipn-info-outside) feature.

## Withdrawing Money

Any PayPal payments will go to your PayPal balance, which you can withdraw or use to pay other merchants.