# Subscription Billing Guide

Subscriptions allow businesses to automate billing customers on a recurring basis.

With subscription billing on Invoiced we can charge customers automatically each billing cycle or issue an invoice that can be paid with any of the payment methods you accept.

If you find yourself sending the same invoices every month then subscription billing is probably for you. Not only will subscription billing save you time, but your customer likely will appreciate the predictability and convenience of subscriptions.

## Introduction

We've designed our subscription billing system to offer power and flexibility, while remaining simple to understand and use. There are a few key concepts you might want to become familiar with before starting.

### Plans

A plan describes how much and how frequently you want to bill your customer. An example plan might be one for website hosting that is $100 per month. Plans are reusable templates for building subscriptions. You can setup and manage your plans in **Settings** > **Plans**.

### Subscriptions

A subscription bills a customer for a fixed amount on regular intervals, according to the plan the customer is subscribed to. Subscription pricing is flexible on Invoiced with quantities, addons, discounts, and taxes supported. We also support customizable billing intervals and fixed-duration subscriptions.

#### Trial Period

Subscriptions support a free trial period at the beginning of the subscription where the customer is not charged. For example, a subscription might have a 30-day trial period where the customer is given service for free until the first bill is issued.

#### Renewal Date

The renewal date is the date when the next bill for the subscription is going to be generated. Practically speaking, when a subscription renews that means the next invoice in the cycle is built and issued.

#### Billing Period

Each subscription keeps track of the current billing period. The billing period represents the timeframe that the subscription covers. The length of the billing period always matches the plan interval. By default the billing period will be the interval following the renewal date. If a monthly subscription renewed on December 1 then the current billing period would be December 1 - December 31.

#### Billing Period Offset

The billing period offset allows you to offset the billing period some number of days from the renewal date. Billing period offsets are great in enterprise billing scenarios where the customer is billed before the service period.

For example, consider a subscription with a billing period offset of 14 days and a renewal date of November 17. This would produce a billing cycle of December 1 - December 31. The result is that the customer will be billed on November 17 for the billing period of December 1 - December 31.

**NOTE: Changing the billing period offset will not change when the subscription renews. Instead change the renewal date for this.**

#### Duration

Subscriptions can be **infinite** or **fixed** duration. An infinite subscription (the default) runs forever until the customer cancels. A finite subscription will run for a fixed number of billing cycles.

#### Quantity

The subscription quantity acts as a multiplier to the base plan price. If your subscription were a per-user subscription (i.e. $30/user/month) then the quantity would represent the number of users the customer should be billed for each month.

### Subscription Addons

Subscription addons are meant to give you pricing flexibility on top of the base plan amount. Addons save you from creating a large number of plans for every possible combination of products/services that a customer could subscribe to. An addon is simply the application of a catalog item to a subscription. You can setup and manage catalog items in **Settings** > **Catalog**.

### Subscription Invoices

A subscription will generate an invoice each billing cycle for the amount owed in that billing cycle. The invoice contains line items for the plan and any addons.

#### AutoPay

Since subscriptions just generate invoices that means [AutoPay](autopay) customers are fully supported with subscription billing. AutoPay will automatically charge your customer's payment source for any invoices issued against their account, including subscription invoices.

If a customer with AutoPay enabled is subscribed to a plan, but has not connected a payment source yet, then we will send them the first invoice automatically. Upon paying the invoice we will capture the customer's payment information for use on future invoices.

#### Payment Terms

When AutoPay is not enabled then the customer will receive an invoice each billing period that they can pay using any of the payment methods you accept.

