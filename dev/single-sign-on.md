# Single Sign-On

With Single Sign-On (SSO) customers can seamlessly sign into your customer portal from your app or website.

Our SSO feature lets you securely generate URLs to sign customers into your [customer portal](/docs/guides/billing-portal). This is perfect for redirecting users already authenticated within your app or service into your customer portal without the need for them to sign in once more.

## Generating SSO URLs

1. Obtain your SSO key from the dashboard
   
   You can grab the secret key for generating SSO URLs for your account in **Settings** &rarr; **Developers** &rarr; **Single Sign-On** within the dashboard.

   **WARNING**: Keep your SSO key secret! It should only be used on servers under your control and never exposed in client-side code.

2. Generate an SSO token

   Using your SSO key you can generate [JWT tokens](https://jwt.io) from your backend that tell us which customer to sign in.
  
   Choose your language:
   
   <div class="language-selector">
       <a href="#" class="btn btn-link" data-lang="ruby">Ruby</a>
       <a href="#" class="btn btn-link" data-lang="php">PHP</a>
       <a href="#" class="btn btn-link" data-lang="java">Java</a>
   </div>

   ```ruby
   require "invoiced"
   client = Invoiced::Client.new("{YOUR_API_KEY}", false, "{YOUR_SSO_KEY}")
   
   customerId = 1234
   ttl = 3600 # 1 hour
   
   token = client.generate_sign_in_token(customerId, ttl)
   ```
   
   ```php
   use Invoiced\Client;
   $invoiced = new Client("{YOUR_API_KEY}", false, "{YOUR_SSO_KEY}");
   
   $customerId = 1234;
   $ttl = 3600; // 1 hour

   $token = $client->generateSignInToken($customerId, $ttl);
   ```
   
   ```java
   import com.invoiced.util.SingleSignOn;
   SingleSignOn sso = new SingleSignOn("{YOUR_SSO_KEY}");
   
   int customerId = 1234;
   int ttl = 3600; // 1 hour
   token = sso.generateToken(customerId, ttl);
   ```

3. Build the SSO URL

   Now you can plug your freshly generated token into an SSO URL (replace `yourcompany` with your Invoiced username):

   `https://{yourcompany}.invoiced.com/login/{generated_token}`

   You can now link your freshly generated SSO URL from your website or else redirect users here.

   ```ruby
   url = "https://yourcompany.invoiced.com/login/#{token}"
   ```
   
   ```php
   $url = "https://yourcompany.invoiced.com/login/$token";
   ```
   
   ```java
   String url = "https://yourcompany.invoiced.com/login/" + token
   ```
   
## Generating SSO tokens without a client library

If you are using a language not supported with an official Invoiced client library then you can still generate single sign-on URLs. The steps to generate a JWT token will vary by language, however, there are many open source libraries that make it a simple process.

Any JWT tokens you generate should be signed using the `HS256` algorithm with your SSO key. The token should have the following parameters for the header:

```bash
{
 "alg": "HS256",
 "typ": "JWT"
}
```

And the following parameters for the payload:

```
{
 "sub": "{invoiced_customer_id}",
 "iss": "Ruby Backend",
 "exp": 1455564948
}
```

- The `sub` parameter should be the ID of the customer on Invoiced you are signing the user in as.
- The `iss` parameter should be a string to identify the service that generated the token (any value works here).
- The `exp` parameter should be a [UNIX timestamp](https://en.wikipedia.org/wiki/Unix_time) to indicate when the URL should expire.

This will generate a token similar to this:

`eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwiaXNzIjoiUnVieSBCYWNrZW5kIiwiZXhwIjoxNDU1NTY0OTQ4fQ.LXu-zcMTF8ikMSRrSVYnP0szyRZuqQOAorHAsDrfwPs`

We recommend taking a look at [jwt.io](https://jwt.io) to verify that tokens you generate are valid and to find client libraries in your language.

### Example

Here is an example showing how to generate an SSO URL in Ruby with the `jwt` gem (as opposed to using the invoiced-ruby library):

```
require 'jwt'

sso_key = '{sso_key_from_dashboard}'

exp = Time.now + 86400 # link expires in 1 day

payload = {
:sub => 1234, # invoiced customer ID
:iss => "Ruby Backend",
:exp => exp.to_i
}

token = JWT.encode payload, sso_key, 'HS256'

# eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjEyMzQsImlzcyI6IlJ1YnkgQmFja2VuZCIsImV4cCI6MTQ1NTY1MjIxMH0.7kClQ2UAVEZ7xYus7ZHGRePnzDG5mBrcgIo6rZuo-Dw
puts token

url = "https://yourcompany.invoiced.com/login/#{token}"

# https://yourcompany.invoiced.com/login/eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjEyMzQsImlzcyI6IlJ1YnkgQmFja2VuZCIsImV4cCI6MTQ1NTY1MjIxMH0.7kClQ2UAVEZ7xYus7ZHGRePnzDG5mBrcgIo6rZuo-Dw
puts url
```