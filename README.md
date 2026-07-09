# Agentic Customer Support Triage System
### Built with Flowise Agentflow | Multi-Agent Orchestration | Intelligent Routing

A working agentic AI workflow that automates customer support ticket classification, routing, and response generation — without human intervention at each step.

Built to demonstrate how real business workflows can be designed using multi-agent orchestration, structured LLM output, conditional routing logic, and flow state management.

---

## What It Does

A customer submits a support request. The system:

1. **Classifies** the issue using an Intake Agent (extracts issue type, department, risk level, and a structured summary)
2. **Routes** the case automatically based on classification — billing issues go one way, technical issues go another
3. **Generates** a professional, context-aware response using a specialist agent
4. **Delivers** the final reply back to the customer via Direct Reply

No single chatbot doing everything. Each agent has a defined role, a defined output format, and a defined scope — which is what makes it *agentic*.

---

## Flow Architecture

```
Customer Message (Chat Input)
        ↓
  [ Intake Agent ]
  Extracts: issue_type, department, risk_level,
            short_summary, draft_reply (JSON)
        ↓
  [ Condition Node ]
  IF issue_type = "billing"  →  [ Billing Agent ]
  ELSE                       →  [ Tech Agent ]
        ↓
  [ Direct Reply ]
  Returns professional response to customer
```

---

## Agent Roles

| Agent / Node | Responsibility |
|---|---|
| **Start / Chat Input** | Entry point — captures the raw customer message |
| **Intake Agent** | Reads the message and extracts structured business data in JSON format |
| **Condition Node** | Routes the flow based on `issue_type` from flow state |
| **Billing Agent** | Generates professional responses for billing, refund, and payment issues |
| **Tech Agent** | Generates professional responses for login, access, and technical issues |
| **Direct Reply** | Returns the final response — reads from flow state, does not generate |

---

## Key Technical Concepts Demonstrated

**Multi-agent orchestration**
Each agent is scoped to a single responsibility. The workflow chains them in sequence rather than relying on one model to do everything — improving consistency and making the system easier to debug and extend.

**Structured JSON output from LLM**
The Intake Agent is prompted to return a strict JSON schema every time:
```json
{
  "issue_type": "billing",
  "department": "billing",
  "risk_level": "medium",
  "short_summary": "Customer charged twice, requesting refund",
  "draft_reply": "Thank you for reaching out..."
}
```
Low temperature (0.1–0.3) enforces consistency. Downstream nodes read these values from flow state.

**Flow state management**
Values extracted by the Intake Agent are stored in shared flow state and referenced by subsequent nodes using `{{ $flow.state.issue_type }}`. This is the mechanism that enables conditional routing and final reply delivery without passing data manually between nodes.

**Conditional routing logic**
The Condition Node evaluates `{{ $flow.state.issue_type }}` against a string value. Matched cases (billing) take one path; all other cases take the else branch. The architecture is designed to extend — adding a Shipping Agent or FAQ Agent requires only a new branch and a new condition.

**Prompt engineering for specialist agents**
Each specialist agent has a focused system prompt with explicit constraints: no invented facts, no placeholder text, consistent sign-off format. This keeps outputs professional and predictable across different customer inputs.

---

## Business Use Case

**Industry:** Customer Service / Operations Automation

**Problem:** Manual support ticket triage is slow, inconsistent, and doesn't scale. Support staff spend time reading and routing tickets that could be classified automatically.

**Solution:** An agentic workflow that classifies every incoming request in milliseconds, routes it to the right specialist path, and generates a professional first response — ready to send or reviewed by a human before sending.

**Measurable outcomes this architecture enables:**
- Reduced average triage time from minutes to seconds
- Consistent response tone and format across all ticket types
- Clear audit trail — flow state captures classification metadata for every interaction
- Easily extensible — new issue types require only a new branch and agent

---

## Tech Stack

| Tool | Purpose |
|---|---|
| **Flowise** | Visual agentic workflow builder and orchestration platform |
| **Flowise Agentflow** | Multi-agent canvas with flow state and conditional routing |
| **LLM (via Flowise)** | Underlying language model for each agent node |
| **Condition Node** | Boolean routing logic based on flow state values |
| **Direct Reply Node** | Terminal output node — returns flow state value to user |

---

## How to Run This Locally

**Prerequisites:**
- Node.js v18+
- Flowise installed (`npm install -g flowise`)

**Steps:**

```bash
# Start Flowise
npx flowise start

# Open in browser
http://localhost:3000
```

1. Go to **Agentflows** → **Add New**
2. Build the flow following the architecture diagram above
3. Add each node in order: Start → Intake Agent → Condition → Billing Agent / Tech Agent → Direct Reply
4. Configure system prompts for each agent (see Agent Roles section)
5. Set up flow state variables in the Start node
6. Configure Update Flow State mappings in the Intake Agent

---

## Test Inputs

**Billing route:**
> "I was charged twice for my order and need help getting a refund."

Expected: Intake Agent classifies `issue_type = billing` → Condition routes to Billing Agent → professional billing response returned

**Technical route:**
> "My account is locked and I cannot log in to the application."

Expected: Intake Agent classifies `issue_type = technical` → Condition routes to Tech Agent → professional technical support response returned

---

## Planned Extensions

- [ ] Add Shipping Agent as a third routing branch
- [ ] Add Review Agent before Direct Reply for high-risk cases
- [ ] Connect to a knowledge base (RAG) so agents reference actual product documentation
- [ ] Add human-in-the-loop approval step for `risk_level = high` cases
- [ ] Integrate with a ticketing API (Zendesk, ServiceNow) to log classified tickets automatically

---

## About This Project

Built as part of independent AI automation development work alongside a Master of Professional Studies in Analytics (Northeastern University, Graduated March 2026).

This project demonstrates practical agentic AI design applied to a real enterprise use case — customer support operations — using visual orchestration tools accessible to both technical and non-technical teams.

**Author:** Nathaniel Akwei Brown
**Portfolio:** [nabrownportfolio.online](https://www.nabrownportfolio.online)
**LinkedIn:** [linkedin.com/in/nathaniel-akwei-brown](https://linkedin.com/in/nathaniel-akwei-brown)
**GitHub:** [github.com/NiiBrown](https://github.com/NiiBrown)
