# Guides

<!-- Start creating guide and go over each and every feature
-->
* [Invoicing Guide](#invoice-guide)
   * [Sending Automatic Reminders to your client](#invoice-automatic-reminders)
      * [Turning on Invoice Chasing](#invoice-automatic-reminders)
      * [Enabling Chase](#invoice-automatic-reminders)
        * [Setting a schedule](#invoice-automatic-reminders)
   * [Getting Paid Automatically Through Subscriptions](#invoice-paid-automatically)
      * [Subscriptions](#invoice-subscriptions) 
      * [Plans](#invoice-plans)
      * [Collections Mode](#invoice-collections-mode)
   * [Enabling Online Payments On Your Invoices](#invoice-enable-online)
      * [Accepting Credit Cards](#invoice-subscriptions) 


   

###<a name="invoice-guide"></a> Invoicing Guide


####<a name="invoice-automatic-reminders"></a>Sending Automatic Reminders For Sent Invoices

Invoiced lets you send automatic reminders to your client.  This can help you close the gap on the time you get paid, by reminding them that payment is due.

We call this feature **Chasing**.  
Invoice Chasing is typically enabled per invoice.  So you will have to explictly turn it on per invoice.  You will also have to enable it in the settings and set a reminding schedule first.

#####<a name="invoice-automatic-reminders-chasing"></a>Getting Started With Invoice Chasing

First you will need to enable chasing in the settings and set a schedule.

Go to Setttings->Chasing

![Invoice Settings Chasing](imgs/invoice-setting-chasing.png)

Click on Enable Chasing to enable it.

![Invoice Settings Chasing Enable](imgs/invoice-setting-chasing-enable.png)

Now we are ready to set the chasing schedule

#####<a name="invoice-automatic-reminders-setting-chasing-schedule"></a>Setting the chasing schedule

It is pretty important to set the chase schedule correctly.  The chase schedule determines when and how often your client receives the reminders.

Now to set the chasing schedule, let us add a step.

![Invoice Settings Chasing Enable](imgs/invoice-setting-chasing-add-step.png)

The chase schedule has 3 schedule templates you can choose from.

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

CASE A:

We set our schedule to

`Send a reminder 5 days before the due date.`

And we also add in

`Send a reminder 5 days repeating`

What will happen is the first reminder will go 

CASE B:

We set our schedule just to 

`Send a reminder 5 days repeating`

What will happen is the reminder will start on the due date and keep repeating until the invoice.

Since our due date is September 10th, our reminder will be sent on September 15th, and it will keep repeating every 5 days until the invoice is paid.

**Once the invoice is paid the reminders will automatically stop not matter what schedule or combination of schedule templates that we sue**

**Best Practices**
Although we allow you add as many schedule templates as you like, we generally recommend to keep the schedule simple (no more than 2 schedule templates).   Adding a combination of many schedule templates can make it hard for you to predict precisely every time your client gets a reminder. 


####<a name="invoice-automatic-reminders"></a>Sending Automatic Reminders For Sent Invoices



####<a name="invoice-automatic-reminders"></a>Getting paid automatically through subscriptions
Invoiced offers business a way to automatically collect money through a feature called subscriptions.


####<a name="invoice-automatic-reminders"></a>Subscriptions

Subscriptions allow businesses to either automatically collect payment or automatically invoice the customer on a recurring basis.

This is great if find yourself frequently invoicing your customer every month.  Using subscriptions allows you to automatically invoice & collect money from them, saving you and your customer valuable time and offering convience.







