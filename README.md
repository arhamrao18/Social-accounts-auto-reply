<div align="center">

# 🤖 AI Auto-Reply for Social Messaging (LinkedIn & Instagram)

**Never miss a lead again. An AI agent that reads, understands, and replies to your social messages — automatically.**

[![n8n](https://img.shields.io/badge/built%20with-n8n-orange?style=flat-square)](https://n8n.io)
[![Instagram](https://img.shields.io/badge/platform-Instagram-E4405F?style=flat-square&logo=instagram&logoColor=white)](#)
</div>

---

## 💡 The Problem

Every business today runs messages across multiple platforms — LinkedIn, Instagram, WhatsApp, and more. And the same thing keeps happening:

- A lead messages at 11 PM. You reply the next afternoon.
- By then, they've already gone to a competitor who replied in 5 minutes.
- You're manually checking 3–4 apps a day just to keep up.
- Casual "hey, how are you" messages and serious business inquiries all land in the same inbox — with no way to tell them apart at a glance.

Response time — not price, not quality — is quietly costing businesses their leads.

## ✅ The Solution

This workflow connects your social accounts through a single unified messaging API and puts an AI agent behind your inbox:

- 🔌 Connects LinkedIn and Instagram accounts through **Unipile's unified messaging API**
- 🧠 Understands the difference between **casual small talk** and a **real business inquiry**
- 📚 Pulls accurate answers from your **own business knowledge base** — services, pricing, portfolio, FAQs — never generic AI fluff
- 💬 Replies instantly, in the **same language and tone** the sender used
- 🔁 Never replies to its own messages — built-in loop protection
- 🕒 Works around the clock, so no lead waits hours for a response

---

## 🖼️ Preview

<div align="center">
  <table>
    <tr>
      <td><img src="assets/preview-1.png" alt="Workflow Overview" width="400"></td>
      <td><img src="assets/preview-2.png" alt="AI Agent in Action" width="400"></td>
    </tr>
  </table>
</div>

---

## 🗺️ How It Works

| Step | Node | What It Does |
|------|------|---------------|
| 1 | **Trigger** (Webhook or Scheduled Poll) | Detects a new incoming message on LinkedIn or Instagram |
| 2 | **Sender Filter** | Ignores messages sent by the account owner — prevents reply loops |
| 3 | **AI Agent** | Reads the message and decides: casual reply, or business inquiry |
| 4 | **Business Knowledge Base** (Vector Store tool) | Retrieved only for business-related questions — pricing, services, portfolio, FAQs |
| 5 | **Reply via Unipile API** | Sends the AI-generated response back to the original platform and chat |

```
New Message → Filter (not my own) → AI Agent ⇄ Knowledge Base → Reply sent via Unipile
```

---

## 🧰 Requirements

- An active [n8n](https://n8n.io) instance (Cloud or self-hosted)
- A [Unipile](https://www.unipile.com) account with LinkedIn and/or Instagram connected
- A Unipile **API key** and **DSN** (account endpoint)
- An LLM provider credential for the AI Agent (e.g. OpenAI, Google Gemini)
- A business knowledge base document (services, pricing, portfolio, FAQs) stored in Google Drive or similar

---

## 🚀 Setup

1. **Import the workflow** JSON into your n8n instance.
2. Add your **Unipile API key** to the HTTP Request nodes (webhook creation and reply-sending).
3. Connect your **LLM credential** (OpenAI / Gemini) to the AI Agent's chat model node.
4. Upload your **business knowledge base file**, connect it via the ingestion branch, and run it once to populate the vector store.
5. Register your **webhook URL** with Unipile (or configure the scheduled polling trigger, if using that mode).
6. Activate the workflow. ✅
7. Send a test message from another account to confirm the AI replies correctly.

---

## 🧠 AI Behavior

The AI Agent runs on two modes, defined entirely by its system prompt:

- **Casual Mode** — greetings and small talk get a warm, natural, human-sounding reply. No business info is volunteered.
- **Business Mode** — pricing, services, portfolio, and availability questions are answered strictly from the connected knowledge base — never invented.

The agent always replies in the same language and tone the sender used, and keeps responses concise and personalized rather than templated.

---

## 🛡️ Safety Features

- **Loop protection** — the workflow checks `is_sender` before responding, so it never replies to its own messages.
- **Grounded answers only** — business questions are answered strictly from the knowledge base document, not made up by the model.
- **Human handoff ready** — the system prompt can be extended to flag conversations that need a real person.

---

## 🧭 Possible Enhancements

- Add WhatsApp, Facebook, and Telegram through the same Unipile connection
- Conversation memory for more natural multi-turn replies
- Automatic lead capture into a CRM (Google Sheets / Airtable) with hot / warm / cold scoring
- Business-hours logic for after-hours auto-responses
- Analytics dashboard tracking response time and lead volume

---

## 📄 License

This project is open for personal and commercial use. Attribution appreciated but not required.

---

<div align="center">
  <sub>Built to make sure no message — and no lead — ever waits too long for a reply.</sub>
</div>
