# WhatsApp Sales Agent 🤖

An AI-powered WhatsApp sales automation agent built for Indian businesses using n8n + Ollama (free, local AI) + Meta WhatsApp Cloud API.

## What it does
- Reads leads from Google Sheets automatically
- Sends personalized WhatsApp messages via Meta API
- AI classifies replies: INTERESTED / NURTURING / NOT INTERESTED
- Auto-assigns leads to salesperson (round robin)
- Updates Google Sheets in real time

## Tech Stack
- n8n (workflow automation)
- Ollama + llama3 (free local AI)
- Meta WhatsApp Cloud API
- Google Sheets

## Cost
- AI cost: ₹0 (runs locally via Ollama)
- WhatsApp: ₹500-1000/month only
- No OpenAI, No paid APIs

## Setup
1. Import workflow JSON into n8n
2. Add your Meta WhatsApp credentials
3. Connect Google Sheets
4. Run!

## Files
- `cold-outreach-workflow.json` — sends initial WhatsApp messages
- `ai-reply-handler-workflow.json` — handles & classifies replies
