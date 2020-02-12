# Credit Card Payments

Accepting credit and debit cards is currently the quickest and easiest way to get paid online.

## Prerequisites

You must have an account with a payment processor that supports one of these [payment gateways](gateways). If you do not see your gateway listed then please contact us at [support@invoiced.com](mailto:support@invoiced.com) to discuss getting it added.

## Setup

Once you are established with a payment processor, setting up credit card payments is easy! Follow these steps to start accepting credit card payments in minutes.

1. From the Invoiced dashboard go to **Settings** &rarr; **Payments**.

   [![Payment Settings](../img/payment-settings.png)](../img/payment-settings.png)

2. Click **Setup** on the *Credit Card* payment method.

  [![Credit Card Payments Setup](../img/credit-card-payment-setup.png)](../img/credit-card-payment-setup.png)

3. Select your payment gateway and follow the on-screen instructions to connect your payment gateway.

## Client Workflow

Paying with credit or debit card is fairly straightforward for customers. When a customer is viewing a payment form they would select **Credit Card** as the payment method. Then they will enter in their card information and click pay. We will give them a receipt immediately following a successful payment.

[![Pay Invoice with Credit Card](/docs/img/pay-invoice-credit-card.png)](/docs/img/pay-invoice-credit-card.png)

## Virtual Terminal

Like customers, internal Invoiced users have the ability to apply a payment to an account with a credit card payment on an invoice. Whether a customer has saved a credit card payment method on file or has provided the user with the information, easily access the virtual terminal for payments by navigating to the invoice and selecting receive payment -> charge. From there, you can select the saved credit card or enter a new card for use.

[![Pay Invoice with credit card](/docs/img/card-terminal-payment.gif)](/card-terminal-payment.gif)

## AutoPay

Credit card payments work with [AutoPay](/docs/payments/autopay) when your customer has a saved card on file.

## Convenience Fees

Credit card payments support charging customers a convenience fee when they pay with a debit or credit card. A convenience fee is a % markup added to the final transaction amount. You may charge up to 4% convenience fees.

### Where convenience fees are applied
When enabled, convenience fees add a % fee to the total payment amount of any credit or debit card charge. Convenience fees are not applied towards outstanding balances.
- Payments in the customer portal, including invoice payments, estimate deposits, and sign up pages
- AutoPay payments
- Payments made through Virtual Terminal

### Setup

Convenience fees can be setup with the following instructions:

1. From the Invoiced dashboard go to **Settings** &rarr; **Payments**.

2. Click **Configure** on the *Credit Card* payment method.

3. In the **Convenience Fee** field enter the % you wish to charge, up to 4%.

  [![Convenience Fee Setup](../img/convenience-fee-setup.png)](../img/convenience-fee-setup.png)

4. Click **Save** to go live with convenience fees.

When a customer makes a payment with a credit or debit card they will see a warning on the payment page about the convenience fee.

[![Credit Card Convenience Fee](/docs/img/credit-card-convenience-fee.png)](/docs/img/credit-card-convenience-fee.png)