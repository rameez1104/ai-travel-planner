# 🧳 AI Travel Planner Bot  

**✨ Plan your perfect trip in seconds!** This automated workflow generates **personalized travel itineraries** with real-time weather forecasts and delivers them via email — all powered by n8n.  

---

## 🌍 **What It Does**  
✅ **User-Friendly Form:** Collects destination, dates, and email.  
📍 **Smart Geocoding:** Converts destinations to coordinates (OpenCage).  
🌦️ **Hyperlocal Weather:** Daily forecasts via Open-Meteo.  
🤖 **AI Magic:** Generates detailed itineraries using **OpenAI GPT-3.5-Turbo**.  
✉️ **Email Delivery:** Sends a beautifully formatted itinerary via **Mailjet**.  

---

## 🛠️ **Technologies Used**  

| **Tool / API**       | **Purpose**                          |
|----------------------|--------------------------------------|
| [n8n](https://n8n.io) | Workflow automation (no-code/low-code) |
| [OpenAI](https://openai.com) | AI itinerary generation |
| [Open-Meteo](https://open-meteo.com) | Free weather API |
| [Mailjet](https://mailjet.com) | Email delivery service |
| **OpenCage** (hidden in your JSON) | Geocoding addresses to coordinates |

---

## 🧩 **Workflow Overview**  

graph TD;
  A[Form Trigger] --> B[Set Node: Prepare Data]
  B --> C[HTTP: Geocode Destination]
  C --> D[Set Node: Extract Lat/Lng]
  D --> E[Code: Expand Dates]
  E --> F[HTTP: Fetch Weather]
  F --> G[Code: Format Weather]
  B --> H[HTTP: OpenAI Itinerary]
  G --> I[Merge Node]
  H --> I
  I --> J[Code: Create HTML Email]
  J --> K[Mailjet: Send Email]

## 🚀 Quick Start

### Prerequisites
- [n8n installed](https://docs.n8n.io/choose-n8n/) (local/Docker/cloud)
- API keys for:
  - [OpenAI](https://platform.openai.com/api-keys) (or [OpenRouter](https://openrouter.ai/keys))
  - [Open-Meteo](https://open-meteo.com/en/docs) (no key needed)
  - [Mailjet](https://app.mailjet.com/account/api_keys)
  - [OpenCage](https://opencagedata.com/api#quickstart) (optional)

### Deployment
1. **Import the workflow**:
   ```bash
   curl -O https://raw.githubusercontent.com/your-username/your-repo/main/travel_plan.json
