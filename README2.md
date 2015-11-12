# Guides

<!-- Start creating guide and go over each and every feature
-->
* [Invoicing Guide](#invoice-guide)
   * [Getting Paid Automatically Through Subscriptions](#invoice-paid-automatically)
      * [Subscriptions](#invoice-subscriptions) 
      * [Plans](#invoice-plans)
      * [Collections Mode](#invoice-collections-mode)
   * [Sending Automatic Reminders to your client](#invoice-automatic-reminders)
      * [Enabling Chasing](#invoice-chasing-enable)
      * [Setting the Chasing Schedule](#invoice-chasing-schedule)
      * [Editing The Chasing Email](#invoice-chasing-edit-email)

   * [Enabling Online Payments On Your Invoices](#invoice-enable-online)
      * [Accepting Credit Cards](#invoice-subscriptions) 


###<a name="invoice-guide"></a> Invoicing Guide


####<a name="invoice-automatic-reminders"></a>Getting paid automatically through subscriptions
Invoiced offers business a way to automatically collect money through a feature called subscriptions.


####<a name="invoice-automatic-reminders"></a>Subscriptions

Subscriptions allow businesses to either automatically collect payment or automatically invoice the customer on a recurring basis.

This is great if find yourself frequently invoicing your customer every month.  Using subscriptions allows you to automatically invoice & collect money from them, saving you and your customer valuable time and offering convience.


####<a name="invoice-create-subscription"></a>Creating a Subscription

To create subscription, click on Subscriptions from the dashboard.  

![Invoice Subscribe](imgs/invoice-subscribe.png)

From their click on `Add Subscription`

![Invoice Subscription Add](imgs/invoice-subscribe-add.png)

Now a the subscription modal will appear.  Enter all the required fields.

![Invoice Subscription Modal](imgs/invoice-subscribe-modal.png)


####<a name="invoice-create-plan"></a>What is a plan

Plans are sort a template for creating a subscription.  You will find that the plan actually specifiy how often the client is invoiced or charged, how much they are invoiced for, the currency, descripton, terms, notes, allowed payments and whether the payment should be chased.

The advantages of using a plan are that it can save you time from having to re-enter the information mentioned above.  


####<a name="invoice-automatic-reminders"></a>Sending Automatic Reminders For Sent Invoices

Invoiced lets you send automatic reminders to your client.  This can help you close the gap on the time you get paid, by reminding them that payment is due.

We call this feature **Chasing**.  
Invoice Chasing is typically enabled per invoice.  So you will have to explictly turn it on per invoice.  You will also have to enable it in the settings and set a reminding schedule first.

#####<a name="invoice-chasing-enable"></a>Enabling Chasing

First you will need to enable chasing in the settings and set a schedule.

Go to Setttings->Chasing

![Invoice Settings Chasing](imgs/invoice-setting-chasing.png)

Click on Allow Chasing to enable it.

![Invoice Settings Chasing Enable](imgs/invoice-setting-chasing-enable.png)

Now we are ready to set the chasing schedule

#####<a name="invoice-chasing-schedule"></a>Setting the Chasing Schedule

It is pretty important to set the chase schedule correctly.  The chase schedule determines when and how often your client receives the reminders.

Now to set the chasing schedule, let us add a step.

![Invoice Settings Chasing Enable](imgs/invoice-setting-chasing-add-step.png)

The chase schedule has 3 schedule steps you can choose from.

1. `Send a reminder X days after the due date`

![Invoice Settings Chasing Step 1](imgs/invoice-setting-chasing-step-1.png)

2. `Send a reminder X days before the due date`

![Invoice Settings Chasing Step 2](imgs/invoice-setting-chasing-step-2.png)

3. `Send a reminder X days repeating`

![Invoice Settings Chasing Step 3](imgs/invoice-setting-chasing-step-3.png)

Schedule 1 means your client will get a 1 time reminder x days after the due date.

Example:
We set our schedule to

`Send a reminder 5 days after the due date` 

If our Invoice is due on September 10th.  Than our client will get a reminder 5 days after on September 15th.

Schedule 2 means your client will get a 1 time reminder x days before the due date.

Example:
We set our schedule to

`Send a reminder 5 days before the due date`

If our Invoice is due on September 10th.  Than our client will get a reminder 5 days before on September 5th.

Schedule 3 means your client will get a continual reminder either x days after the due date if schedule 1 or 2 has not been sett.  If schedule 1 or 2 have been set, schedule 3 will repeat x days from the date that the client receives the reminder from schedule 1 or 2.

Example:

`Let the invoice due date be September 10th`

**CASE A:**

We set our schedule to

`Send a reminder 5 days before the due date.`

And we also add in

`Send a reminder 5 days repeating`

What will happen is the first reminder will go September 5th, the next one will go on September 10th, 15th, etc, until the invoice is paid.

**CASE B:**

We set our schedule just to 

`Send a reminder 5 days repeating`

What will happen is the reminder will start on the due date and keep repeating until the invoice.

Since our due date is September 10th, our reminder will be sent on September 15th, and it will keep repeating every 5 days until the invoice is paid.

**Once the invoice is paid the reminders will automatically stop not matter what schedule or combination of schedule templates that we sue**

**Best Practices**
Although we allow you add as many schedule templates as you like, we generally recommend to keep the schedule simple (no more than 2 schedule templates).   Adding a combination of many schedule templates can make it hard for you to predict precisely every time your client gets a reminder. 

---
#####<a name="invoice-chasing-edit-email"></a>Editing The Chasing Emails
Invoiced sends out a default chasing email depending on the context.  

There are 3 email templates that are sent depending on context `New Invoice Email`, `Invoice Reminder Email`, `Payment Reminder Email` .

That means that if you have not sent the invoice to the client, it will send out the `New Invoice Email`, which is the standard email sent out.

If you already have sent the invoice to client and the invoice is not over due, it will send out `Invoice Reminder Email`, whose purpose is to remind the client that the invoice will be due soon.

If the invoice has been sent and is over due than the `Payment Reminder Email` is sent, it's purpose is to gently remind clients that they are late and payment is due as soon as possible.

To edit these emails you can go to Settings->Emails.

![Invoice Settings Email](imgs/invoice-setting-emails.png)

To edit or customize these email templates click on the customize button.

![Invoice Settings Email Customize](imgs/invoice-setting-emails-customize.png)


<!-- Maybe add more on customizing emails -->









