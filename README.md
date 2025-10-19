# Price-Monitoring-Agent-n8n

# 🛒 Amazon Price Monitoring Agent

An **n8n workflow** that automatically tracks Amazon product prices using the **ScrapeOps API** and sends alerts when prices increase or decrease beyond your set limits.

This workflow helps users or businesses keep track of product prices, save time, and make smarter buying decisions — all in one automated setup.

---

## 🚀 Features

* Track prices of multiple Amazon products at once
* Automatically calculate price difference and percentage change
* Set your own **high** and **low** alert thresholds
* Get email alerts when prices drop or rise beyond your limits
* Save all price data to Google Sheets for history and analysis
* Fully automated — runs on a schedule, no manual checking needed

---

## 🧰 Prerequisites

Before starting, make sure you have:

* An **n8n instance** (self-hosted or cloud)
* A **ScrapeOps API key**
* A **Google account** (for Google Sheets)
* An **SMTP email account** (for sending alerts)

---

## ⚙️ Setup Instructions

### 1. Import the Workflow

1. Download the `Amazon_Price_Monitoring_Agent.json` file from this repository.
2. In your **n8n** dashboard, go to:
   **Workflows → Import from File → Select the downloaded JSON file.**

---

### 2. Configure Google Sheets

Create a copy of [this spreadsheet template](https://docs.google.com/spreadsheets/d/1-5_LBZk8hRxe8rEG0A4ujqsE0X8pFX5Ibop-Dlq8FXc/edit?usp=sharing) or create your own with the required structure.
* Set up the "Products to Monitor" sheet with your Amazon ASINs
* Configure the Google Sheets nodes in the workflow to connect to your spreadsheet

### 3. Add Your ScrapeOps API Key

1. Go to your [ScrapeOps Dashboard](https://scrapeops.io/) to get your API key.
2. In your workflow, open the **“ScrapeOps – Amazon Product”** node.
3. Replace the existing API key with your own.

---

### 4. Configure Email Notifications

1. Open the **“Send Email”** node.
2. Add your **SMTP server details**, **username**, and **password**.
3. Customize the email template if needed.

---

### 5. Set the Schedule

Use the **Schedule Trigger** node to run the workflow automatically.
* You can set it to run daily, or multiple times a day like: (every 6–12 hours).
* Choose your local timezone in the node settings.

---

## 🔄 How It Works

1. The workflow reads the list of Amazon ASINs from your Google Sheet.
2. It calls the **ScrapeOps API** to get the current price of each product.
3. It compares the new price with the previous one.
4. If the change is above or below your defined thresholds, it sends an email alert.
5. Each result is saved in your **Google Sheet** for future tracking.

---

## 🧩 Customization Options

* **Alert Thresholds:**
  Adjust `alert_threshold_low` and `alert_threshold_high` in your spreadsheet.

* **Email Design:**
  Edit the email text inside the “Send Email” node.

* **More Notifications:**
  Add nodes for Slack, Telegram, or Discord if you want alerts there too.

---

## 🧠 Troubleshooting

| Problem            | Solution                                                      |
| ------------------ | ------------------------------------------------------------- |
| No product data    | Check your ScrapeOps API key and that you have enough credits |
| No emails sent     | Verify SMTP settings and check your spam folder               |
| Sheet not updating | Make sure n8n has permission to access your Google Sheet      |

---

## 🏗️ Future Improvements

* Add AI-based price prediction
* Visualize trends with a dashboard
* Include support for more e-commerce websites
