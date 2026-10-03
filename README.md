<div align="center">

# 🧠 Agentic AI 360
### Proactive Intervention Desk · Customer 360 Control Room

**An event-driven multi-agent system that turns fragmented customer signals into grounded, explainable and governed interventions.**

<p>
  <img src="https://img.shields.io/badge/Python-3.10%2B-3776AB?logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/Streamlit-Control%20Room-FF4B4B?logo=streamlit&logoColor=white" alt="Streamlit"/>
  <img src="https://img.shields.io/badge/LangChain-Groq%20Integration-1C3C3C?logo=langchain&logoColor=white" alt="LangChain"/>
  <img src="https://img.shields.io/badge/Groq-LLM%20Inference-F55036?logo=groq&logoColor=white" alt="Groq"/>
  <img src="https://img.shields.io/badge/Pydantic-Structured%20Outputs-E92063?logo=pydantic&logoColor=white" alt="Pydantic"/>
  <img src="https://img.shields.io/badge/Architecture-Event--Driven-5B5BD6" alt="Event driven"/>
  <img src="https://img.shields.io/badge/HITL-Approve%20%7C%20Reject%20%7C%20Modify-D97706" alt="HITL"/>
</p>
</div>

---

## 🎬 Product Demo

<video src="VIDEO_ASSET_URL" width="100%" controls muted loop playsinline></video>

https://github.com/user-attachments/assets/6458f296-a285-4a30-9fd1-f77302efccd7

---

## ✦ What is Agentic AI 360?

Agentic AI 360 is an **ambient, event-driven Customer 360 system** rather than a chatbot.

Customer activity arrives as a stream of heterogeneous events — transactions, support interactions, application usage and KYC/compliance signals. Independent specialist agents analyze their own domains, hand structured findings to a shared customer state, and trigger deeper reasoning only when the evidence warrants it.

The system then moves through:

```text
Customer Events
      │
      ▼
┌───────────────────────┐
│ Event Stream + Router │
└───────────┬───────────┘
            ▼
   ┌───────────────────┐
   │ Specialist Swarm  │
   │ Usage · Support   │
   │ Transaction · KYC │
   └─────────┬─────────┘
             ▼
   ┌────────────────────┐
   │ Synthesis /        │
   │ Correlation        │
   └──────────┬─────────┘
              ▼
   ┌────────────────────┐
   │ Life-Event         │
   │ Inference           │
   └──────────┬─────────┘
              ▼
       ┌──────────────┐
       │ Conflict?    │
       └──────┬───────┘
          Yes │   │ No
              ▼   └──────────────┐
      ┌───────────────┐          │
      │ Debate /       │          │
      │ Arbitration    │          │
      └───────┬───────┘          │
              └──────────┬───────┘
                         ▼
                ┌────────────────┐
                │ Decision +     │
                │ Eligibility    │
                └───────┬────────┘
                        ▼
                ┌────────────────┐
                │ 3-Pass Drafting│
                └───────┬────────┘
                        ▼
                ┌────────────────┐
                │ Critique /     │
                │ Compliance     │
                └───────┬────────┘
                        ▼
                ┌────────────────┐
                │ Guardrail      │
                └───────┬────────┘
                        ▼
                ┌────────────────┐
                │ Human Review   │
                │ Approve/Reject │
                │ /Modify        │
                └───────┬────────┘
                        ▼
                  Safe Execution
```

The important design principle is **not “let an LLM decide everything.”**

Instead:

> **LLMs reason where useful; deterministic components constrain, validate, audit and safely complete the workflow.**

---
### Core architecture

