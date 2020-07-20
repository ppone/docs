# Twilio Integration

Our Twilio integration enables you to send invoices and statements to customers via text messages.

## Setup

We are going to walk you through setting up the Twilio integration. This assumes you have already signed up for a Twilio account. If not, you may [sign up here](https://www.twilio.com/).

1. Get your Twilio SID and Auth Token from the Twilio dashboard. 

   [![Obtaining Twilio API Key](/docs/img/twilio-settings.png)](/docs/img/twilio-settings.png)

2. Go to **Settings** &rarr; **Integrations** of the Invoiced application. Click **Connect** underneath the *Twilio* integration.

3. Enter in your Twilio SID and Auth Token. Click **Save**.

4. Click on **Configure** underneath the *Twilio* integration.

5. Select a phone number in your account that you'd like to send text messages from. If you don't have one yet then click **Buy a new number**.

6. Click **Save** to enable the integration. You are now ready to start sending text messages!

## Sending a text message

You can send both account statements and individual invoices through a text message. In this tutorial we are going to walk you through it.

### Sending an invoice

1. Open up the invoice in the Invoiced application.

2. Click **Actions** &rarr; **Send Invoice**.

3. Click the **Text Message** option.

4. Add a mobile phone contact to your customer's account by clicking **Add Contact**. At a minimum you need to add a name, phone number, and check the *Can receive text messages* options.

5. Enter in your message, and remember to keep it short! Then click **Send**.

### Sending an account statement

1. Open up the customer's account in the Invoiced application.

2. Click **Actions** &rarr; **Generate Statement**.

3. Enter in the parameters for the statement and click **Send**.

4. Click the **Text Message** option.

5. Add a mobile phone contact to your customer's account by clicking **Add Contact**. At a minimum you need to add a name, phone number, and check the *Can receive text messages* options.

6. Enter in your message, and remember to keep it short! Then click **Send**.

## Limitations

Text messages have a few limitations in place to help you stay compliant with regulations.

- You can only send text messages between 8am and 9pm in your local time zone.
- If customers reply *STOP* or *UNSUBSCRIBE* then you will not be able to send them a message ([more details here](https://support.twilio.com/hc/en-us/articles/223134027-Twilio-support-for-opt-out-keywords-SMS-STOP-filtering-)).
- You can only send a text message to the same phone number once per day, in order to prevent you from accidentally spamming your customers.
- Twilio is not a free service (although it is very affordable). Any text messages you send will incur a charge. See [Twilio's pricing](https://www.twilio.com/sms/pricing).
