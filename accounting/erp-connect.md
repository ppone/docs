# ERP Connect

ERP Connect allows you to securely integrate your on-premise ERP system with Invoiced.

[![ERP Connect Data Flow](/docs/img/erp-connect.png)](/docs/img/erp-connect.png)

## Capabilities

ERP Connect can upload data in real-time to your Invoiced account(s) through one of the supported data sources. It also has the ability to download data from Invoiced on a daily, weekly, or monthly schedule.

Data sources for ingesting data:
- Spreadsheet files (CSV, XLS, XLSX)
- Invoice file attachments (any file type)
- Invoice PDFs

File formats for outputting data:
- CSV

## Installation

1. [Download ERP Connect here](https://invoiced.com/download) for your operating system.

2. Open the downloaded installer on the computer you intend to keep ERP Connect running. Please keep mind of the minimum system requirements below.

3. The installer will guide you through the installation process.

### System Requirements

Operating System | Minimum Supported Version
-----------------|---------------------------
Windows          | Windows 7 or above
Mac OS X         | OS X 10.10 or above

Other Requirements:
- At least 2GB of memory
- 1 GHz+ processor
- 300MB of disk space

## Usage

In order to use ERP Connect you must first have an Invoiced account. Once you have an Invoiced account and ERP Connect installed then you are ready to begin using the application.

### Creating a Mapping

The key concept in ERP Connect is a mapping. Mappings describe a data flow between Invoiced and a third party system.

The first place to start is by adding your Invoiced API key in the **Settings** page. You can obtain an API key from the Invoiced web application at **Settings** &rarr; **Developers**.

With an API key installed you are now ready to create a mapping. Click the **New Mapping** button to begin configuring your data flow. The application will walk you through the setup process.

### Operating ERP Connect

Once configured, ERP Connect will run in the background and execute your data mappings. It is required that the computer remain on for the periods in which ERP Connect should be brokering data with Invoiced.

If you find any issues with your data syncing then you can go to the **Errors** page in the application for troubleshooting.