| Layer | Responsibility |
|---|---|
| **Event Stream** | Replays heterogeneous customer events with event-time semantics |
| **Trigger Router** | Decides when specialists/checkpoints should run |
| **Specialist Swarm** | Usage, Support/Sentiment, Transaction/Billing and KYC/Compliance analysis |
| **Customer State Board** | Maintains the current per-customer working state |
| **Synthesis / Correlation** | Converts independent findings into correlated signals |
| **Life-Event Agent** | Infers the current customer state with evidence and confidence |
| **Debate / Arbitration** | Makes disagreement explicit instead of hiding conflicting evidence |
| **Decision / Eligibility** | Selects a bounded action vocabulary under policy constraints |
| **Round-Robin Drafting** | Produces multiple customer-facing drafts through sequential refinement |
| **Critique / Refiner** | Reviews drafts from multiple compliance perspectives |
| **Guardrail** | Deterministic final safety boundary |
| **HITL** | Human approval checkpoint before customer-facing execution |
| **Execution Adapter** | Simulates safe downstream execution after clearance |
| **Trace / Evaluation** | Records reasoning, handoffs, actions, HITL and benchmark results |

---

## 🤖 Agentic Workflow

### 1. Specialist Swarm

Each specialist has a bounded responsibility and data boundary.

| Agent | Reads | Produces |
|---|---|---|
| 🔵 **Usage Agent** | Web/app activity | Engagement and usage signals |
| 🟣 **Support Agent** | Support interactions | Sentiment / support signals |
| 🟢 **Transaction Agent** | Transaction/billing events | Financial and anomaly signals |
| 🟠 **KYC / Compliance Agent** | KYC + policy | Compliance / verification signals |

Specialists do **not** directly produce customer-facing actions.

They produce structured findings that are handed to synthesis.

---

### 2. Synthesis & Correlation

The synthesis layer combines independent findings into correlated signals such as:

```text
Digital engagement activity
            +
Financial activity change
            +
Temporal context
            ↓
     Correlated signal
            ↓
    Life-event inference
```

This prevents a single isolated event from automatically becoming an intervention.

---

### 3. Life-Event Inference

The Life-Event stage produces a structured state:

```text
Inferred State
Confidence
Confidence Band
Evidence
Rationale
Supporting Signals
```

Example states include:

```text
no_significant_event
financial_distress_general
churn_risk
medical_hardship
potential_fraud_or_takeover
```

Provider reasoning can be used here, but deterministic evidence-floor logic remains available as a safety/resilience layer.

---

## ⚔️ Explicit Agent Debate

One of the key design goals is that **disagreement is visible**.

When specialists materially disagree, the system does not simply average their outputs.

Instead it creates two contrasting perspectives:

```text
┌──────────────────────────────┐
│ Perspective A                │
│ Evidence / argument          │
│ Supporting signals           │
│ Counterpoints                │
└──────────────┬───────────────┘
               │
               │  DEBATE
               │
┌──────────────▼───────────────┐
│ Perspective B                │
│ Evidence / argument          │
│ Supporting signals           │
│ Counterpoints                │
└──────────────┬───────────────┘
               ▼
       Arbitration / Outcome
```

The Control Room exposes:

- the conflicting agents
- each agent's position
- evidence supporting each position
- arguments
- counterarguments
- points of agreement
- points of disagreement
- unresolved uncertainty
- final arbitration outcome

This makes the debate inspectable instead of turning it into an invisible LLM call.

---

## ✍️ Round-Robin Drafting

When a customer-facing intervention is proposed, the system does not immediately send the first generated message.

It uses a three-pass refinement loop:

```text
Pass 1
Customer Support Agent
        ↓
Pass 2
Relationship Manager Agent
        ↓
Pass 3
Customer Experience Agent
        ↓
Critique / Compliance Review
        ↓
Guardrail
        ↓
HITL
```

Each pass has a distinct perspective, while the final message remains bounded by the approved action and evidence.

---

## 🛡️ Guardrails & Governance

The final customer-facing boundary is deterministic.

The system checks for:

- unsupported claims
- risky personalization
- compliance-sensitive language
- unsafe or overconfident statements
- action eligibility
- human-review requirements
- hard-stop conditions

The guardrail can:

```text
ALLOW
  │
  ├──→ safe continuation
  │
REQUIRE HUMAN REVIEW
  │
  └──→ HITL
       ├── Approve
       ├── Reject
       └── Modify

BLOCK
  │
  └──→ hard-stop queue
```

The architecture intentionally separates **reasoning** from **authorization**.

---

## 👤 Human-in-the-Loop

