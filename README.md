# Business Model Canvas AI Agent
### Built with Flowise | LLM-Powered Business Strategy Tool | Prompt Engineering

An AI agent that transforms a raw business idea into a complete strategic framework in seconds — including a full Business Model Canvas, investor pitch, risk analysis, and 30-day validation plan.

Built to demonstrate practical prompt engineering, structured LLM output design, and agentic AI applied to a real business use case.

---

## What It Does

You give it a business idea. It gives you back four things immediately:

1. **Business Model Canvas** — all 9 sections filled out (Customer Segments, Value Propositions, Channels, Customer Relationships, Revenue Streams, Key Resources, Key Activities, Key Partnerships, Cost Structure)
2. **60-second investor pitch** — concise, professional, ready to use
3. **Top 5 assumptions and risks** — each with a short mitigation strategy
4. **30-day validation plan** — concrete steps to test the idea before investing further

No back-and-forth. No clarifying questions. One input, four structured outputs.

---

## Example

**Input:**
> "A mobile app that connects local farmers directly with urban consumers for weekly fresh produce delivery."

**Output:**
```
BUSINESS MODEL CANVAS
─────────────────────
Customer Segments:
  - Urban households aged 25–45 who value fresh, locally sourced food
  - Health-conscious consumers willing to pay a premium
  - Local farmers with excess produce and no direct sales channel

Value Propositions:
  - Farm-to-door freshness with full traceability
  - Fair pricing for farmers, lower markup for consumers
  - Convenient weekly subscription with flexible box customization

Channels:
  - Mobile app (iOS and Android)
  - Social media and community groups
  - Local farmers market presence for awareness

Customer Relationships:
  - Subscription model with personalised box preferences
  - Community newsletters and farm story features
  - Responsive in-app support

Revenue Streams:
  - Weekly subscription fees from consumers
  - Small transaction fee per order from farmer payouts
  - Premium tier for organic and specialty produce

Key Resources:
  - Mobile app platform
  - Network of verified local farmers
  - Logistics and cold-chain delivery partners

Key Activities:
  - Farmer onboarding and quality verification
  - Order management and delivery coordination
  - App maintenance and customer support

Key Partnerships:
  - Local farms and agricultural co-operatives
  - Last-mile delivery services
  - Payment processing providers

Cost Structure:
  - App development and maintenance
  - Delivery and logistics costs
  - Farmer acquisition and support
  - Marketing and community building

─────────────────────
60-SECOND INVESTOR PITCH
─────────────────────
Consumers want fresh, local food but can't access it easily.
Farmers have great produce but no direct sales channel.
We connect them.

Our app lets urban households subscribe to weekly fresh produce boxes
sourced directly from verified local farms — no supermarket markup,
no supply chain mystery.

We make money on subscriptions and a small transaction fee per order.
Farmers earn more. Consumers pay less than premium grocery. Everyone wins.

We're targeting a $4B local food market growing at 12% annually.
We need $250K to launch in two cities, sign 50 farmers, and reach
1,000 subscribers in 90 days.

─────────────────────
TOP 5 ASSUMPTIONS AND RISKS
─────────────────────
1. Assumption: Urban consumers will pay a premium for local produce
   Risk: Price sensitivity may reduce conversion
   Mitigation: Offer a trial box at cost to demonstrate value before subscription

2. Assumption: Local farmers can meet consistent weekly volume
   Risk: Seasonal shortages disrupt supply
   Mitigation: Partner with 3–5 farms per region to diversify supply

3. Assumption: Last-mile delivery is cost-effective at small scale
   Risk: Delivery costs eat into margins early
   Mitigation: Start with fixed weekly delivery days per zone to batch routes

4. Assumption: Consumers will stay subscribed beyond the first month
   Risk: High early churn
   Mitigation: Build in box customization and farm storytelling to increase engagement

5. Assumption: Farmers are willing to commit to weekly volume commitments
   Risk: Farmers prefer spot sales over forward commitments
   Mitigation: Offer flexible commitment tiers — guaranteed minimum with optional surplus

─────────────────────
30-DAY VALIDATION PLAN
─────────────────────
Week 1: Customer discovery — interview 20 target consumers about produce buying habits and willingness to pay
Week 2: Farmer outreach — approach 10 local farms, assess volume capacity and interest in direct sales channel
Week 3: Manual MVP — run one delivery cycle manually (no app) with 10 households and 2 farms to test logistics
Week 4: Measure and decide — track order completion rate, customer satisfaction, and farmer reliability; decide whether to build the app
```

