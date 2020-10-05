# Stripe Integration

This document details how to connect the [Stripe](https://stripe.com) payment gateway to accept payments and how our integration works.

## Capabilities

The Stripe payment gateway on Invoiced supports the following features:

Capability | Supported
-----------|------------
[Credit card payments](/resources/docs/payments/card) | &#10003;
[ACH payments](/resources/docs/payments/ach) | &#10003;
Vaulting cards | &#10003;
Vaulting bank accounts | &#10003;
[AutoPay](/resources/docs/payments/autopay) | &#10003;
Level 3 Processing | &mdash;
Apple Pay | &#10003;
Multi-currency | &#10003;
Refunds | &#10003;

## Setup

Connecting Stripe is a straightforward process. Follow these steps to start accepting payments through Stripe in minutes. These steps assume you already have a Stripe account. If not, then you can sign up for one at [stripe.com](https://stripe.com).

1. From the Invoiced dashboard go to **Settings** &rarr; **Payments**.

2. Click **Setup** on the payment method you want to accept.

3. Click **Connect Payment Gateway**.

4. Select **Stripe** as the payment gateway.

5. Click **Connect With Stripe**. You will be taken to Stripe's website where you can sign into your Stripe account and grant Invoiced access.

6. After you've connected your Stripe account then the payment method you selected should be enabled.

7. If you are accepting ACH payments then you also need to accept the [Stripe ACH Terms of Service](https://stripe.com/docs/ach).

   *Please make sure you are first signed into your Stripe account in order to accept the ToS.*

## Client Workflow

### Credit Cards

Paying with credit or debit card is fairly straightforward for customers. They simply enter in their cardholder information and click **Pay**. We give receipts to your customers after a successful payment.

[![Pay Invoice with Credit Card](/docs/img/pay-invoice-credit-card.png)](/docs/img/pay-invoice-credit-card.png)

### ACH

When a customer decides to pay with ACH they must first connect a bank account and verify it. The verification process depends on where they bank.

[![Stripe ACH Verification](/docs/img/stripe-add-bank-account.png)](/docs/img/stripe-add-bank-account.png)

**NOTE: Your Stripe account might have a dollar limit for individual ACH transactions, i.e. customers cannot submit payments greater than $2,000. We recommend checking with Stripe support to confirm if there are any ACH limits for your account and if it needs to be raised to accommodate the size of your transactions. This should be done before you allow customers to pay with ACH.**

#### Instant Verification

We support instant verification for select banks, like Chase and Wells Fargo. Instant verification works by asking your customer to securely sign into their online banking account to prove access. Once they sign in they will be able to select the account they want to pay with, all without ever having to enter a bank account and routing number.

[![Stripe Instant ACH Verification](/docs/img/stripe-ach-instant-verification.png)](/docs/img/stripe-ach-instant-verification.png)

#### Manual Verification

All other bank accounts that do not support instant verification will require manual verification, also known as micro-deposit verification. The manual verification process makes two small, random deposits to your customer's bank account. We will then ask your customer to confirm the deposit amounts to prove ownership of the account. It generally takes 2 business days for the deposits to appear on the customer's bank statement.

[![Stripe Manual ACH Verification](/docs/img/stripe-ach-manual-verification.png)](/docs/img/stripe-ach-manual-verification.png)

[![Stripe Manual ACH Verification Micro-Deposit](/docs/img/stripe-ach-manual-verification-2.png)](/docs/img/stripe-ach-manual-verification-2.png)

#### Paying with ACH

Once a bank account has been verified then your customer can now use it to pay any invoice from you by returning to the invoice payment page and selecting their bank account as the payment method.

New ACH payments will have a pending status. ACH payments generally take 3-5 business days to complete. Once the transaction succeeds or fails we will update the invoice and send the customer a receipt. In the event of a failure we will create an event in the dashboard.

Subsequent payments will not require the customer to go through the verification process again.

[![Stripe ACH Payment](/docs/img/stripe-ach-pay-invoice.png)](/docs/img/stripe-ach-pay-invoice.png)

## Withdrawing Money

You just received your first payment through Stripe. Congrats! Now what?

Stripe sweeps successful payments to your bank account automatically on a daily basis. Once you have received your first payment with Stripe the first payout generally takes 7 business days. After that your payouts will happen on a 2-day or 7-day rolling basis depending on your account. You can learn more in [Stripe's payout docs](https://support.stripe.com/topics/payouts).

### ACH Payment Settlement

ACH payments are not instant like credit card payments. An ACH payment will be marked as pending until the transaction has cleared. An ACH payment is not considered paid until the transaction has cleared.

ACH payments take up to 5 business days to receive acknowledgment of their success or failure. Because of this, ACH payments take up to 7 business days to be reflected in your available Stripe balance. You can learn more from [Stripe's ACH docs](https://stripe.com/docs/ach).

## Importing Customers from Stripe

In this section we will show you how to import customers and payment information from Stripe into Invoiced. The process is very straightforward and does not require that you handle or send us any sensitive payment information.

1. Go to the **Customers** page and click on the **Import** button in the top-right.

2. Click on **Stripe**.

3. Click **Start** to begin the import.

4. The import will begin. You can go elsewhere while you wait. If there is a large # of customers being imported then this could take several minutes.

5. Invoiced will send you an email when the import is done. When the import is finished all of your imported customers should be visible in the **Customers** page.

## Support

Need help with your Stripe account? You can get help from [Stripe's support website](https://support.stripe.com) or [contact Stripe directly](https://support.stripe.com/contact).