HITL is a real execution boundary, not a decorative UI element.

For a review-required action, the operator can inspect:

- customer state
- evidence
- selected action
- action subtype
- eligibility
- guardrail result
- proposed message
- debate/arbitration context
- compliance critique

Then:

```text
[A] APPROVE
[R] REJECT
[M] MODIFY
```

Only after the appropriate clearance does the simulated execution adapter proceed.

---

## 🧠 Memory Architecture

Agentic AI 360 uses three distinct memory layers:

### Working Memory

Current `CustomerState`.

Used for the immediate customer context and current checkpoint.

### Episodic Memory

Historical customer-specific interventions and inferred states.

Used to answer:

> “What has happened with this customer before?”

### Semantic Memory

Shared policy and domain definitions.

Used to answer:

> “What does this policy or state definition mean?”

This separation prevents historical customer events from being confused with shared policy knowledge.

---

## 🖥️ Control Room

The Streamlit interface is designed as an operator console rather than a chatbot.

### Overview

Shows the current operational picture:

- customer profile
- current inferred state
- action
- run health
- checkpoint count
- provider usage
- pipeline state
- evaluation status

### Agent Reasoning

Shows the deeper reasoning chain:

```text
Specialists
   ↓
Synthesis
   ↓
Life Event
   ↓
Conflict
   ↓
Debate
   ↓
Arbitration
```

### Decision & HITL

Shows:

- selected action
- eligibility
- guardrail
- proposed intervention
- approval state
- human controls

### Drafting & Compliance

Shows all three draft passes and reviewer decisions.

### Customer Context

Shows grounding evidence and memory layers.

### Observability

Shows runtime trace, evaluation and audit information.

---

## 📊 Evaluation

The project includes a scenario-level evaluation harness covering:

- state accuracy
- action accuracy
- action subtype accuracy
- HITL accuracy
- confidence-band accuracy
- complete checkpoint accuracy
- action false-positive rate
- action false-negative rate
- red-herring handling

For the hardened Scenario 03 replay, the validated benchmark reached:

| Metric | Result |
|---|---:|
| State accuracy | **1.00** |
| Action accuracy | **1.00** |
| Subtype accuracy | **1.00** |
| HITL accuracy | **1.00** |
| Confidence-band accuracy | **1.00** |
| Complete checkpoint accuracy | **1.00** |
| Action false-positive rate | **0.00** |
| Action false-negative rate | **0.00** |
| Red-herring check | **PASS** |

> These are replay/evaluation results for the supplied scenario package, not a claim of production accuracy.

---

## ⚡ Provider & Quota Safety

Groq is used for bounded reasoning stages.

Default provider-enabled stages:

```text
life_event
debate
draft
critique
```

The system has hard runtime ceilings:

```text
Provider attempts / run       ≤ 12
Prompt-token ceiling / run   ≤ 24,000
Output tokens / provider call ≤ 800
```

The provider path is deliberately **not a single point of failure**.

If a provider call:

- fails
- times out
- returns empty output
- returns malformed structured output
- hits a quota
- reaches the process-local cap

the pipeline can fall back to deterministic logic and continue safely.

This makes the project usable under constrained/free API tiers while retaining live provider reasoning when available.

---

## 🔎 Traceability

Every important stage is designed to leave structured artifacts.

```text
outputs/
├── scenario_03_traces/
│   └── *.jsonl
├── scenario_03_inferred_events.jsonl
├── scenario_03_evaluation.json
├── scenario_03_hitl_audit.jsonl
└── scenario_03_hard_stop_queue.jsonl
```

These artifacts allow a reviewer to inspect:

- agent execution
- tool activity
- evidence
- handoffs
- inference
- debate
- drafting
- critique
- guardrail decisions
- HITL
- execution
- evaluation

---

## 🚀 Quick Start

### 1. Clone

```bash
git clone <https://github.com/newtonspaxe-source/final-Endterm-Atharva-Pandey>
cd <final-Endterm-Atharva-Pandey>
```

### 2. Create a virtual environment

#### Windows PowerShell

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

#### Linux / macOS

