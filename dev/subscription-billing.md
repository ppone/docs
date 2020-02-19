# Subscription Billing

In this guide we are going to show you how to programmatically setup [subscription billing](/resources/guides/subscription-billing) through the Invoiced API.

## Quickstart Guide

In this example we are going to walk you through setting up a basic subscription billing scenario from scratch.

### Choose your language

<div class="language-selector">
	<a href="#" class="btn btn-link" data-lang="bash">Shell</a>
	<a href="#" class="btn btn-link" data-lang="ruby">Ruby</a>
	<a href="#" class="btn btn-link" data-lang="php">PHP</a>
    <a href="#" class="btn btn-link" data-lang="python">Python</a>
	<a href="#" class="btn btn-link" data-lang="java">Java</a>
</div>

### Create a customer

In order to bill our customer, we must first create an account for them on Invoiced. For this example we are going to use [AutoPay](/resources/docs/payments/autopay), which will charge your customer's payment source automatically when invoices are issued on the account, including each billing cycle when the subscription renews.

```bash
curl "https://api.invoiced.com/customers" \
  -u {API_KEY}: \
  -d name="Acme" \
  -d email="billing@acmecorp.com" \
  -d number="1234" \
  -d autopay=1
```

```ruby
require "invoiced"
invoiced = Invoiced::Client.new("{YOUR_API_KEY}")

customer = invoiced.Customer.create(
  :name => "Acme",
  :email => "billing@acmecorp.com",
  :number => "1234",
  :autopay => true
)
```

```php
$invoiced = new Invoiced\Client("{YOUR_API_KEY}");

$customer = $invoiced->Customer->create([
  'name' => "Acme",
  'email' => "billing@acmecorp.com",
  'number' => "1234",
  'autopay' => true
]);
```

```python
import invoiced
client = invoiced.Client("{YOUR_API_KEY}")

customer = client.Customer.create(
  name="Acme",
  email="billing@acmecorp.com",
  number="1234",
  autopay=True
)
```

```java
import com.invoiced.entity.Connection;
import com.invoiced.entity.Customer;

Connection invoiced = new Connection("{YOUR_API_KEY}", false);

Customer customer = invoiced.newCustomer();
customer.name = "Acme";
customer.email = "billing@acmecorp.com";
customer.autopay = true;
customer.create();
```

Since our customer does not have payment information yet, they will be sent the first invoice. When they pay that invoice their payment information will be automatically saved because AutoPay is turned on.

### Subscribe the customer to a plan

In this example we are going to bill for charges that happen during our customer's billing cycle, in addition to the base subscription price. The plan we are using was created through the dashboard in **Settings** &rarr; **Plans** with the ID `starter`. For example, the plan could be $30/month.

```bash
curl "https://api.invoiced.com/subscriptions" \
  -u {API_KEY}: \
  -d customer={CUSTOMER_ID} \
  -d plan="starter"
```

```ruby
invoiced.Subscription.create(
	:customer => customer.id,
	:plan => "starter"
)
```

```php
$invoiced->Subscription->create([
	'customer' => $customer->id,
	'plan' => "starter"
]);
```

```python
client.Subscription.create(
	customer=customer.id,
	plan="starter"
)
```

```java
import com.invoiced.entity.Subscription;

Subscription subscription = invoiced.newSubscription();
subscription.customer = customer.id;
subscription.plan = "starter";
subscription.create();
```

## Subscriptions with Addons

Subscription addons allow you to bill for multiple line items in the same billing cycle. Addons can represent a fixed recurring cost on top of the base price, such as extra user seats or more capacity than the base plan includes. Or addons can represent a usage-based component that is added to the base price, where the amount varies each month depending on usage (see [metered billing](/resources/docs/dev/metered-billing) for more information). Underneath the hood an addon is just another plan added to a subscription. In this example we are using a plan with the ID `ipad-license` that is $20/month.

```bash
curl "https://api.invoiced.com/subscriptions" \
  -u {API_KEY}: \
  -d customer={CUSTOMER_ID} \
  -d plan="starter" \
  -d addons[0][plan]="ipad-license" \
  -d addons[0][quantity]=11

```

```ruby
invoiced.Subscription.create(
	:customer => customer.id,
	:plan => "starter",
	:addons => [
		{
			:plan => "ipad-license",
			:quantity => 11
		}
	]
)
```

```php
$invoiced->Subscription->create([
	'customer' => $customer->id,
	'plan' => "starter",
	'addons' => [
		[
			'plan' => "ipad-license",
			'quantity' => 11
		]
	]
]);
```

```python
client.Subscription.create(
	customer=customer.id,
	plan="starter",
	addons=[
		{
			'plan': "ipad-license",
			'quantity': 11
		}
	]
)
```

