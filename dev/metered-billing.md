# Metered Billing

Metered billing allows you to bill customers for charges incurred during a billing cycle. These charges could be from usage, one-off purchases, prorations, or some other amount not accounted for by the customer's subscription.

## Introduction

Conceptually metered billing on Invoiced is simple. It's just line items! Metered billing should feel natural if you are already familiar with our invoicing API.

### Pending Line Items

Whenever a customer incurs a charge with your business that you want to bill for later then you create a **pending line item**. A pending line item behaves just like invoice line items, with the distinction that it has not been billed yet. The line item is attached to a customer but not an invoice.

### Invoicing pending line items

Pending line items get billed to the customer by issuing an invoice. When a pending line item is billed then it will be moved from the customer's account to an invoice. There are two ways that pending line items can be invoiced:

1. Automatically at the end of a customer's billing period. Any pending line items will be swept up into the next subscription invoice.

2. Manually triggering an invoice from pending line items. Use this method if you do not want to wait for the end of the billing cycle or your customer does not have a subscription.

## Implementing metered billing

We are going to walk you through a basic metered billing workflow using the Invoiced API.

### Choose your language

<div class="language-selector">
	<a href="#" class="btn btn-link" data-lang="bash">Shell</a>
	<a href="#" class="btn btn-link" data-lang="ruby">Ruby</a>
	<a href="#" class="btn btn-link" data-lang="php">PHP</a>
    <a href="#" class="btn btn-link" data-lang="python">Python</a>
	<a href="#" class="btn btn-link" data-lang="java">Java</a>
</div>

### Create a customer

In order to bill our customer, we must first create an account for them on Invoiced. For this example we are going to invoice our customer with **NET 7** payment terms each billing cycle. You could just as easily use [AutoPay](/resources/docs/payments/autopay), which will charge your customer's payment source automatically when invoices are issued on the account.

```bash
curl "https://api.invoiced.com/customers" \
  -u {API_KEY}: \
  -d name="Acme" \
  -d email="billing@acmecorp.com" \
  -d number="1234" \
  -d payment_terms="NET 7"
```

```ruby
require "invoiced"
invoiced = Invoiced::Client.new("{YOUR_API_KEY}")

customer = invoiced.Customer.create(
  :name => "Acme",
  :email => "billing@acmecorp.com",
  :number => "1234",
  :payment_terms => "NET 7"
)
```

```php
$invoiced = new Invoiced\Client("{YOUR_API_KEY}");

$customer = $invoiced->Customer->create([
  'name' => "Acme",
  'email' => "billing@acmecorp.com",
  'number' => "1234",
  'payment_terms' => "NET 7"
]);
```

```python
import invoiced
client = invoiced.Client("{YOUR_API_KEY}")

customer = client.Customer.create(
  name="Acme",
  email="billing@acmecorp.com",
  number="1234",
  payment_terms="NET 7"
)
```

```java
import com.invoiced.entity.Connection;
import com.invoiced.entity.Customer;

Connection invoiced = new Connection("{YOUR_API_KEY}", false);

Customer customer = invoiced.newCustomer();
customer.name = "Acme";
customer.email = "billing@acmecorp.com";
customer.paymentTerms = "NET 7";
customer.create();
```

### Subscribe the customer to a plan

In this example we are going to bill for charges that happen during our customer's billing cycle, in addition to the base subscription price. The plan we are using was created through the dashboard in **Settings** &rarr; **Plans** with the ID `starter`.

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

### Add metered charges

Let's pretend during the billing cycle our customer used engineering hours that we want to bill for. Instead of issuing a separate invoice we can just add it to their next subscription invoice.

We are going to use an item that was set up in **Settings** &rarr; **Items** with the ID `engineer_hours`. The item already has the price set, however, you can also bill for one-off line items, just like with invoices. The [Line Item Object](/resources/docs/api/#line-item-object) shows all of the attributes that we support for creating line items.

```bash
curl "https://api.invoiced.com/customers/{CUSTOMER_ID}/line_items" \
  -u {API_KEY}: \
  -d catalog_item="engineer_hours" \
  -d quantity=5
```

```ruby
customer.line_items.create(
	:catalog_item => "engineer_hours",
	:quantity => 5
)
```

```php
$customer->lineItems()->create([
	'catalog_item' => "engineer_hours",
	'quantity' => 5
]);
```

```python
customer.line_items().create(
	catalog_item="engineer_hours",
	quantity=5
)
```

```java
import com.invoiced.entity.PendingLineItem;

PendingLineItem pendingCharge = customer.newPendingLineItem();
pendingCharge.catalogItem = "delivery";
pendingCharge.quantity = 5;
pendingCharge.create();
```

And that's it! You can add further pending line items to the customer, or even edit an existing pending line item. Next time the subscription renews, your pending line items will be added to the invoice.

### Trigger invoice for metered charges (optional)

If your customer is not on a subscription, or you want to bill them *now* for pending line items, then you can manually trigger an invoice for metered charges.

```bash
curl "https://api.invoiced.com/customers/{CUSTOMER_ID}/invoices" \
  -u {API_KEY}: \
  -X POST
```

```ruby
customer.invoice
```

```php
$customer->invoice();
```

```python
customer.invoice()
```

```java
import com.invoiced.entity.Invoice;

Invoice invoice = customer.invoice();
```

A new invoice using your customer's pending line items will be generated on the spot. If the customer does not have any pending line items then an error will be returned.

## What's next?

We have gone through a basic metered billing workflow. Of course, business is not always that simple. The [Metered Billing](/resources/docs/api/#metered-billing) section of the API reference details all of the metered billing endpoints available to you.