```bash
python -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
pip install -r requirements.txt
```

### 4. Configure Groq

Copy:

```text
api.env.example
```

to:

```text
api.env
```

Then add:

```env
GROQ_API_KEY=your_key_here
```


## ▶️ Run the Pipeline

### Full scenario replay

```powershell
python .\main.py --scenario scenario_03
```

### Streamlit Control Room

```powershell
streamlit run .\app.py
```

## 🧩 Technology Stack

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.10%2B-3776AB?style=for-the-badge&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/Streamlit-Control%20Room-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white" alt="Streamlit"/>
  <img src="https://img.shields.io/badge/LangChain-Agent%20Workflow-1C3C3C?style=for-the-badge&logo=langchain&logoColor=white" alt="LangChain"/>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Groq-LLM%20Inference-F55036?style=for-the-badge&logo=groq&logoColor=white" alt="Groq"/>
  <img src="https://img.shields.io/badge/Pydantic-Validation-E92063?style=for-the-badge&logo=pydantic&logoColor=white" alt="Pydantic"/>
  <img src="https://img.shields.io/badge/Git-Version%20Control-F05032?style=for-the-badge&logo=git&logoColor=white" alt="Git"/>
  <img src="https://img.shields.io/badge/GitHub-Repository-181717?style=for-the-badge&logo=github&logoColor=white" alt="GitHub"/>
</p>

| Technology       | Used For                                                       |
| ---------------- | -------------------------------------------------------------- |
| **Python 3.10+** | Core runtime, event processing and agent orchestration         |
| **Streamlit**    | Customer 360 Control Room and operator interface               |
| **LangChain**    | LLM integration, structured workflows and provider abstraction |
| **Groq**         | Bounded live LLM inference for reasoning stages                |
| **Pydantic**     | Typed schemas, validation and structured outputs               |
| **JSON / JSONL** | Events, memory, traces, audits and evaluation artifacts        |
| **Git + GitHub** | Version control and project delivery                           |

> **Architecture note:** The project deliberately combines LLM reasoning with deterministic state, evidence, policy and safety layers. LangGraph is **not** a runtime dependency of the current implementation.


## 🔐 Security & Data Boundaries

The repository is designed as a simulation/replay environment.

- No real customer API integration is included.
- No real `api.env` or secret is committed.
- Customer data access is scoped by specialist responsibility.
- PII is redacted at relevant prompt/trace/audit boundaries.
- Customer-facing side effects are blocked behind guardrails and HITL.
- `ground_truth.json` is evaluation data and is not used as an inference source.

---

## 🎯 Design Principles

### 01 · Evidence before intervention

An isolated event should not automatically create a customer-facing action.

### 02 · Disagreement should be visible

When agents disagree, expose the disagreement and its evidence instead of hiding it behind a single answer.

### 03 · LLMs are reasoning components, not authorization layers

Provider output is validated and constrained by deterministic policy.

### 04 · Human approval is a real boundary

Sensitive customer-facing interventions can require explicit human clearance.

### 05 · Every decision should be traceable

A reviewer should be able to move backwards from:

```text
Execution
   ↓
HITL
   ↓
Guardrail
   ↓
Draft
   ↓
Decision
   ↓
Life Event
   ↓
Correlated Evidence
   ↓
Specialist Findings
   ↓
Customer Events
```

### 06 · Provider failure should not destroy the pipeline

The architecture is designed to remain executable under quota pressure or provider failure.

---


## 📌 Project Status

**Status: Hardened demo/research prototype**

The project is designed to demonstrate:

- event-driven multi-agent coordination
- customer state reconstruction
- structured agent handoffs
- conditional debate
- multi-pass communication drafting
- compliance critique
- deterministic safety boundaries
- human-in-the-loop intervention
- memory
- traceability
- evaluation
- bounded live LLM usage

It is not presented as a production banking system or as a substitute for real compliance, risk, or customer-service infrastructure.

---

<div align="center">

### Built as an explainable Agentic AI 360 control plane

**Events → Evidence → Reasoning → Debate → Decision → Guardrail → Human → Action**

</div>
