# Magic Links

With Magic Links customers can seamlessly sign into your customer portal from your app or website.

Magic Links are a secure passwordless authentication mechanism that lets you securely generate URLs to sign customers into your [customer portal](/resources/docs/guides/billing-portal). This is perfect for redirecting users already authenticated within your app or service into your customer portal without the need for them to sign in once more.

## Generating Magic Links

1. Obtain your Magic Link key from the dashboard
   
   You can grab the secret key for generating Magic Links for your account in **Settings** &rarr; **Developers** &rarr; **Magic Links** within the dashboard.

   **WARNING**: Keep your Magic Link key secret! It should only be used on servers under your control and never exposed in client-side code.

2. Generate a sign in token

   Using your Magic Link key you can generate [JWT tokens](https://jwt.io) from your backend that tell us which customer to sign in.
  
   Choose your language:
   
   <div class="language-selector">
       <a href="#" class="btn btn-link" data-lang="ruby">Ruby</a>
       <a href="#" class="btn btn-link" data-lang="php">PHP</a>
       <a href="#" class="btn btn-link" data-lang="java">Java</a>
   </div>

   ```ruby
   require "invoiced"
   client = Invoiced::Client.new("{YOUR_API_KEY}", false, "{YOUR_MAGIC_LINK_KEY}")
   
   customerId = 1234
   ttl = 3600 # 1 hour
   
   token = client.generate_sign_in_token(customerId, ttl)
   ```
   
   ```php
   use Invoiced\Client;
   $invoiced = new Client("{YOUR_API_KEY}", false, "{YOUR_MAGIC_LINK_KEY}");
   
   $customerId = 1234;
   $ttl = 3600; // 1 hour

   $token = $client->generateSignInToken($customerId, $ttl);
   ```
   
   ```java
   import com.invoiced.util.SingleSignOn;
   SingleSignOn magicLink = new SingleSignOn("{YOUR_MAGIC_LINK_KEY}");
   
   int customerId = 1234;
   int ttl = 3600; // 1 hour
   token = magicLink.generateToken(customerId, ttl);
   ```

3. Build the URL

   Now you can plug your freshly generated token into a sign in URL (replace `yourcompany` with your Invoiced username):

   `https://{yourcompany}.invoiced.com/login/{generated_token}`

   You can now link your freshly generated URL from your website or else redirect users here.

   ```ruby
   url = "https://yourcompany.invoiced.com/login/#{token}"
   ```
   
   ```php
   $url = "https://yourcompany.invoiced.com/login/$token";
   ```
   
   ```java
   String url = "https://yourcompany.invoiced.com/login/" + token
   ```
   
## Generating Magic Links without a client library

If you are using a language not supported with an official Invoiced client library then you can still generate Magic Links. The steps to generate a JWT token will vary by language, however, there are many open source libraries that make it a simple process.

Any JWT tokens you generate should be signed using the `HS256` algorithm with your Magic Link key. The token should have the following parameters for the header:

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

Here is an example showing how to generate a Magic Link in Ruby with the `jwt` gem (as opposed to using the invoiced-ruby library):

```
require 'jwt'

magic_link_key = '{magic_link_key_from_dashboard}'

exp = Time.now + 86400 # link expires in 1 day

payload = {
:sub => 1234, # invoiced customer ID
:iss => "Ruby Backend",
:exp => exp.to_i
}

token = JWT.encode payload, magic_link_key, 'HS256'

# eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjEyMzQsImlzcyI6IlJ1YnkgQmFja2VuZCIsImV4cCI6MTQ1NTY1MjIxMH0.7kClQ2UAVEZ7xYus7ZHGRePnzDG5mBrcgIo6rZuo-Dw
puts token

url = "https://yourcompany.invoiced.com/login/#{token}"

# https://yourcompany.invoiced.com/login/eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOjEyMzQsImlzcyI6IlJ1YnkgQmFja2VuZCIsImV4cCI6MTQ1NTY1MjIxMH0.7kClQ2UAVEZ7xYus7ZHGRePnzDG5mBrcgIo6rZuo-Dw
puts url
```