# Invoiced Documentation

Welcome to Billing 101. We're going to walk you through using Invoiced to get paid. If you look at the left sidebar you will see that our documentation is broken up into sub-topics.

## Getting Started

In this tutorial we are going to show you how to issue your first invoice.

If you have not already then you need to [sign up](/signup) for an Invoiced account. We offer a 14-day free trial with no credit card or obligations required. During the onboarding process we will ask you a few questions about your business like what payment methods you want to accept. After you have set up your business then you will be signed into the dashboard.

The dashboard is where you can access all of your customer and billing data. Since it is a web application the only system requirement is a modern web browser. As a bonus the dashboard is responsive which means it can be used on any device, including desktops, tablets, and smartphones. This means you can run your business from anywhere (with Internet).

### Creating your first invoice

Creating an invoice is a fairly simple process. After all, it's the main thing that Invoiced was designed to do. If you click on the **Invoices** section in the left sidebar you will be taken to the invoices page. Then click the big **New Invoice** button.

[![Drafting First Invoice](/docs/img/drafting-first-invoice.png)](/docs/img/drafting-first-invoice.png)

Now you are inside of the invoice editor. Let's select the customer that we are invoicing. Click the dropdown where it says *Find or create client* and start typing your customer's name. Since that customer does not exist yet you need to click *Add Joe Customer as a new client*. A new dialog will appear where you can enter your customer's information.

[![Creating First Customer](/docs/img/create-first-customer.png)](/docs/img/create-first-customer.png)

How do you expect to get paid from this customer? When **AutoPay** is disabled (the default) your customer will be able to pay invoices using any of the payment methods you accept, according to the payment terms you specify. If you enable [AutoPay](autopay) then your customer's payment source will be charged for any invoices issued against their account.

For this example we're going to leave AutoPay disabled and use *Net 7* payment terms. This means that payment is due within 7 days. Once you have entered in your customer's information then you can click **Create**.

Selecting the customer will fill in the payment terms and due date on the invoice. All that remains is to add the line items.

[![Finished First Invoice](/docs/img/finished-first-invoice.png)](/docs/img/finished-first-invoice.png)

After building your line items you are ready to go. If you are not ready to go live with this invoice then you can save it as a draft. An invoice is not treated as outstanding until it has been issued. By clicking **Save and Issue** the invoice will be posted to the customer's account and is now considered due.

### Sending the invoice

Upon issuing the invoice we will ask if you want to send it. If you choose not to send it now you will have the option to send it later or else mark the invoice as sent if you sent the invoice using some other medium. Let's go ahead and send it now.

[![Sending First Invoice](/docs/img/sending-first-invoice.png)](/docs/img/sending-first-invoice.png)

The message will be populated with the default email template (hint: you can change the defaults in **Settings** > **Emails**). Whenever you click **Send** your customer will receive an email with your branding, your message, and a **View Invoice** button.

### Getting paid

When your customer clicks the **View Invoice** button they will be taken to the invoice in the billing portal. The billing portal is where customer's can view and pay invoices, in addition to having access to their past billing history. Another nifty feature is that once your customer views an invoice we will send you a notification to let you know they have seen it.

[![Client Invoice Email](/docs/img/client-invoice-email.png)](/docs/img/client-invoice-email.png)

This is what your client would see after clicking the view invoice button:

[![Invoice Client View](/docs/img/client-invoice-view.png)](/docs/img/client-invoice-view.png)

Here the client can leave a comment, download the invoice, and of course, pay it. In order to pay they would simply click the **Pay** button at the bottom of the screen. They will be taken to the payment page to select a payment method.

[![Pay Invoice Page](/docs/img/pay-invoice-page.png)](/docs/img/pay-invoice-page.png)

For example, this is what it would look like if your customer decided to pay with a credit or debit card.

[![Pay Invoice with Credit Card](/docs/img/pay-invoice-credit-card.png)](/docs/img/pay-invoice-credit-card.png)

Once your customer pays online then we will record the payment automatically in the dashboard and give them a receipt.

### What's next?

This tutorial has shown you what a simple invoicing workflow looks like with Invoiced. We recommend checking out our other guides to learn how to solve more complex billing workflows and set up automation for tedious billing tasks. There are guides for [subscription billing](/docs/guides/subscription-billing), [chasing](/docs/guides/chasing), [payments](/docs/payments), and more.