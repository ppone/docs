# Payment Plans

Payment plans allow your customers to agree to make installment payments to you within a specified timeframe. 

## How it works

A payment plan can be understood as an extension of the invoice due date. Typically an invoice has payment terms, such as NET 7. For example: An invoice billed on October 1 has a full balance due on October 8. Rigid due dates are not helpful in scenarios where you do not want to collect the full balance at once. This is where payment plans can help.

A payment plan describes a multi-step schedule for collecting payments on an invoice. When coupled with the [AutoPay](/resources/docs/payments/autopay) feature, the payment plan will completely automate the collection of payment for an invoice according to the payment schedule that you and your customer agree on. This ensures that you are always paid on time and saves your customer the hassle of remembering when to pay installment payments.

Consider this example:

A customer has purchased a water heater from you for $1,000. Perhaps that customer is not able to pay the entire balance up front, but you still want to work with them. With payment plans you can issue a $1,000 invoice for the work performed/ products sold, etc., except that you will establish a schedule agreed upon by you and your customer to pay off the invoice balance. Such a payment schedule might look like this:

*Installment 1*: $500 due on October 1st

*Installment 2*: $250 due on November 1

*Final Installment*: $250 due on November 15

Once your customer approves the payment plan they will be charged automatically for the installments on the date each payment is due. Invoiced will keep track of the installments as they become due, and update the invoice balance as payment is collected.

Payment plans differ from subscription billing in that neither the time between installment payments nor the installment amounts need to be uniform. Payment plans are attached to a single invoice, and thus can work with any schedule. 

*Please note*: Payment plans are limited in that the payment plan must add up to the invoice balance.

## Usage

Prerequisites:
- Your account must support [AutoPay](/resources/docs/payments/autopay).
- You have [created an invoice](/docs) with an outstanding balance.

### Creating a payment plan

After creating an invoice for a customer, you can now add a payment plan to allow for installments. Setting up a payment plan is simply building the installment schedule. Each step in the installment schedule represents the date and amount to be paid. Open the invoice that has the outstanding balance. Here, you will add a payment plan to allow the customer to pay off the balance.

Click *Actions* &rarr; *Add Payment Plan*. A new dialog will appear.

   [![Click to add a payment plan](/docs/img/add-payment-plan.png)](/docs/img/add-payment-plan.png)

Invoiced has a clever payment plan calculator that handles most common scheduling scenarios. Just input your constraints and it will calculate the installment schedule for you.



   [![Create a new payment plan](/docs/img/add-payment-plan-1.png)](/docs/img/add-payment-plan-1.png)


*Fixed Installment Amount*: This section allows you to enter a fixed amount you would like the customer to pay each payment. You will also need to add a Fixed Stop Date or a Fixed time between installments to calculate this.

*Fixed # of Installments*: This allows you to set the number of payments you would like the customer to pay. Simply add a number and it will calculate each payment. You will also need to add a Fixed Stop Date or a Fixed time between installments to calculate this.

*Fixed time Between Installments:* This allows you to set a daily, weekly, monthly, or yearly time between the payments. Note: You will need to add a stop date to this. 


Once you are finished adding your installments then you can save the payment plan. We recommend double-checking that the installments have the correct dates and amounts before clicking *Save*. It's not possible to edit a payment plan once created. Instead you would have to cancel the payment plan and start over.

If your payment plan is not uniform, or needs further customization then you can switch the schedule to **Custom**. This will give you fine-grained control over the installment schedule.

   [![Build a custom payment plan](/docs/img/payment-plan-custom.png)](/docs/img/payment-plan-custom.png)

   If your customer already has payment information on file then there's nothing left to do. AutoPay will be enabled on the invoice and payment will be collected according to your newly created schedule.

   [![Payment plan started](/docs/img/payment-plan-enabled.png)](/docs/img/payment-plan-enabled.png)


If your customer does not have payment information on file yet, please read the next section to learn how to finish enrolling the customer in the payment plan.

##Signing up customers

Customers that do not have payment information on file must approve the payment plan and enter in their payment information before installments can be collected. They can do this by viewing the invoice online.

   [![Payment plan pending approval](/docs/img/confirming-payment-plan.png)](/docs/img/confirming-payment-plan.png)


1. Send the invoice with the payment plan to your customer.

2. Your customer will then open the email from you and click *View Invoice*.

3. Your customer will then click *Pay*.

4. Instead of the normal payment screen the customer will see the payment plan. After reviewing the payment plan they will click *Approve*.

   [![Payment plan email](/docs/img/payment-plan-approval.png)](/docs/img/payment-plan-approval.png)

5. Finally, they will need to add payment information to pay for the payment plan.

*Please Note*: AutoPay for the invoice will be enabled now that your customer has approved the payment plan and payment information on file. Invoiced will then automatically collect the correct amount from your customer as each installment becomes due.

## FAQ

### How do I manually trigger a collection attempt?

As with all AutoPay invoices, you can manually trigger a collection attempt before Invoiced does automatically performs collection. When a payment plan is attached, then instead of collecting the full invoice balance, Invoiced will only collect the amount of the next installment. This might be useful if your customer wants the next installment to be collected a few days earlier.

### How do I edit or cancel active payment plans?

Once a payment plan is running then the payment plan cannot be edited. With the invoice open, just click **Cancel** in the *Payment Plan* section to instantly stop the payment plan. If needed, you can re-add a new payment plan.

Please keep in mind if there were any previously received payments that replacing the payment plan with a new one must add up to the current balance, and not the original balance.

### When are payment plan installments collected?

Payment plan installments will be collected on the day the installment is due. Generally this will be at the beginning of the day, however, the specific time might vary.

### How are failed payments handled?

Just like any other [failed AutoPay attempt](/resources/docs/payments/autopay#failed-payments), we will contact the customer for you with the reason the payment failed and the option to update their payment information. We will also schedule retries according to your payment retry schedule. The installment will not be marked as paid until the amount is collected successfully.

### How can customers see the current balance?

Customers can open the invoice at any point to see the current balance. As installments are collected the invoice balance will be updated to reflect the remaining amount that is due. With a payment plan attached to an invoice, the payment terms will be *Payment Plan* to reflect how payment is being collected and customer will not be able to manually pay the invoice. Otherwise, an invoice with a payment plan behaves like any other invoice.