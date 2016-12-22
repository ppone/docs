# Credit Card Payments

Accepting credit and debit cards is currently the quickest and easiest way to get paid online.

*The downside of accepting credit card payments is that credit card payments are one of the more expensive payment methods for merchants. In most locations Stripe currently charges *2.9% + .30* per transaction, although this may vary by your country.*

## Setup

Setting up credit card payments is easy! Follow these steps to start accepting credit card payments in minutes.

1. From the Invoiced dashboard go to **Settings** > **Payments**.

   [![Online Payments](../img/invoice-online-payments.png)](../img/invoice-online-payments.png)

2. Click **Credit Card** > **Connect With Stripe**.

   If you don't have a Stripe account yet, don't worry. The connect button will walk you through creating an account. It's a single form that takes minutes to complete. Once completed you can start accepting payments right away.

   [![Credit Card Enabled](../img/invoice-enable-credit-card.png)](../img/invoice-enable-credit-card.png)

3. After you've connected your Stripe account then credit card payments should be enabled.

## Client Workflow

Paying with credit/debit card is fairly straightforward for clients. They simply enter the card information, the amount they want to pay, and click pay. We will give them a receipt following the transaction.

## AutoPay

Credit card payments work with [AutoPay](/docs/guides/autopay) when your customer saves their card as a payment source.

## Withdrawing Money

You just received your first credit card payment (congrats!), now what?

Stripe transfers incoming payments to your bank account automatically on a daily basis. Once you have received your first payment with Stripe the first transfer generally takes 7 business days. After that your transfers will happen on a 2-day or 7-day rolling basis depending on your account. You can learn more in [Stripe's transfer docs](https://stripe.com/help/transfers).