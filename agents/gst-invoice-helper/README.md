# 🇮🇳 GST Invoice Helper Agent

An n8n workflow designed to automate the process of calculating Indian GST, pushing records to Google Sheets, and notifying the client via WhatsApp. 

## Workflow Overview
1. **Webhook Trigger:** Receives raw invoice data (Base Amount, Client Details, Item Description).
2. **GST Calculation (Code Node):** Automatically calculates CGST & SGST (total 18% standard, customizable) and computes the final grand total in INR.
3. **Google Sheets Integration:** Appends the structured invoice data row into your sales ledger.
4. **WhatsApp Notification:** Sends a customized text to the client with the final billing amount via the Meta WhatsApp Cloud API.

## Requirements
- n8n instance (Self-hosted or Cloud)
- Google Service Account Credentials
- Meta WhatsApp Cloud API token

## How to Import
1. Download the `workflow.json` file in this directory.
2. In your n8n workspace, click on `Import from File` inside a new workflow.
3. Add your credentials to the specific nodes.
