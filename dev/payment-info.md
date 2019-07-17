# Collecting Payment Information

In this document we are going to show you how to collect, store, and use payment information on Invoiced through your own website or application.

## Introduction

When implementing Invoiced into your app or website you often want control over the billing and payment UIs in order to provide customers with a seamless experience. Invoiced allows you to collect and vault payment information using your own forms while still relying on Invoiced to manage payments. As a result of letting Invoiced handle payment information you can also enjoy simplified PCI compliance.

The way that it works is that within your customer's web browser you can tokenize your customer's payment information that can later be passed to our API in order to save the payment information for future billing or payments.

The key to a secure implementation is to use either the Invoiced tokenization scheme or your payment gateway's tokenization scheme (if there is one). Tokenization gives you a randomly generated token ID that you can pass to your servers that references the payment information collected. The benefit of this approach is to prevent you from directly handling sensitive payment information.

With tokenization the payment information is sent to Invoiced on the client-side using our Javascript library. When the payment information is sent in you receive a short-lived, single-use token that references the captured payment information, which can be a card or bank account. You can then use that payment info token in our API to vault it on a customer's account or use it to process a payment.

It's important to consider that payment info tokens will only work with your Invoiced account and last for a maximum of 2 hours. Once a token is used it cannot be re-used. As such you should not be storing tokens on your end.

### Choose your language

<div class="language-selector">
    <a href="#" class="btn btn-link" data-lang="bash">Shell</a>
    <a href="#" class="btn btn-link" data-lang="ruby">Ruby</a>
    <a href="#" class="btn btn-link" data-lang="php">PHP</a>
    <a href="#" class="btn btn-link" data-lang="python">Python</a>
    <a href="#" class="btn btn-link" data-lang="java">Java</a>
</div>

### Prerequisites

1. You have built your own form to capture payment information.
2. Include the `invoiced.js` library on your payment page:
   ```
   <script src="https://js.invoiced.com/v1/"></script>
   ````
3. Obtain your publishable key from **Settings** &rarr; **Developers**.

## Storing credit card information

### 1. Tokenize credit card

```
<script type="text/javascript">
    Invoiced.setPublishableKey("{YOUR_PUBLISHABLE_KEY}");

    // This information should be collected by your form...
    var number = '4242424242424242';
    var cvc = '123';
    var expMonth = '12';
    var expYear = '2021';
    var name = 'Jim Halpert';
    var address = {
        address1: '1234 Main St',
        address2: null,
        city: 'Scranton',
        state: 'PA',
        postal_code: '12345',
        country: 'US'
    };
    Invoiced.card.tokenize(number, cvc, expMonth, expYear, name, address, handleInvoicedToken);

    function handleInvoicedToken(statusCode, response) {
        if (statusCode >= 400) {
            console.error(response.message);
            return;
        }

        console.log('Success! Send this token to the backend for the next step: ', response.id);
    }
</script>
```

### 2. Add card to the customer

If this is a new customer then you can pass in the Invoiced token like below:

```bash
curl "https://api.invoiced.com/customers" \
  -u {API_KEY}: \
  -d name="Acme" \
  -d payment_source[method]=credit_card \
  -d payment_source[invoiced_token]={CAPTURED_TOKEN}
```

```ruby
require "invoiced"
invoiced = Invoiced::Client.new("{YOUR_API_KEY}")

customer = invoiced.Customer.create(
  :name => "Acme",
  :payment_source => {
    :method => "credit_card",
    :invoiced_token => token
  }
)
```

```php
$invoiced = new Invoiced\Client("{YOUR_API_KEY}");

$customer = $invoiced->Customer->create([
  'name' => "Acme",
  'payment_source' => [
    'method' => "credit_card",
    'invoiced_token' => $token
  ]
]);
```

```python
import invoiced
client = invoiced.Client("{YOUR_API_KEY}")

customer = client.Customer.create(
  name="Acme",
  payment_source={
    'method': "credit_card",
    'invoiced_token': token
  }
)
```

```java
import com.invoiced.entity.Connection;
import com.invoiced.entity.Customer;

Connection invoiced = new Connection("{YOUR_API_KEY}", false);

Customer customer = invoiced.newCustomer();
customer.name = "Acme";
customer.payment_source = token;
customer.create();
```

Or if this is an existing customer then you can make a similar call to update the customer (assuming you have already [retrieved the customer](https://invoiced.com/docs/api/#retrieve-a-customer)):

```bash
curl "https://api.invoiced.com/customers/CUSTOMER_ID" \
  -u {API_KEY}: \
  -d payment_source[method]=credit_card \
  -d payment_source[invoiced_token]={CAPTURED_TOKEN}
```

```ruby
customer.payment_source = {
  :method => "credit_card",
  :invoiced_token => token
}
customer.save
```

```php
$customer->payment_source = [
  'method' => "credit_card",
  'invoiced_token' => $token
];
$customer->save();
```

```python
customer.payment_source = {
  'method': "credit_card",
  'invoiced_token': token
}
customer.save()
```

```java
customer.payment_source = token;
customer.save();
```

## Storing bank account information

You can also capture bank account information for ACH debits.

### 1. Tokenize bank account

```
<script type="text/javascript">
    Invoiced.setPublishableKey("{YOUR_PUBLISHABLE_KEY}");

    // This information should be collected by your form...
    var name = 'Jim Halpert';
    var accountType = 'individual'; // `individual` or `company`
    var accountNumber = '123456789';
    var routingNumber = '110000000';

    Invoiced.bankAccount.tokenize(name, accountType, accountNumber, routingNumber, handleInvoicedToken);

    function handleInvoicedToken(statusCode, response) {
        if (statusCode >= 400) {
            console.error(response.message);
            return;
        }

        console.log('Success! Send this token to the backend for the next step: ', response.id);
    }
