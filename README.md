# 🛒 Allegro Order Agent — n8n

> New Allegro order → AI parses details → auto-replies to buyer → updates BaseLinker status → logs to Google Sheets. Full order automation for Polish e-commerce.

![n8n](https://img.shields.io/badge/n8n-workflow-FF6B6B?style=flat-square)
![Groq](https://img.shields.io/badge/Groq-LLaMA%203.3%2070B-F55036?style=flat-square)
![BaseLinker](https://img.shields.io/badge/BaseLinker-API-0066CC?style=flat-square)
![Allegro](https://img.shields.io/badge/Allegro-orange?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-green?style=flat-square)

## ✨ What it does

1. **Detects** new order on Allegro via BaseLinker webhook
2. **Parses** order details: product, buyer, address, payment status
3. **Generates** personalized confirmation message with Groq AI
4. **Replies** to buyer automatically via Allegro messaging
5. **Updates** order status in BaseLinker
6. **Logs** everything to Google Sheets for analytics

## 🏗️ Architecture

```
Allegro New Order
        │
        ▼
┌──────────────┐
│  BaseLinker   │  fetches order details
│  Webhook      │  buyer, product, address, status
└──────┬───────┘
       │
       ▼
┌──────────────┐
│   Groq AI     │  generates personalized
│               │  confirmation message in Polish
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ BaseLinker    │  sends message to buyer
│ Send Message  │  updates order status
└──────┬───────┘
       │
       ▼
┌──────────────┐
│ Google Sheets │  logs order analytics
└──────────────┘
```

## 💡 Auto-reply Example

```
Dzień dobry Panie Marcinie!

Dziękujemy za zamówienie produktu "Słuchawki Sony WH-1000XM5".
Zamówienie nr 1234567 zostało przyjęte do realizacji.

Przewidywany czas wysyłki: 1-2 dni robocze.
Numer śledzenia zostanie przesłany po nadaniu paczki.

Pozdrawiamy,
Sklep ABC
```

## 🚀 Setup

1. Import `workflow.json` into n8n
2. Add credentials: BaseLinker API key, Groq API key, Google Sheets OAuth2
3. Set your BaseLinker store ID
4. Configure reply template language (PL/EN/UA)
5. Activate workflow

## 🛠️ Tech Stack

| Component | Technology |
|-----------|-----------|
| Automation | n8n |
| E-commerce | BaseLinker API + Allegro |
| AI Replies | Groq — LLaMA 3.3 70B |
| Storage | Google Sheets |

---
*Built by [VinteliVision](https://vintelivision.com) — AI automation for Polish e-commerce.*
