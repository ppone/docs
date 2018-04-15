# File Attachments

Invoiced supports attaching files to invoices in order to give customers more context about a bill.

## Usage

Files can be attached to invoices through the dashboard or programmatically through the API. In this guide we are going to walk you through the complete steps to attach a file to an invoice through the API.

### Choose your language

<div class="language-selector">
	<a href="#" class="btn btn-link" data-lang="bash">Shell</a>
	<a href="#" class="btn btn-link" data-lang="ruby">Ruby</a>
	<a href="#" class="btn btn-link" data-lang="php">PHP</a>
    <a href="#" class="btn btn-link" data-lang="python">Python</a>
    <a href="#" class="btn btn-link" data-lang="java">Java</a>
</div>

### Prerequisites

We don't support uploads through the API at the moment (but the dashboard does). This means that you must host the file somewhere publicly accessible. Once that's done you are ready to send us the URL along with some basic file metadata.

### Create a file

Next we are going to tell Invoiced about your file.

```bash
curl "https://api.invoiced.com/files" \
  -u {API_KEY}: \
  -d url="https://invoiced.com/img/logo-invoice.png" \
  -d name="logo-invoice.png" \  # filename
  -d size=6936 \                # size in bytes
  -d type="image/png"           # MIME type
```

```ruby
require "invoiced"
invoiced = Invoiced::Client.new("{YOUR_API_KEY}")

file = invoiced.File.create(
  :url => "https://invoiced.com/img/logo-invoice.png",
  :name => "logo-invoice.png",  # filename
  :size => 6936,                # size in bytes
  :type => "image/png"          # MIME type
)
```

```php
$invoiced = new Invoiced\Client("{YOUR_API_KEY}");

$file = $invoiced->File->create([
  'url' => "https://invoiced.com/img/logo-invoice.png",
  'name' => "logo-invoice.png", // filename
  'size' => 6936,               // size in bytes
  'type' => "image/png"         // MIME type
]);
```

```python
import invoiced
client = invoiced.Client("{YOUR_API_KEY}")

file = client.File.create(
  url="https://invoiced.com/img/logo-invoice.png",
  name="logo-invoice.png",  # filename
  size=6936,                # size in bytes
  type="image/png"          # MIME type
)
```

```java
import com.invoiced.entity.Connection;
import com.invoiced.entity.File;

Connection invoiced = new Connection("{YOUR_API_KEY}", false);

File file = invoiced.newFile();
file.url = "https://invoiced.com/img/logo-invoice.png";
file.size = 6936;
file.name = "logo-invoice.png";
file.type = "image/png";
file.create();
```

### Attach to an invoice

Once you have created your file you can now attach it to an invoice. This is done by passing in an array of file IDs through the `attachments` parameter when creating or editing an invoice.

In this example we are going to show how to attach a single file when creating a new invoice:

```bash
curl "https://api.invoiced.com/invoices" \
  -u {API_KEY}: \
  # invoice parameters...
  -d attachments[]={FILE_ID}
```

```ruby
invoice = invoiced.Invoice.create(
  # invoice parameters...
  :attachments => [file.id]
)
```

```php
$invoiced->Invoice->create([
  // invoice parameters...
  'attachments' => [$file->id]
]);
```

```python
invoice = client.Invoice.create(
  # invoice parameters...
  attachments=[file.id]
)
```

```java
import com.invoiced.entity.Attachment;
import com.invoiced.entity.Invoice;

Invoice invoice = invoiced.newInvoice();
// invoice parameters...
Attachment[] attachments = new Attachment[1];
attachments[0] = new Attachment();
attachments[0].file = file.id;
invoice.attachments = attachments;
invoice.create();
```

And the file is now attached! It will be available in the client view and dashboard as a downloadable attachment.

### Retrieving attachments for an invoice

You can also retrieve the existing file attachments for an invoice with a simple API query. This might be useful to synchronize the attachments for an invoice with your internal systems.

```bash
curl "https://api.invoiced.com/invoices/{INVOICE_ID}/attachments" \
  -u {API_KEY}:
```

```ruby
attachments, metadata = invoice.attachments
```

```php
list($attachments, $metadata) = $invoice->attachments();
```

```python
attachments, metadata = invoice.attachments()
```

```java
import com.invoiced.entity.Attachment;

Attachment[] attachments = invoice.listAttachments();
```

The call will produce a response like this:

```bash
[
  {
    "id": 13,
    "file": {
      "id": 13,
      "object": "file",
      "name": "logo-invoice.png",
      "size": 6936,
      "type": "image/png",
      "url": "https://invoiced.com/img/logo-invoice.png",
      "created_at": 1464625855
    },
    "created_at": 1464625855
  }
]
```

```ruby
[
  #<Invoiced::Attachment:0x3ff10dd39db4 id=13> JSON: {
    "id": 13,
    "file": {
      "id": 13,
      "object": "file",
      "name": "logo-invoice.png",
      "size": 6936,
      "type": "image/png",
      "url": "https://invoiced.com/img/logo-invoice.png",
      "created_at": 1464625855
    },
    "created_at": 1464625855
  }
]
```

```php
[
  Invoiced\Attachment JSON: {
    "id": 13,
    "file": {
      "id": 13,
      "object": "file",
      "name": "logo-invoice.png",
      "size": 6936,
      "type": "image/png",
      "url": "https://invoiced.com/img/logo-invoice.png",
      "created_at": 1464625855
    },
    "created_at": 1464625855
  }
]
```

```python
[
  <Attachment id=13 at 0x3ff10dd39db4> JSON: {
    "id": 13,
    "file": {
      "id": 13,
      "object": "file",
      "name": "logo-invoice.png",
      "size": 6936,
      "type": "image/png",
      "url": "https://invoiced.com/img/logo-invoice.png",
      "created_at": 1464625855
    },
    "created_at": 1464625855
  }
]
```

```java
[
  com.invoiced.entity.Attachment@1759eafd JSON: {
    "id": 13,
    "object": "attachment",
    "file": {
      "id": 13,
      "object": "file",
      "name": "logo-invoice.png",
      "size": 6936,
      "type": "image/png",
      "url": "https://invoiced.com/img/logo-invoice.png",
      "created_at": 1464625854
    },
    "created_at": 1464625855
  },
  com.invoiced.entity.Attachment@1759eafd JSON: {...},
  com.invoiced.entity.Attachment@1759eafd JSON: {...}
]
```