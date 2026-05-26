# Groundwork

**An honest AI readiness diagnostic for banks and large enterprises.**

Groundwork is a structured assessment tool that helps organisations understand how ready they actually are for AI transformation — not how ready they want to be. It asks 30 questions across eight dimensions, then uses an LLM to synthesise the answers into a specific, sequenced readiness profile.

Built as a companion to research into AI transformation in real organisations.

→ **[Live tool](https://vashishthask.github.io/ai-groundwork/)**

---

## What it does

You enter an organisation name, work through 30 questions across eight dimensions, then choose an AI provider and model to synthesise the results. The output is a readiness profile that includes:

- **Primary constraint** — the single most important blocker, named before anything else
- **Dimension profiles** — maturity rating and specific finding for each dimension
- **Recommended sequence** — step 1, step 2, step 3. Never a flat list
- **Problem-readiness gap** — honest assessment of whether current readiness matches the stated ambition
- **Questions they should be asking** — grounded in their specific answers
- **Red flags** — explicit blockers, not softened as opportunities
- **Assessor's note** — two sentences of candid summary

---

## The eight dimensions

| # | Dimension | What it surfaces |
|---|-----------|-----------------|
| 0 | Intent & Problem Framing | Whether the organisation is problem-led or technology-led |
| 1 | Data Readiness | Whether data is accessible, trusted, and owned |
| 1b | Knowledge Accessibility | Whether domain knowledge is in a state AI tools can reach |
| 2 | Process Clarity | Whether the organisation understands its own work well enough |
| 3 | Governance & Risk | Whether accountability, regulation, and failure culture are real |
| 4 | Organisational Readiness | Whether culture and structure match the AI ambition |
| 5 | Skills & Knowledge | Whether the organisation has the judgment to use AI well |
| 6 | Ambition vs Capacity | Whether appetite is matched by realistic capacity |

---

## What makes it different

Most AI readiness frameworks are either too generic (a 5-point Likert scale across vague dimensions) or too technical (focused on MLOps maturity, not organisational reality). Groundwork is built around a different analytical frame:

**Constraint-first** — the output leads with the binding constraint, not a technology recommendation. You cannot identify what to fix until you know what is actually blocking progress.

**Value stream thinking** — questions trace problems to where work flows and stalls, not where it is theoretically supposed to go.

**Organisational dynamics as first-class variables** — culture, politics, capacity, and failure handling are treated as real constraints, not soft factors.

**Specific, not generic** — the synthesis prompt contains a rule that no sentence in the output should apply equally to every organisation. If a finding could appear in any readiness report without changing a word, it is rewritten.

---

## Analytical lens

The synthesis prompt was designed around three principles drawn from enterprise transformation practice:

1. **Find the binding constraint first.** Adapted from Theory of Constraints — the constraint that, if resolved, unlocks progress on everything else. Addressing any other problem first is waste.

2. **Distinguish documented process from actual process.** Organisations frequently have process documentation that describes intended behaviour, not real behaviour. The questions are designed to surface that gap.

3. **Treat governance and failure culture as predictors of AI success.** How an organisation handles failure today predicts how it will handle AI errors tomorrow. This is often a more accurate readiness signal than data maturity or technical infrastructure.

---

## Supported AI providers

Groundwork works with three providers. You bring your own API key — it is used only to call the synthesis API and is never stored on any server.

| Provider | Recommended model | Notes |
|----------|------------------|-------|
| **Groq** | llama-3.3-70b-versatile | Fast, free tier available at [console.groq.com](https://console.groq.com) |
| **OpenAI** | gpt-4o | Strong reasoning, higher cost |
| **Anthropic** | claude-sonnet-4-20250514 | Strong analytical output |

API keys can optionally be saved to browser localStorage using the "Remember on this device" checkbox on the generate screen.

---

## How to use it

### As a self-assessment
Open the tool, enter your organisation name, work through all eight dimensions, select your provider and model, enter your API key, and generate.

### As a facilitated workshop tool
Run the assessment as a 30-minute facilitated conversation. Work through the questions verbally with a leadership team — a CIO, transformation lead, or delivery manager. Enter answers on their behalf. The free-text questions (Q0a, Q5, Q6, Q22, Q23) typically produce the most useful signal when answered out loud rather than typed.

### As a research instrument
The question set was designed to surface patterns across organisations. Running it with multiple organisations and comparing dimension profiles reveals systemic constraints — not just individual organisational gaps. Free-text answers to Q22 ("what would have to stop") and Q23 ("what success looks like") are particularly useful as research material.

---

## Running it locally

No build step, no dependencies. Just a single HTML file.

```bash
git clone https://github.com/vashishthask/ai-groundwork.git
cd ai-groundwork
open index.html
```

Or serve it locally:

```bash
python3 -m http.server 8000
# then open http://localhost:8000
```

---

## Deploying your own instance

1. Fork this repository
2. Go to Settings → Pages
3. Source: Deploy from a branch → main → / (root)
4. Save

Your instance will be live at `https://[your-username].github.io/ai-groundwork/`

---

## The synthesis prompt

The analytical logic lives in the synthesis prompt embedded in `index.html`. Key rules:

- Every finding must trace to a specific answer — no claims that cannot be grounded in the input
- Lead with the primary constraint before anything else
- When naming a risk, state the specific consequence for this organisation — not the category
- Sequence recommendations (step 1 → step 2 → step 3) — never a flat list
- No sentence should apply equally to every organisation

The prompt was developed and iterated through a series of test runs against a simulated bank profile (MidlandFirst Bank), with specific attention to the difference between generic findings ("partial approval process is a risk") and specific findings ("partial approval process means a mortgage AI tool could reach production without model risk sign-off, which is a PRA SS1/23 breach").

---

## Project context

Groundwork was built as part of a learning-by-doing approach to understanding AI in enterprise settings — specifically how AI tools perform when applied to the kinds of messy, politically complex, constraint-laden situations that characterise real organisations rather than demos.

It is a companion to ongoing research and writing on AI transformation in banks and large enterprises, with a focus on:

- Where AI actually helps vs where it looks useful
- How organisational constraints shape AI adoption more than technology constraints
- What "readiness" means in practice vs in frameworks
- Why AI tends to help people who already have domain skill more than those who don't

---

## Feedback and contributions

If you run this with a real organisation and the output surprises you — either because it was more accurate or less accurate than expected — that is useful signal. Open an issue with the dimension that surprised you and what you expected instead.

Pull requests welcome for question improvements, additional providers, or output format changes.

---

## Licence

MIT — use freely, including commercially. Attribution appreciated but not required.
