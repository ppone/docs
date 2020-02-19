# Chasing Guide

<p class="alert alert-warning">This document is for our legacy chasing system. If you are using the legacy system and want to move to the new chasing system then please contact support@invoiced.com.</p>

Invoiced lets you send automatic reminders to your client for outstanding invoices according to the schedule you specify. We call this feature **chasing**.

Chasing can help you close the gap on getting paid by reminding customers to pay. In order to start chasing invoices you must set up a schedule and then turn enable chasing for the invoices you want to chase.

## Chase Schedules

You must specify the schedule that you want your invoices to be chased with. We will stop chasing an invoice once the schedule is finished or when the invoice is paid or closed.

Chase schedules are defined as a series of steps each specifying when an invoice reminder should be sent. Your chasing schedule can be built from the following types of steps:

1. **When issued** - sends an invoice on the issue date
2. **Before the due date** - sends a reminder N days *before* the due date
3. **On the due date** - sends a reminder on the due date
3. **After the due date** - sends a reminder N days *after* the due date
4. **Repeater** - sends a reminder *every N days after* the due date until the invoice is paid or closed.

We will then only chase invoices that have chasing enabled on the invoice. Once the schedule has been completed or the invoice is paid or closed then chasing will stop.

## Getting Started

First you will need to enable chasing for your account in the settings and set up a schedule.

Go to **Settings** &rarr; **Chasing**. Flip the **Allow Chasing** toggle.

[![Invoice Settings Chasing Enable](/docs/img/allow-chasing-new.png)](/docs/img/allow-chasing-new.png)

Now we are ready to set the chasing schedule in order to instruct Invoiced exactly when to send reminders. Click on **+ Step** to add your first and subsequent steps to the chasing schedule.

[![Invoice Settings Chasing Enable](/docs/img/add-chasing-schedule.png)](/docs/img/add-chasing-schedule.png)

You can remove existing steps or add new ones easily. We will automatically sort the schedule for you.

[![Adding Chasing Steps](/docs/img/chasing-schedue-editor.png)](/docs/img/chasing-schedue-editor.png)

When finished click **Save**. Chasing is now enabled for your account. All that's left is to enable chasing on the invoices you want chased.

[![Completed Chasing Schedule](/docs/img/finished-chasing-schedule.png)](/docs/img/finished-chasing-schedule.png)

### Additional Chasing Support

When creating a chasing schedule, you can also select a method to initiate a response based on chasing objective. These methods include: 

**Send a Reminder** - Sends a reminder to the customer based on chasing objective

**Flag the Invoice** - Flags invoice in Invoiced to be filtered in reporting as well as flagged on invoice for the customer. 

Invoices flagged will be considered an invoice that "Needs Attention". Invoices that need attention will be marked on the invoices outstanding page with an attention icon. 

[![Invoice Settings Chasing Enable](/docs/img/needs-attention.png)](/docs/img/needs-attention.png)

You can also filter your invoices by invoices that need attention with the needs attention filter.

[![Invoice Attention Filter](/docs/img/attention-filter.png)](/docs/img/attention-filter.png)

When accessing the invoice, the action item will be placed on the invoice and can be marked as "resolved" to remove the action item.

[![Resolve Attention](/docs/img/mark-as-resolved.png)](/docs/img/mark-as-resolved.png)


### Chasing Invoices

When drafting an invoice you can turn on chasing by clicking **Options** at the top of the screen and enabling the **Chasing** setting.

If the invoice has already been created then you can simply click **Enable** under the *Invoice Details* section (next to where it says **Chase: No**). Your invoice will now be chased according to the schedule you set up. The next chase date will be shown in the *Invoice Details* section.

### Further Customization

#### Enable Chasing by Default

If you want chasing enabled by default when drafting new invoices then you enable the **Chasing** setting in **Settings** &rarr; **General** &rarr; **Defaults**.

#### Customizing the Chasing Email Templates

The email template used for chasing reminders depends on the invoice's status.

1. **New Invoice Email**
   This email template is used when the invoice has not been sent yet.

2. **Invoice Reminder Email**
   This email template is used when the invoice has already been sent but is not due yet.

3. **Late Payment Reminder Email**
   This email template is always used when the invoice is past due.

You can learn more about customizing email templates in the [Emails Guide](emails#customizing-email-templates).

## Manually Scheduling Invoices

In addition to the global chasing schedule, you can also schedule arbitrary follow ups on a specific invoice. You might use this if you want to follow up on a specific invoice far into the future. Simply schedule the follow up and Invoiced will do it for you when it's time!

Scheduling invoices to be sent into the future only requires that chasing is enabled globally. It does not require you to set up a chasing schedule. Follow these steps in order to schedule a follow up for an invoice:

1. Ensure that **Allow Chasing** is enabled in **Settings** &rarr; **Chasing**. You only need to enable this once for your account.

   [![Chasing is enabled globally](/docs/img/turn-chasing-on.png)](/docs/img/turn-chasing-on.png)

2. Open the invoice that you want Invoiced to follow up on.

   [![Invoice you want to schedule](/docs/img/scheduling-invoices-2.png)](/docs/img/scheduling-invoices-2.png)

3. Click **Actions** &rarr; **Enable Chasing**.

   [![Enable invoice chasing](/docs/img/scheduling-invoices-3.png)](/docs/img/scheduling-invoices-3.png)

4. In the *Invoice Details* section you should see that chasing is enabled. If you have a chasing schedule then *Next Follow Up* might be set to a date already. If not, then it will say *Not scheduled*.

   [![No follow ups scheduled](/docs/img/scheduling-invoices-4.png)](/docs/img/scheduling-invoices-4.png)

5. Click on **Schedule** below *Next Follow Up* (or **Modify** if there is already a scheduled follow up).

   [![Scheduling an automatic follow up](/docs/img/scheduling-invoices-5.png)](/docs/img/scheduling-invoices-5.png)

6. Enter in the date you want Invoiced to follow up on the invoice and click **Save**. Your follow up is scheduled. Invoiced will follow up on the date you've selected and no further action is needed.

   [![Invoice follow up is now scheduled](/docs/img/scheduling-invoices-6.png)](/docs/img/scheduling-invoices-6.png)

## Examples

Here are a few examples how Invoiced will behave given a chasing schedule.

### Schedule with one-time reminders

Given the following schedule:

1. Send a reminder **7** days **before** the due date
2. Send a reminder **5** days **after** the due date

Let's say our invoice is due on *September 10th*. Or client will receive a reminder the week before it is due, on *September 3rd*. If it still is not paid then on *September 15th* they will receive a late payment reminder.

### Schedule with repeating reminders

Given the following schedule:

1. Send a reminder **7** days **before** the due date
1. Send a reminder **0** days **after** the due date
2. Send a reminder **5** days **repeating**

Like the previous example our invoice is due on *September 10th*. As with the previous example they will receive a reminder the week before. They will receive another reminder on the due date, *September 10th*, if the invoice is still not paid. By *September 15th* if they still have not paid then they will receive a late payment reminder, and again every 5 days until the invoice is paid or closed.

### Automatically send all newly issued invoices

Given the following schedule:

1. **When issued**

Any invoice that is issued in the system will be sent automatically (approximately 1-2 hours after the issue date). If an invoice is issued with a date of *September 10th* then it will be sent on that day.