# 🤖 Smart CRM WhatsApp Automation

> Automated post-purchase follow-up system in Moroccan Darija via WhatsApp & Email, with automatic VIP classification.

---

## 📋 Overview

This n8n workflow automates customer relationship management after every purchase. It sends personalized follow-up messages in **Moroccan Darija** through WhatsApp and Email, classifies customers as **VIP** based on their purchase history, and logs everything in Airtable.

---

## 🛠️ Tech Stack

| Tool | Role |
|------|------|
| **n8n** | Workflow automation engine |
| **Airtable** | Customer database & CRM |
| **Evolution API** | WhatsApp messaging gateway |
| **OpenAI GPT-4.1-mini** | Personalized message generation in Darija |
| **Gmail** | Email follow-up delivery |

---

## ✨ Key Features

- 🛒 **Trigger on Purchase** — workflow fires automatically after each new order
- 💬 **WhatsApp Follow-up** — sends warm thank-you messages in Moroccan Darija via Evolution API
- 📧 **Email Follow-up** — professional follow-up email sent via Gmail
- 🌟 **VIP Auto-Classification** — customers exceeding purchase threshold are automatically tagged as VIP in Airtable
- 🤖 **AI-Generated Messages** — GPT-4.1-mini crafts personalized, natural-sounding messages per customer
- 📊 **Airtable Sync** — all interactions are logged and customer records updated in real-time

---

## 🔄 Workflow Architecture

```
New Purchase Event
       │
       ▼
  Airtable Lookup (Customer Record)
       │
       ▼
  GPT-4.1-mini (Generate Darija Message)
       │
    ┌──┴──┐
    ▼     ▼
WhatsApp  Gmail
(Evolution API)
    │
    ▼
Airtable Update (VIP Check & Log)
```

---

## 📁 Repository Structure

```
.
├── README.md          # Project documentation
├── workflow.json      # n8n workflow export (credentials removed)
└── .gitignore         # Excludes sensitive files
```

---

## 🚀 Getting Started

### Prerequisites

- [n8n](https://n8n.io/) instance (self-hosted or cloud)
- Airtable account with a Customers base
- Evolution API instance configured with WhatsApp
- OpenAI API key
- Gmail account connected via OAuth2

### Setup Steps

1. **Clone this repository**
   ```bash
   git clone https://github.com/mustaphatb1975/smart-crm-whatsapp-automation.git
   ```

2. **Import the workflow**
   - Open your n8n instance
   - Go to **Workflows → Import from File**
   - Select `workflow.json`

3. **Configure credentials** in n8n:
   - `Airtable API Key`
   - `Evolution API URL + API Key`
   - `OpenAI API Key`
   - `Gmail OAuth2`

4. **Set workflow variables:**
   - Airtable Base ID & Table name
   - VIP threshold (e.g., 5 purchases or 500 MAD)
   - WhatsApp instance name in Evolution API

5. **Activate the workflow** and test with a sample purchase event.

---

## ⚙️ Configuration

| Variable | Description | Example |
|----------|-------------|----------|
| `AIRTABLE_BASE_ID` | Your Airtable base ID | `appXXXXXXXXXXXXXX` |
| `VIP_THRESHOLD` | Purchase count for VIP status | `5` |
| `WHATSAPP_INSTANCE` | Evolution API instance name | `my-business` |
| `FROM_EMAIL` | Sender Gmail address | `crm@yourdomain.com` |

---

## 🔒 Security Notes

- All credentials have been **removed** from `workflow.json`
- Never commit `.env` files or API keys
- Use n8n's built-in **Credentials Manager** for all secrets
- WhatsApp numbers are anonymized in this repository

---

## 👤 Author

**Mustapha Taleb** — AI Automation Engineer  
📍 Agadir, Morocco  
🔗 [LinkedIn](https://www.linkedin.com/in/talebmustapha/)  
🐙 [GitHub](https://github.com/mustaphatb1975)

---

## 📄 License

MIT License — feel free to use and adapt for your projects.
