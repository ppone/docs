# Emails

Email is a core component to any online billing system. Here you can learn more about how sending works on Invoiced.

## Features

We have built many features around sending and email to make billing less stressful.

### Auditing

We log and track every message sent to customers from Invoiced. When it comes to billing, it's super important to be able to look up past communications with your customer. Within the dashboard you can see precisely what messages were sent to customers, when, and by whom. We track opens, clicks, and views (for invoices).

### View Tracking

Anyone that has billed customers before has probably heard the "I never received it" excuse, at least once. Sometimes it is true that the client never received the invoice. We built view tracking to to solve this problem.

All invoices have what is known as the **Client View**. The client view renders the full document in the recipient's web browser and supports several features, like online payments, PDF downloads, commenting, file attachments, and more. The client view is hosted on your [billing portal](billing-portal).

Sending invoices have a **View Invoice** button that links to the client view. As soon as your client clicks the view button we log it and notify you.

*Note: we have taken precautions to prevent false alerts should you open the client view of your own invoice.*

### Gmail Actions

We also have a partnership with Gmail that will give special treatment to the invoices you send to Gmail users. Your clients will see a **View Invoice** next to the subject line that takes them straight to the client view without ever needing to open the email. We've seen an uptick in views and paid invoices with this integration.

## Customizing Email Templates

Our default email templates were written to be professional and clearly communicate important billing information to your client, however, we understand these defaults do not work for everyone. It's easy to change the default email templates we use for emails.

The email templates use Mustache for templating awesomeness. Please consult the [Mustache documentation](https://mustache.github.io/mustache.5.html) to learn more. You can use [this tool](http://trymustache.com/) to validate your email templates. The funny-looking values like **{{customer_name}}** are placeholders that get replaced with the correct value, like the client's name, at send time.

In order to customize any of the email templates you need to go to **Settings** > **Emails** in the dashboard. Just click the **Customize** button next to the email template you want to edit the message and other settings. When finished you can click **Save**.

## Available Email Templates

### Invoices

**New Invoice** - Used when an outstanding invoice is sent to a customer for the first time, or when a manually collected invoice is generated from a subscription. Includes a **View Invoice** button.

**Invoice Reminder** - Used for outstanding invoices that have already been sent but are not past due yet. Includes a **View Invoice** button.

**Late Payment Reminder** - Used for past due invoices. Includes a **View Invoice** button.

**Thank You** - Used for invoices that have been paid in full. Includes a PDF attachment of the invoice.

### Payments

**Payment Receipt** Used for payment receipts. Includes a PDF attachment with the receipt.

**Failed AutoPay Attempt** - Sent when a payment attempt on an AutoPay invoice fails. Includes an **Update Payment Info** button.

### Subscriptions

**Onboarding Request** - Sent to request that a customer sign up for a subscription. When auto collections is enabled asks for a payment source also. Includes a **Sign Up** button.

**Sign Up Confirmation** - Sent to confirm a customer has been signed up to a subscription. Includes a **Manage Subscription** button. *Turned off by default.*

**Renews Soon** - Sent to notify a customer their subscription renews soon. You specify how many days in advance of a subscription renewal to send these notices. Includes a **Manage Subscription** button. *Turned off by default.*

**Cancellation** - Sent to confirm a customer's subscription has been canceled. *Turned off by default.*

### Customers

**Statement** - Used to send customer statements. Includes a PDF attachment of the statement.

## Invoice PDF attachments

The default behavior for Invoiced is to include a **View Invoice** button that links to the client view in the billing portal. Only the **Thank You** email will include a PDF attachment of the document. When your customer clicks the View Invoice they will be taken to an interactive document online that supports view tracking, file attachments, commenting, payments, and also has a download button for the document.

While we *strongly recommend* using the client view because of its many advantages, we understand there are situations where you may want to send a PDF instead, such as when you are sending invoices into automated systems. You can elect to send PDFs instead of a client view link. Here's how you do it:

1. Click **Customize** on the email template you want to have a PDF attachments in **Settings** > **Emails**.

2. Turn on the **Attach PDF instead of client view button** option.

3. (optional) If you want to send a view button *and* a PDF attachment then you need to also add a `{{{view_invoice_button}}}` line to the message body.