Payment terms succinctly tell the customer when an invoice is due. For example, NET 7 means that payment is due within 7 days of the invoice whereas NET 30 means payment is due in 30 days. You can read more about the different kinds of payment terms in this [blog post](https://invoiced.com/blog/how-to-get-paid-faster-on-your-invoice-part-i).

#### Pending Line Items

If there are any unbilled one-time charges (setup fees or usage charges) that were added to the customer's account during the billing cycle then those line items will be swept into subscription invoice at the time it is generated.

### Prorations

Invoiced supports prorations on subscriptions when changing a plan, quantity, or addons mid- billing cycle. When a customer downgrades they will receive a credit, and when they upgrade will be charged.

Prorations are calculated any time a subscription is changed, unless disabled. A proration will generate a credit for the time remaining on the current billing cycle before the subscription update and a charge for the time remaining with the subscription update. If the proration is negative (downgrade) then we will issue the customer a credit. If positive (upgrade) then will add the amount to the next subscription invoice.

When switching to a plan with a different billing cycle, for example switching from monthly to annual billing, then a new billing cycle will be started at the time of proration. This means an invoice will be generated for the next billing cycle on the plan.

Prorations are calculated based on the number of seconds left in the billing cycle.

### Sign Up Pages

Sign up pages allow customers to purchase a subscription online through a self-serve form hosted by Invoiced. The [Sign Up Pages Guide](sign-up-pages) has more information on this.

## Usage

### Creating a Subscription

In this guide we are going to walk you through creating a subscription to invoice a customer each month with NET 14 terms.

If you are using AutoPay then we recommend using sign up pages to subscribe new customers and securely capture payment information.

1. First sign in to the Invoiced dashboard and go to the **Subscriptions** page. Then click **Add Subscription**.

   [![Empty Subscriptions Page](../img/subscriptions-page.png)](../img/subscriptions-page.png)

2. A new subscription dialog will appear. Let's start by selecting our customer. If the customer does not exist yet then you would click **Add Ben Bitdiddle as a new customer**.

   [![New Subscription Step 1](../img/new-subscription-step1.png)](../img/new-subscription-step1.png)

3. This will open a new customer dialog. You can fill in any contact information for the customer now. We are also going to enter **NET 14** for the payment terms.

   [![New Customer](../img/subscription-new-customer.png)](../img/subscription-new-customer.png)

4. Now you can go ahead and click **Create** to finish creating your customer.

   [![New Subscription with Customer](../img/new-subscription-with-customer.png)](../img/new-subscription-with-customer.png)

5. Next we need to select a plan. If you don't have a recurring plan yet then let's create one. Click on **+ New Plan**.

   [![New Recurring Plan](../img/new-plan.png)](../img/new-plan.png)

   Let's say we want to create a plan called **Basic** for **$39/month**. The **ID** field is a unique identifier used to reference your plan through the API. The ID is automatically generated for you, but you are free to rename this to match your own internal SKU or naming scheme.

6. Once finished you can click **Save** to create the plan.

   [![New Subscription with Customer and Plan](../img/new-subscription-with-plan.png)](../img/new-subscription-with-plan.png)

7. All that is left is to customize how long the subscription should run and select any addons. Click the **Options** button to reveal these options.

   [![New Subscription Options](../img/new-subscription-options.png)](../img/new-subscription-options.png)

   We want to start the subscription now. If you want to start the subscription at a later date or offer a free trial period then you can uncheck the **Starting now** option to select a start date.

   We are going to leave the **Duration** as *Until canceled*. The subscription will renew until canceled by you or the customer.

   The **Quantity** can be left as **1**, unless the customer is purchasing multiple quantities of the base price.

   Let's try adding an addon by clicking **+ Addon**. In our example we are selecting an **iPad License** addon and setting the quantity to **4**.

   We can leave the **Billing Period Offset** at **0** unless we wanted to shift the billing period.

8. At the bottom of the screen you can see the calculated recurring total. If you click the **Preview** button you can even see a preview of the upcoming billing cycles.

   [![New Subscription Preview](../img/new-subscription-preview.png)](../img/new-subscription-preview.png)

   Once the subscription looks right you can now click **Create**.

   You will now see that your newly created subscription is active. The invoice for the first billing cycle has already been generated.

   [![Newly created subscription and generated invoice](../img/subscription-summary.png)](../img/subscription-summary.png)

### Editing a Subscription

What happens when your customer falls in love with your service and wants to purchase more? This common scenario is easily handled with Invoiced. We will even (optionally) calculate and bill the prorated amount when switching a plan, quantity, or addons in the middle of the billing cycle.

You can edit a subscription by opening the subscription in the dashboard and clicking the **Edit** button in the top right corner.

[![Edit Subscription with Prorations](../img/edit-subscription.png)](../img/edit-subscription.png)

### Changing the Renewal Date

Once your subscription is running you might want to change when it renews next. The reason might be that the customer wants the subscription to renew on a certain day of the month, maybe the wrong start date was chosen, or else you want to issue invoices sooner.

With the subscription in the dashboard you can click **More** > **Change Renewal Date** to change when the subscription will renew next.

[![Change Subscription Renewal Date Step 1](../img/change-renewal-date-step1.png)](../img/change-renewal-date-step1.png)

The renewal date cannot be set in the past. Changing the renewal date will not produce any prorations.

[![Change Subscription Renewal Date Step 2](../img/change-renewal-date-step2.png)](../img/change-renewal-date-step2.png)

You can also change the billing period offset as well by clicking **More** > **Change Billing Period Offset**. This will adjust the current billing period right away, however, it will not change when the next bill is generated or produce any prorations.

### Canceling a Subscription

Canceling a subscription is simple. With the subscription open in the dashboard you can click **More** > **Cancel Subscription**.

[![Canceling a Subscription Step 1](../img/cancel-subscription-step1.png)](../img/cancel-subscription-step1.png)

You can choose whether you want the subscription to be canceled immediately or at the end of the billing period.

[![Canceling a Subscription Step 2](../img/cancel-subscription-step2.png)](../img/cancel-subscription-step2.png)

## FAQs

### What automated emails does Invoiced send for subscriptions? 

Invoiced can send these emails with subscriptions:

- **Sign up confirmation**
  
  Confirmation that a customer has finished signing up for automatic billing.

- **Renews Soon**

  A reminder sent X days before a subscription renews to let customers know about upcoming charges.

- **New invoice**
  
  Sends any invoices generated from a subscription to your customer.

- **Cancellation**

  Notification when a subscription is canceled.

You can learn more about these emails in the [Emails Guide](emails#subscriptions).

### When do subscription invoices go out?

Subscriptions are usually renewed very close to the renewal timestamp (within a minute). Subscriptions will never renew early but please keep in mind that they might be renewed late. If a subscription does happen to be renewed later than scheduled then our system will not punish the customer for non-payment, as should yours.