</script>
```

### 2. Add bank account to the customer

If this is a new customer then you can pass in the Invoiced token like below:

```bash
curl "https://api.invoiced.com/customers" \
  -u {API_KEY}: \
  -d name="Acme" \
  -d payment_source[method]=ach \
  -d payment_source[invoiced_token]={CAPTURED_TOKEN}
```

```ruby
require "invoiced"
invoiced = Invoiced::Client.new("{YOUR_API_KEY}")

customer = invoiced.Customer.create(
  :name => "Acme",
  :payment_source => {
    :method => "ach",
    :invoiced_token => token
  }
)
```

```php
$invoiced = new Invoiced\Client("{YOUR_API_KEY}");

$customer = $invoiced->Customer->create([
  'name' => "Acme",
  'payment_source' => [
    'method' => "ach",
    'invoiced_token' => $token
  ]
]);
```

```python
import invoiced
client = invoiced.Client("{YOUR_API_KEY}")

customer = client.Customer.create(
  name="Acme",
  payment_source={
    'method': 'ach',
    'invoiced_token': token
  }
)
```

```java
import com.invoiced.entity.Connection;
import com.invoiced.entity.Customer;

Connection invoiced = new Connection("{YOUR_API_KEY}", false);

Customer customer = invoiced.newCustomer();
customer.name = "Acme";
customer.payment_source = token;
customer.create();
```

Or if this is an existing customer then you can make a similar call to update the customer (assuming you have already [retrieved the customer](https://invoiced.com/docs/api/#retrieve-a-customer)):

```bash
curl "https://api.invoiced.com/customers/CUSTOMER_ID" \
  -u {API_KEY}: \
  -d payment_source[method]=ach \
  -d payment_source[invoiced_token]={CAPTURED_TOKEN}
```

```ruby
customer.payment_source = {
  :method => "ach",
  :invoiced_token => token
}
customer.save
```

```php
$customer->payment_source = [
  'method' => "ach",
  'invoiced_token' => $token
];
$customer->save();
```

```python
customer.payment_source = {
  'method': "ach",
  'invoiced_token': token
}
customer.save()
```

```java
customer.payment_source = token;
customer.save();
```

## Gateway tokenization

Some payment gateways support their own payment information tokenization scheme, often coupled with their own UI components for capturing payment information. One such example is the Stripe gateway.

If your payment gateway supports tokenization then you can tokenize payment information directly on the payment gateway and pass that token to Invoiced. For example, if you are using Stripe's front-end components to capture payment information and have a Stripe token then you can pass that token to Invoiced and we will save it on your customer.

### 1. Tokenize payment information on your gateway

This step will depend on your payment gateway. For example, here is [Stripe's documentation](https://stripe.com/docs/quickstart) for tokenizing payment information. You should get a Stripe token as a result of this process.

### 2. Add gateway token to the customer

If this is a new customer then you can pass in the Invoiced token like below:

```bash
curl "https://api.invoiced.com/customers" \
  -u {API_KEY}: \
  -d name="Acme" \
  -d payment_source[method]=credit_card \
  -d payment_source[gateway_token]={CAPTURED_TOKEN}
```

```ruby
require "invoiced"
invoiced = Invoiced::Client.new("{YOUR_API_KEY}")

customer = invoiced.Customer.create(
  :name => "Acme",
  :payment_source => {
    :method => "credit_card",
    :gateway_token => token
  }
)
```

```php
$invoiced = new Invoiced\Client("{YOUR_API_KEY}");

$customer = $invoiced->Customer->create([
  'name' => "Acme",
  'payment_source' => [
    'method' => "credit_card",
    'gateway_token' => $token
  ]
]);
```

```python
import invoiced
client = invoiced.Client("{YOUR_API_KEY}")

customer = client.Customer.create(
  name="Acme",
  payment_source={
    'method': "credit_card",
    'gateway_token': token
  }
)
```

```java
import com.invoiced.entity.Connection;
import com.invoiced.entity.Customer;

Connection invoiced = new Connection("{YOUR_API_KEY}", false);

Customer customer = invoiced.newCustomer();
customer.name = "Acme";
customer.payment_source = token;
customer.create();
```

Or if this is an existing customer then you can make a similar call to update the customer (assuming you have already [retrieved the customer](https://invoiced.com/docs/api/#retrieve-a-customer)):

```bash
curl "https://api.invoiced.com/customers/CUSTOMER_ID" \
  -u {API_KEY}: \
  -d payment_source[method]=credit_card \
  -d payment_source[gateway_token]={CAPTURED_TOKEN}
```

```ruby
customer.payment_source = {
  :method => "credit_card",
  :gateway_token => token
}
customer.save
```

```php
$customer->payment_source = [
  'method' => "credit_card",
  'gateway_token' => $token
];
$customer->save();
```

```python
customer.payment_source = {
  'method': "credit_card",
  'gateway_token': token
}
customer.save()
```

```java
customer.payment_source = token;
customer.save();
```