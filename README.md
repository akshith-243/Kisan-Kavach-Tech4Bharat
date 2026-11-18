# 🛡️ Kisan Kavach
**Autonomous Market, Weather & Supply-Chain Orchestrator for Small Farmers**  
*Tech4Bharat Hackathon | Theme: Agriculture & Food Processing | Problem Statement 6.1 (Agentic AI)*

---
 
## 📌 Overview
Small and marginal farmers lose **₹5,000–₹20,000** every harvest cycle because urgent cash needs and informal trader debt force them to sell at low local rates, while **20–30%** of produce spoils due to sudden weather shifts and lack of storage.

**Kisan Kavach** is a voice-first, multi-agent AI assistant accessible via a one-tap mobile shortcut, WhatsApp voice notes, and a toll-free local-language helpline. Instead of displaying static price boards, four specialized AI agents collaborate to track live mandi prices within 100 km, prevent local market gluts, poll 2-to-5-day weather forecasts for proactive rain/drying alerts, pool shared trucks and cold storage across neighbors, arrange 70% upfront warehouse credit, and broker fair B2B bulk contracts—while keeping the farmer 100% in control of every decision.

---

## 🚨 Why Small Farmers Lose Money Today
* **Price & Location Blindness:** Farmers sell at their village mandi or farm gate without knowing a mandi 30–50 km away is paying significantly higher rates. Hiring a full commercial truck alone for a small harvest is unaffordable.
* **Weather & Spoilage Losses:** 20–30% of harvested crops rot in open yards due to unseasonal rain, humidity spikes, and inaccessible cold storage.
* **The Middleman Debt Trap:** Most farmers borrow input money for seeds and fertilizers from local commission agents (*Arhtiyas*) and urgently need cash on harvest day to pay farm labor—rendering static price-display apps ineffective.

---

## 👥 Dual-Login Ecosystem & Zero-Friction Access
1. **Farmer Access (App + One-Tap Voice Helpline):** All farmers call or message a single unified helpline via a one-tap phone shortcut or speed-dial (supporting both smartphones and basic keypad phones). Caller ID identifies the farmer's profile, and **Bhashini API** enables natural voice interaction in Telugu, Hindi, and regional dialects without typing.
2. **Verified B2B Bulk Buyer Login:** Wholesale contractors, FPOs, food processors, and retail chains post bulk crop requirements (quantity, grade, delivery window). Buyers cannot lowball individual farmers; Kisan Kavach acts as an autonomous fair-price and bundling broker.

---

## 🤖 Multi-Agent AI Architecture

```text
[Farmer 5-Sec Voice Note / App Tap]  <--- (Bhashini STT/TTS | WhatsApp / IVR)
                 │
                 ▼
    ┌──────────────────────────┐
    │ Central Coordinator Agent│ (Applies Cash Urgency, Spoilage Limits & Risk Boundaries)
    └────┬───────┬────────┬────┘
         │       │        │
   ┌─────┘       │        └─────┐
   ▼             ▼              ▼
┌──────────┐ ┌──────────┐ ┌──────────┐
│ Market & │ │ Weather, │ │ Agri-    │
│ Fair-    │ │ Storage &│ │ Fintech  │
│ Price    │ │ Logistics│ │ Credit   │
│ Agent    │ │ Agent    │ │ Agent    │
└──────────┘ └──────────┘ └──────────┘
```

1. **Market & Fair-Price Agent:** Scrapes live mandi rates across a 100 km radius (**e-NAM**, **Agmarknet**) and maintains an anonymized **Regional Supply Ledger**. If dozens of local farmers harvest simultaneously, it predicts local market gluts—advising farmers with high-spoilage batches to sell first while helping farmers with fresh, storable crops hold for a few days. For B2B bulk orders, it computes a **Fair Floor Price** (weighing mandi rates, season, stock, and distance) and bundles 4–5 neighboring farmers.
2. **Proactive Weather, Storage & Logistics Agent:** Continuously polls **IMD** and weather APIs every few hours for current and **2-to-5-day future forecasts**. Pushes automated local-language SMS, voice calls, and app alerts tied to stored crops (e.g., 48-hour rain warnings to cover grain, or 3-day sunny windows to sun-dry crops). Models dynamic shelf-life and pools small batches to split shared truck and cold-storage costs.
3. **Agri-Fintech Credit Agent:** Connects with partner banks and FPOs to arrange **Electronic Negotiable Warehouse Receipt (e-NWR)** loans, providing up to **70% upfront cash** against stored produce so farmers can pay workers and clear urgent dues immediately while waiting for peak prices.
4. **Central Coordinator Agent (Farmer-First Decision Engine):** Filters options by immediate cash needs and spoilage countdowns. Before sharing farmer details or committing stock to a B2B bulk buyer, it presents net take-home payouts alongside explicit **forecast uncertainty probabilities**. Execution happens **only after the farmer confirms**.

