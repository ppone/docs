# Testing

Our sandbox environment makes it easy to build integrations on Invoiced and speeds up the QA process.

## Sandbox

You can sign up for a sandbox account at [sandbox.invoiced.com](https://sandbox.invoiced.com).

In the sandbox you will be able to test out workflows and integrations you are building on Invoiced. The sandbox is identical to our production environment with the exception that it **does not perform any live charges** to credit cards or bank accounts. Sandbox accounts are entirely separate from your production account in order to keep testing isolated.

### API

In order to access the sandbox through the API you must use the `api.sandbox.invoiced.com` endpoint. All of our official client libraries have support for the sandbox built in. You simply pass in your sandbox API key and `true` as the second argument when instantiating a new API client, i.e. `Invoiced::Client.new("{YOUR_SANDBOX_API_KEY}", true)`.

### Payments

When using the test gateway you can use the payment information below to simulate payments in various scenarios.

#### Credit Card

Brand            | Number                 
---------------- | ---------------------- 
Visa             | `4242 4242 4242 4242` 
Visa             | `4111 1111 1111 1111`  
MasterCard       | `5454 5454 5454 5454`
American Express | `3782 822463 10005` 
Discover         | `6011 1111 1111 1117`
Diners Club      | `3056 9309 0259 04`
JCB              | `3530 1113 3330 0000`
UnionPay         | `6200 0000 0000 0005`

#### Credit Card Failures

Brand            | Number                 | Description
---------------- | ---------------------- | -------------
Visa             | `4000 0000 0000 0069`  | Declined charge

#### ACH

Any valid account and routing number will produce a successful charge.

Account Number   | Routing Number        
---------------- | ----------------------
`123456789`      | `110000000`

#### ACH Failures

Account Number   | Routing Number         | Description
---------------- | ---------------------- | -------------
`123123456`      | `123123123`            | Declined charge
`123123893`      | `123123123`            | Pending charge

#### SEPA

IBAN                     | Description
------------------------ | ------------------
`DE89370400440532013000` | Successful charge
`DE62370400440532013001` | Failed charge

#### Other gateways

If you are connecting to a payment gateway other than test in the sandbox then the sandbox will connect to your payment gateway in test mode. This means that you can use test payment sources from your payment gateway instead of live ones. For example, if you connected Stripe as your payment gateway then you can use these [test accounts](https://stripe.com/docs/testing). In test mode, payments will behave identically to live mode without performing any real charges.

### Data Storage and Rate Limiting

**You should not depend on any data stored in the sandbox.** Test data is not guaranteed to be retained, and we might periodically clean out old test data to preserve system resources. Generally this would happen after data has been stale for months.

The sandbox is intented to allow you to build and test without restrictions, however, we could enforce rate limiting or data caps to prevent abuse. In normal scenarios you should never bump into these.

### Clearing data

You can clear all the data in your test account in **Settings** > **Developers** with the **Delete all test data** button. This will clear out data such as customers, invoices, and subscriptions while retaining your settings.