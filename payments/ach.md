# ACH Payments

[ACH](https://en.wikipedia.org/wiki/Automated_Clearing_House) payments allow customers to pay online using a bank account. Payments happen through the ACH network, an electronic network for financial transactions in the United States. The primary benefit of ACH payments is the low transaction fee, particularly on larger transactions.

*Stripe currently charges *0.8%* up to a maximum of *$5* for ACH transactions.*

The tradeoff when accepting ACH is that payments do not happen instantly like credit cards. Instead they take 3-7 business days to clear. There is also an additional one-time verification step that your customer must complete when paying with a new bank account.

## Setup

Setting up ACH payments is easy! Follow these steps to start accepting ACH payments in minutes.

1. From the Invoiced dashboard go to **Settings** > **Payments**.

   [![Online Payments](../img/invoice-online-payments.png)](../img/invoice-online-payments.png)

2. Click **ACH** > **Connect With Stripe**.

   If you don't have a Stripe account yet, don't worry. The connect button will walk you through creating an account. It's a single form that takes minutes. Once completed you can start accepting payments right away.

3. Accept the [Stripe ACH Terms of Service](https://stripe.com/docs/ach)

   Please make sure you are first signed into your Stripe account in order to accept the ToS. 

4. Click **Enable ACH Payments**.

## Client Workflow

When a customer decides to pay with ACH they must first connect a bank account and verify it. The verification process depends on where they bank.

### Instant Verification

We support instant verification for select banks, like Chase and Wells Fargo. Instant verification works by asking your client to securely sign into their online banking account to prove access. Once they sign in they will be able to select the account they want to pay with, all without ever having to enter a bank account and routing number.

### Manual Verification

All other bank accounts that do not support instant verification will require manual verification, also known as micro-deposit verification. The manual verification process makes two small, random deposits to your customer's bank account. We will then ask your customer to confirm the deposit amounts to prove ownership of the account. It generally takes 2 business days for the deposits to appear on the customer's bank statement.

### Paying

Once a bank account has been verified then your customer can now use it to pay any invoice from you by returning to the invoice payment page and selecting their bank account as the payment method.

New ACH payments will have a pending status. ACH payments generally take 3-5 business days to complete. Once the transaction succeeds or fails we will update the invoice and send the customer a receipt. In the event of a failure we will create an event in the dashboard.

Subsequent payments will not require the customer to go through the verification process again.

## AutoPay

ACH payments work with [AutoPay](/docs/guides/autopay) when your customer saves a bank account payment source.

## Withdrawing Money

You just received your first ACH payment (congrats!), now what?

ACH payments are not instant like credit card payments. An ACH payment will be marked as pending until the transaction has cleared. An ACH payment is not considered paid until the transaction has cleared.

ACH payments take up to 5 business days to receive acknowledgment of their success or failure. Because of this, ACH payments take up to 7 business days to be reflected in your available Stripe balance. You can learn more from [Stripe's ACH docs](https://stripe.com/docs/ach).

Stripe transfers incoming payments to your bank account automatically on a daily basis. Once you have received your first payment with Stripe the first transfer generally takes 7 business days. After that your transfers will happen on a 2-day or 7-day rolling basis depending on your account. You can learn more in [Stripe's transfer docs](https://stripe.com/help/transfers).