---

## How It Works

The agent uses a single, carefully engineered system prompt that:

- Accepts any business idea as free-form text input
- Suppresses clarifying questions — it works with whatever information is given
- Structures output into four distinct, professionally formatted sections
- Maintains consistent tone and depth regardless of idea complexity

**Core prompt design principles applied:**
- **Role assignment** — the agent is told explicitly what it is and what it must produce
- **Output schema enforcement** — the 9 BMC sections are enumerated to ensure none are skipped
- **Constraint setting** — no clarifying questions, no filler, structured and professional output only
- **Multi-output generation** — four different deliverable types from one prompt without chaining

---

## Tech Stack

| Tool | Purpose |
|---|---|
| **Flowise** | Visual agent builder and orchestration platform |
| **LLM Node** | Language model that processes the prompt and generates structured output |
| **Prompt Template** | Engineered system prompt with `{idea}` variable injection |
| **Chat Interface** | Flowise built-in chat for testing and demo |

---

## How to Run This Locally

**Prerequisites:**
- Node.js v18+
- Flowise installed

```bash
# Install Flowise
npm install -g flowise

# Start Flowise
npx flowise start

# Open in browser
http://localhost:3000
```

**Setup:**
1. Go to **Chatflows** → **Add New**
2. Add an **LLM Node** to the canvas
3. Connect a **Chat Input** node → LLM Node → **Chat Output** node
4. In the LLM Node, add a **Prompt Template** with the system prompt below
5. Set the input variable to `{idea}`
6. Save and open the chat interface to test

**Import the flow directly:**
Download [`bmc_agent_flow.json`](./bmc_agent_flow.json) and import it 
into Flowise via **Chatflows → Import** to get the full working flow instantly.

**System Prompt:**
```
You are a Business Model Canvas Agent.
Input business idea: {idea}

Do not ask for any clarifying questions if any key info is missing.

Generate:
1) Business Model Canvas with 9 sections:
   - Customer Segments, Value Propositions, Channels,
     Customer Relationships, Revenue Streams, Key Resources,
     Key Activities, Key Partnerships, Cost Structure
2) A 60-second investor pitch
3) Top 5 assumptions/risks with short mitigations
4) A 30-day validation plan

Keep output clear, structured, and professional.
```

---

## Screenshots

- canvas_overview.png
- prompt_config.png
- live_output1.png
- live_output2.png
- live_output3.png
- live_output4.png

---

## Why This Is Useful

Early-stage founders, product managers, and analysts spend hours producing the kind of structured thinking this agent generates in seconds. It's not a replacement for deep strategy work — it's a starting point that removes the blank-page problem and surfaces assumptions worth testing immediately.

**Potential extensions:**
- [ ] Add a RAG layer connected to industry reports so outputs are market-specific
- [ ] Add a second agent that critiques the BMC and identifies weak sections
- [ ] Connect to a document export tool to produce a formatted PDF output
- [ ] Build a multi-turn version that lets users refine individual sections

---

## About This Project

Built as part of independent AI automation and agentic workflow development work, alongside a Master of Professional Studies in Analytics (Northeastern University, Graduated March 2026).

This project demonstrates applied prompt engineering, structured LLM output design, and practical agentic AI development using visual orchestration tools.

**Author:** Nathaniel Akwei Brown
**Portfolio:** [nabrownportfolio.online](https://www.nabrownportfolio.online)
**LinkedIn:** [linkedin.com/in/nathaniel-akwei-brown](https://linkedin.com/in/nathaniel-akwei-brown)
**GitHub:** [github.com/NiiBrown](https://github.com/NiiBrown)