---

## 📊 End-to-End Real-World Workflow (2,000 kg Onion Harvest)
* **Farmer Voice Input:** *"I harvested 40 bags (2,000 kg) of onions today, and I need ₹12,000 right away to pay my workers."*
* **Parallel Agent Analysis:** Weather Agent detects a **75% chance of heavy rain in 48 hours**. Market, Logistics, and Credit Agents compute three net take-home choices:
  * **Option 1 — Local Mandi Today:** ₹16/kg = **₹32,000 cash today** (zero truck cost; covers ₹12,000 worker pay, but loses ₹10,500+ to middlemen).
  * **Option 2 — Pooled B2B Bulk Deal:** Bundled with 3 neighbors at ₹22/kg gross (₹44,000) minus ₹1,500 shared truck share = **₹42,500 net** paid digitally on pickup tomorrow (**+₹10,500 extra profit**, beats the 48-hour rain safely).
  * **Option 3 — 15-Day Cold Storage + 70% Bank Advance:** Forecast ₹26/kg in 15 days (*80% probability of rise; 20% risk of supply influx*). Gross ₹52,000 minus ₹5,500 transport/storage/interest = **₹46,500 estimated net**, with **₹22,400** (70% of ₹32,000 spot value) credited upfront via e-NWR loan to pay workers immediately.
* **Farmer Final Call:** Farmer replies **"Option 2"**, locking guaranteed extra profit ahead of the storm, and Kisan Kavach automatically dispatches the shared pickup truck.

---

## 🔒 Privacy, Anti-Manipulation & Government Safeguards
* **Zero Personal Surveillance:** Processes only direct opt-in messages and calls made to the official Kisan Kavach helpline; never accesses private chats, contacts, or personal call logs.
* **Two-Stage AI Audit (Zero Routine Burden on Officials):** Cross-checks reported harvest weights against official land records (*e-Crop*) without bothering officials. Unusually large harvest claims require a **live, GPS-tagged field photo/video** (phone gallery uploads blocked), verified via Computer Vision, followed by truck/warehouse weight verification at dispatch.
* **Targeted Officer Escalation & Honest Farmer Appeal:** Local government officials (**AEOs, VAAs, and PPC/PACS staff**) are alerted only when an AI check flags a mismatch. If an honest farmer achieves a genuine bumper yield and the AI mistakenly rejects it, tapping **"Request Officer Verification"** forwards their live field video directly to the village officer for manual approval.

---

## 🛠️ Proposed Technology Stack
* **Multi-Agent Orchestration:** LangGraph / CrewAI + Frontier Reasoning LLMs
* **Voice & Alert Layer:** Bhashini API (Regional STT/TTS), WhatsApp Business Cloud API, Twilio IVR & SMS
* **Computer Vision & Integrity:** Live EXIF/GPS validation & Perceptual Image Hashing (pHash)
* **Public Data & DPI Ecosystem:** e-NAM, Agmarknet, IMD Weather APIs, e-Crop & WDRA (e-NWR) frameworks

> *Note: This proposed technology stack is flexible. During prototype development, if any specific tool or API faces latency, access, or integration constraints, we will adapt and adopt the most reliable, optimal technologies available to ensure seamless field performance for farmers.*

---

## 📚 Official Research & Infrastructure References
* [e-NAM (National Agriculture Market)](https://enam.gov.in)
* [Agmarknet (Directorate of Marketing & Inspection)](https://agmarknet.gov.in)
* [Bhashini (National Language Translation Mission)](https://bhashini.gov.in)
* [WDRA (Warehousing Development and Regulatory Authority — e-NWR)](https://wdra.gov.in)
* [India Meteorological Department (IMD)](https://imd.gov.in)
