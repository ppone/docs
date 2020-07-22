# Customer Portal

The customer portal is a self-serve website where your customers can go to handle all billing related functions from your business. The customer portal is provided by Invoiced with no coding experience or extra setup required. Customers can access the customer portal at anytime and from anywhere with an internet connection. With your customer portal, customers can access the following features:

* view and pay invoices
* download receipts for past payments
* manage subscriptions
* update payment information
* view and approve estimates

[![Customer Portal My Account](/docs/img/billing-portal.png)](/docs/img/billing-portal.png)

When customers access an invoice via the View Invoice link received in the invoice email, the customer will be taken directly to the invoice to be paid. The customer will have the option to view the invoice and access the main customer portal screen when on an selected invoice. 

## Usage 

Your customer portal is hosted at yourusername.invoiced.com where yourusername matches your Invoiced username in **Settings** &rarr; **Business Profile**. Any customer facing activity happens on this domain, like viewing invoices or paying. Customers can also access the customer portal by going directly to this URL.

### System Requirements

We strive to make the customer portal work with as many web browsers as possible, although a recently updated web browser is recommended. In order to access the full functionality, the visitor's browser must be configured with:
* Javascript enabled
* Cookies enabled
* TLS v1.2 or above

## Signing In 

Customers must be signed in to access the customer portal. We've made signing in as simple as possible while remaining highly secure. There are a few ways that customers can sign in:

1. *Email sign in*
    Customers can visit your customer portal (yourusername.invoiced.com) directly and request a sign in link by simply entering in their email address. We will then immediately send them an email with a *Sign In* button.
    The email address provided must match a main email address or attached contact for a customer profile in your Invoiced account. We will only send a sign in link to email addresses matching this criteria.
2. *Magic Links*
    Magic Links allow you to securely generate URLs to sign customers into the customer portal. This allows you to transparently sign users into the customer portal from your app or website without requiring an additional login step. We only recommend generating a sign in link for users that you have already authenticated through your own login system.
    Magic Links can be generate through the [API](https://www.invoiced.com/resources/docs/dev/single-sign-on) or through the dashboard by opening a customer profile and clicking *Actions* &rarr; *Generate Sign In Link*.
3. *Sign up pages*
    We temporarily sign in any customers when they sign up from a sign up page. On the thank you page there is a *Go to My Account* button.
4. *Manage Subscription links*
    We temporarily sign in customers when they click on the *Manage Subscription* button on subscription email notices. This allows customers to easily update payment information.

## Leave a Comment on Invoices 

Customers can provide feedback on their invoices in the customer portal by adding a comment to the invoices. This allows customers to ask questions regarding the information on the invoice as well as resolve any billing issues that might arise. 

Invoiced will also flag the customers invoice if a comment is left and alert the users on the Account profile. This gives the business an easy way to filter out invoices that need attention. Once a response is left on the comment, the invoice can be marked as resolved to remove from the needs attention filter.

## Google Analytics Tracking

You can include the Google Analytics tracking script on all customer portal and sign up pages. This enables you to track usage and adoption of the customer portal.

Setting up Google Analytics:
1. Go to **Settings** &rarr; **Customer Portal** in the Invoiced application.
2. Enter in your Google Analytics tracking ID (i.e. UA-XXXX-Y)
3. Click **Save**.

Going forward you will start to see activity in Google Analytics for customer portal traffic.

## Custom CSS and Javascript

You can modify the look and feel of the customer portal by providing your own CSS stylesheet. The stylesheet will be added in addition to the default stylesheet on all customer portal pages. This can be setup in **Settings** &rarr; **Customer Portal** &rarr; **Custom CSS**.

You also add Javascript to the customer portal in **Settings** &rarr; **Customer Portal** &rarr; **Custom Javascript**. Please keep in mind that when embedding external scripts or making AJAX calls to external services that there is a content security policy in place to keep customers more secure. If you find that a source is blocked, please contact [support@invoiced.com](mailto:support@invoiced.com) for assistance.