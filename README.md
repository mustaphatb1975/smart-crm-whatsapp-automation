# 🤖 Smart CRM WhatsApp Automation

> Intelligent CRM system that sends automatic follow-up messages in **Moroccan Darija** via WhatsApp and Email after each purchase, with automatic VIP classification.

---

## 🧠 System Overview

This n8n workflow automates post-purchase customer engagement for Moroccan businesses. It uses AI to write culturally authentic follow-up messages in Moroccan Darija (Arabic script), delivered via WhatsApp and Email.

---

## ⚙️ Tech Stack

| Tool | Role |
|------|------|
| **n8n** | Workflow automation engine |
| **Airtable** | Customer CRM database |
| **Evolution API** | WhatsApp messaging |
| **OpenAI GPT-4.1-mini** | AI message generation in Darija |
| **Gmail** | Email follow-up delivery |

---

## 🔄 Workflow Logic

```
Schedule Trigger (Daily 10:00 AM)
  └─> Airtable: Search customers due for follow-up
        └─> Filter: Has email OR phone number
              ├─> AI Agent: Generate personalized Darija message
              │     ├─> Day 3: Warm thank-you & experience check
              │     └─> Day 10: "We miss you" + soft offer
              ├─> WhatsApp (Evolution API): Send message
              ├─> Gmail: Send email version
              └─> Airtable: Update follow-up sequence & VIP status
```

---

## 🌟 Key Features

- **Moroccan Darija AI Copywriting** — Messages written in authentic Arabic script Darija, not formal Arabic
- **Multi-channel delivery** — WhatsApp + Email simultaneously
- **Automatic VIP Classification** — Customers who reach purchase threshold get VIP status
- **Smart Follow-up Sequences** — Day 3 (satisfaction check) → Day 10 (re-engagement offer)
- **Airtable CRM Integration** — Full customer lifecycle tracking
- **No hardcoded data** — All customer data fetched dynamically

---

## 📋 Airtable Schema Required

**Table: Customers**

| Field | Type | Description |
|-------|------|-------------|
| `Customer Name` | Single line text | Full name |
| `Email` | Email | Customer email |
| `Phone Number` | Phone | WhatsApp number (international format) |
| `Last_Order_Date` | Date | Date of last purchase |
| `Next_Scheduled_Message` | Date | Auto-calculated next follow-up date |
| `Message_Type` | Single select | `day3` or `day10` |
| `Followup_Sequence_Num` | Number | Current sequence step |
| `VIP Status` | Single select | `VIP` or blank |
| `Total_Purchases` | Currency | Lifetime purchase value |

---

## 🚀 Setup Instructions

### 1. Prerequisites
- n8n instance (self-hosted or cloud)
- Airtable account with the schema above
- Evolution API instance connected to WhatsApp
- OpenAI API key (GPT-4.1-mini access)
- Gmail account with OAuth configured in n8n

### 2. Import Workflow
1. Download `workflow.json`
2. In n8n: **Settings → Import from file**
3. Upload `workflow.json`

### 3. Configure Credentials
Update the following in n8n credentials:
- `Airtable API` — Your Airtable API key
- `OpenAI API` — Your OpenAI API key
- `Gmail OAuth2` — Your Gmail account
- `Evolution API` — Your WhatsApp API endpoint + key

### 4. Update Placeholders in Workflow
Search and replace:
- `YOUR_AIRTABLE_BASE_ID` → Your actual Airtable Base ID
- `YOUR_AIRTABLE_TABLE_CUSTOMERS` → Your table ID
- `YOUR_EVOLUTION_API_URL` → Your Evolution API URL

### 5. Activate
- Enable the **Schedule Trigger** node
- Test with a sample customer record
- Monitor via n8n execution logs

---

## 📌 Important Notes

- Phone numbers must be in international format: `+212XXXXXXXXX`
- The AI generates messages in **Moroccan Darija (Arabic script only)** — no Latin, no Classical Arabic
- VIP classification threshold can be adjusted in the workflow logic
- All credentials are stored in n8n credential store, never in the workflow file

---

## 👤 Author

**Mustapha Taleb** — AI Automation Engineer  
📍 Agadir, Morocco  
🔗 [LinkedIn](https://www.linkedin.com/in/talebmustapha/) | [GitHub](https://github.com/mustaphatb1975)

---

## 📄 License

MIT License — Free to use and modify.
