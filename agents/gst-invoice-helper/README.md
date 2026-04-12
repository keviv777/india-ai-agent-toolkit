# GST Invoice Helper

An AI-powered n8n workflow designed to generate professional GST invoices in both Hindi and English for Indian businesses. 

## Overview
This automation listens via Webhook for incoming sales or transaction details, uses a Local LLM (Llama 3 via Ollama) to draft a formatted, bilingual GST invoice complete with HSN code, taxable amount, and GST calculations, and returns it dynamically via an API response.

### Workflow Structure
1. **Webhook Node**: Triggers the workflow securely on a POST request to `/webhook/gst-invoice`.
2. **Basic LLM Chain**: Runs the prompt logic via LangChain against a locally hosted language model.
3. **Ollama Chat Model**: A local fallback or primary model mechanism running `llama3:latest` for zero-cost, high-speed AI generation.
4. **Respond to Webhook Node**: Returns the final AI-generated invoice back to the app, tool, or user who fired the webhook.

## 📸 Workflow Screenshot
![GST Invoice Helper Workflow](gst-invoice-workflow.png)
*n8n workflow: Webhook → Basic LLM Chain → Ollama Chat Model → Respond to Webhook*

## Setup Instructions

### Prerequisites
1. **n8n**: Tested with `n8n` properly installed.
2. **Ollama**: You must have [Ollama](https://ollama.com/) installed and running locally with the Llama 3 model. 
   - Run `ollama run llama3:latest` to ensure it is installed.

### Importing the Workflow
1. In your n8n workspace, go to **Workflows**.
2. Click **Add Workflow** -> **Import from File** (or copy-paste the JSON).
3. Select the `gst-invoice-helper-workflow.json` file in this directory.
4. Ensure your **Ollama Chat Model** credential points to `http://localhost:11434` (or your respective Ollama URL).
5. Ensure the top-right toggle is **Active**.

## How to Test

You can manually trigger this workflow via `curl`. Once the workflow is **Active**, run the following command in your terminal:

```bash
curl -s -X POST http://localhost:5678/webhook/gst-invoice \
  -H "Content-Type: application/json" \
  -d '{
    "customer": "Ramesh Traders",
    "item": "Steel Pipes",
    "amount": 10000,
    "gst_rate": 18
  }'
```

*(Note: If you are testing this from the n8n canvas using "Test Workflow" rather than full activation, replace `/webhook/` with `/webhook-test/` in the URL).*