```java
import com.invoiced.entity.Subscription;
import com.invoiced.entity.SubscriptionAddon;

Subscription subscription = invoiced.newSubscription();
subscription.customer = customer.id;
subscription.plan = "starter";
subscription.addons = new SubscriptionAddon[1];
subscription.addons[0] = new SubscriptionAddon();
subscription.addons[0].plan = "ipad-license";
subscription.addons[0].quantity = 11;
subscription.create();
```

Note: An addon must use a plan that matches the billing interval of the subscription's primary plan (i.e. you cannot mix monthly and yearly plans on the same subscription).

## Upgrades and Downgrades

Occassionally a subscriber will need to modify their subscription for various reasons, which can result in an increased price (upgrade) or a decreased price (downgrade). Subscription changes that affect the price include changing the billing interval (i.e. going from monthly to yearly billing), changing the base plan, adding or removing addons, and quantity adjustments of the subscription or addons. Invoiced handles subscription changes easily out of the box and will even perform proration calculations for you, up to the second.

### Changing a plan

The easiest subscription change is to change the plan and/or quantity.

```bash
curl "https://api.invoiced.com/subscriptions/:id" \
  -u {API_KEY}: \
  -d plan="pro" \
  -X PATCH
```

```ruby
subscription.plan = "pro"
subscription.save
```

```php
$subscription->plan = "pro";
$subscription->save();
```

```python
subscription.plan = "pro"
subscription.save()
```

```java
subscription.plan = "pro";
subscription.save();
```

Note: If you change the base plan to a new billing interval (i.e. monthly to yearly) then any addons must match the billing interval of the new plan.

### Adding an addon

Addons can be added or removed, just as easily as changing the base plan.

```bash
curl "https://api.invoiced.com/subscriptions/:id" \
  -u {API_KEY}: \
  -d addons[0][plan]="extra-users" \
  -d addons[0][quantity]=25 \
  -X PATCH
```

```ruby
subscription.addons = [
    {
        :plan => "extra-users",
        :quantity => 25
    }
]
subscription.save
```

```php
$subscription->addons = [
    [
        'plan' => "extra-users",
        'quantity' => 25
    ]
];
$subscription->save();
```

```python
subscription.addons = [
    {
        'plan': "extra-users",
        'quantity': 25
    }
]
subscription.save()
```

```java
import com.invoiced.entity.SubscriptionAddon;

subscription.addons = new SubscriptionAddon[1];
subscription.addons[0] = new SubscriptionAddon();
subscription.addons[0].plan = "extra-users";
subscription.addons[0].quantity = 25;
subscription.save();
```

### Prorations

When you make a change to a subscription that affects the price during the middle of the billing period, Invoiced will by default generate a proration for the time remaining in the billing period. The prorated amount will be added to the next bill, unless the billing interval is changing, in which case a new invoice will be generated immediately.

When modifying the subscription you can pass in `prorate` set to `false` in order to disable prorations. If you are allowing prorations and want to change the timestamp used to generate the proration you can use the `proration_date` parameter (defaults to current timestamp).

Note: Taxes and discounts are excluded from the proration calculations. 

## Cancellations

Not all billing arrangements last forever. When a customer is ready to cancel their subscription and stop billing this can be handled with a simple API call.

### Cancel immediately

When canceling a subscription the cancellation will take effect immediately. If you wish to return funds to your customer then you have to perform this calculation yourself.


```bash
curl "https://api.invoiced.com/subscriptions/:id" \
  -u {API_KEY}: \
  -X DELETE
```

```ruby
subscription.cancel
```

```php
$subscription->cancel();
```

```python
subscription.cancel()
```

```java
subscription.cancel();
```

Note: Cancellations do not produce a proration.

### Cancel at end of period

Instead of canceling immediately, you can cancel the subscription at the end of the current billing period, or at the end of the current contract term if the subscription has a contract. You might decide to use this because the customer has already paid for the month and they should continue to have access to your service for the full period.

The procedure for canceling at the end of the period is slightly different. You will modify the subscription to set the `cancel_at_period_end` property to `true`. When the subscription is billed next (or up for contract renewal) then the subscription will be canceled instead of being billed.

```bash
curl "https://api.invoiced.com/subscriptions/:id" \
  -u {API_KEY}: \
  -d cancel_at_period_end=1 \
  -X PATCH
```

```ruby
subscription.cancel_at_period_end = true
subscription.save
```

```php
$subscription->cancel_at_period_end = true;
$subscription->save();
```

```python
subscription.cancel_at_period_end = True
subscription.save()
```

```java
subscription.cancelAtPeriodEnd = true;
subscription.save();
```

## What's next?

We have gone through several subscription billing workflows. Of course, business is not always that simple. The [Subscription Billing](/resources/docs/api/#subscription-billing) section of the API reference details all of the subscription billing endpoints available to you.