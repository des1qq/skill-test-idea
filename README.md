<p align="center">
  <img alt="Business Idea Validator logo" src="assets/logo.png" width="140">
</p>

<h1 align="center">Business Idea Validator</h1>

<p align="center">
  An agent skill that stress-tests a specific business idea with real research instead of generic AI optimism.
</p>

<p align="center">
  <img alt="type" src="https://img.shields.io/badge/type-Agent%20Skill-3f78c2?style=flat-square">
  <img alt="runtime" src="https://img.shields.io/badge/runtime-Qoder%20CLI-e2711d?style=flat-square">
  <img alt="format" src="https://img.shields.io/badge/format-Markdown-336791?style=flat-square&logo=markdown&logoColor=white">
  <img alt="method" src="https://img.shields.io/badge/method-Web%20Research-5e9fe8?style=flat-square&logo=googlechrome&logoColor=white">
  <img alt="output" src="https://img.shields.io/badge/output-Scored%20Report-72bc8f?style=flat-square">
  <img alt="language" src="https://img.shields.io/badge/language-RU%20%2F%20EN-f89939?style=flat-square">
  <img alt="license" src="https://img.shields.io/badge/license-MIT-9d4edd?style=flat-square">
  <img alt="status" src="https://img.shields.io/badge/status-active-2ea44f?style=flat-square">
</p>

---

## Overview

Ask most AI assistants to "evaluate my business idea" and you get a confident,
well-formatted answer that is often half-invented. **Business Idea Validator**
is an agent skill that forces a different workflow: gather the user's real
context, research the market with live web search, keep every claim labeled
by its epistemic status, score the idea against a fixed rubric, and finish
with an unambiguous verdict — not a vague "sounds promising."

## Why it exists

| Problem with generic AI idea evaluation | How this skill addresses it |
| --- | --- |
| Plausible-sounding numbers with no source | Every claim must be tagged as a **Fact**, **Hypothesis**, **Conclusion**, or **Unknown** |
| Evaluates the niche in the abstract, not the user's actual idea/resources | Mandatory intake step collects geography, idea stage, budget/time/team, and monetization preference first |
| Ends in a mushy "this could work" | Final verdict is forced into one of four explicit decisions: launch / adjust / test / abandon |
| No reusable structure, inconsistent reports | Fixed report template and a 7-criterion scoring rubric (1–10) applied every time |

## How it works

1. **Intake** — collects market geography, idea stage, available budget/time/team, and monetization preference before any research starts.
2. **Clarify the idea** — asks 1–2 targeted questions only if the idea itself is too vague to research.
3. **Research** — runs multiple web searches covering the niche, target segments, customer pain points (in the customer's own words), competitors and alternatives, pricing, market trends, entry barriers, acquisition channels, and failure signals.
4. **Classify** — sorts every finding into Fact / Hypothesis / Conclusion / Unknown before scoring.
5. **Score** — rates the idea on 7 criteria (1–10), weighted against the user's own resources, not the market in the abstract.
6. **Report** — produces a structured Markdown report: strengths, weaknesses, key hypotheses, a competitive alternatives table, a scorecard, concrete validation steps, and a verdict.
7. **Verdict** — always one of: launch, adjust, test, or abandon — justified by the scores and risks, never a plain good/bad judgment.

## Scoring rubric

| Criterion | What it measures |
| --- | --- |
| Problem strength | How painful and urgent the problem actually is |
| Audience ability to pay | Whether the target segment already spends money on adjacent solutions |
| Competition | Density and strength of existing alternatives |
| Access to first customers | How findable and reachable the first paying users are |
| Implementation complexity | Effort required given the user's own resources and skills |
| Margin potential | Expected profitability and scalability of the pricing model |
| Regulatory / operational risk | Legal, compliance, and operational exposure |

Full scoring guidance: [`references/scoring-rubric.md`](references/scoring-rubric.md).

## Installation

Copy the `business-idea-validator/` folder into a Qoder CLI skills directory:

```bash
# User-level (available in every project)
cp -r business-idea-validator ~/.qoder/skills/

# Project-level (available in this project only)
cp -r business-idea-validator .qoder/skills/
```

Reload skills (`/skills reload`) or restart the session, then confirm it is
listed with `/skills list`.

## Usage

Trigger the skill with a natural request, in Russian or English:

```
Оцени мою бизнес-идею: сервис планирования ремонта квартиры для новостроек в Москве
Проведи исследование ниши для подписочного сервиса доставки корма для кошек
Is there a market for a Chrome extension that tracks subscription renewals?
Validate my business idea: a B2B SaaS for restaurant inventory forecasting
Проверь, стоит ли делать MVP для платформы по поиску фрилансеров-дизайнеров
```

The skill will first ask for missing context (geography, stage, resources,
monetization) if it wasn't included in the request, then research and
produce the full report.

## Report structure

Each report follows a fixed template so results are comparable across ideas:

```
## Оценка идеи: [idea name]

Итог: score X/10, one-line recommendation
Сильные стороны / Слабые стороны
Главные гипотезы
Конкурентные альтернативы (table)
Баллы по критериям (table)
Что проверить первым (numbered action steps)
Вердикт: launch / adjust / test / abandon
```

Full template with a worked example: [`references/report-template.md`](references/report-template.md).

## Repository structure

```
business-idea-validator/
├── SKILL.md                     — skill instructions and workflow (loaded by the agent)
├── assets/
│   └── logo.png
└── references/
    ├── report-template.md       — exact report format + a calibration example
    └── scoring-rubric.md        — 1–10 scoring criteria and interpretation
```

## Limitations

- Report quality depends on the host agent actually performing web search
  before writing conclusions — this skill provides the instructions, not a
  guarantee of search execution.
- Pricing and demand data quality varies by market/geography and by how much
  is publicly indexed online.
- This is a decision-support tool, not financial or legal advice.

## Contributing

Issues and pull requests are welcome — in particular, improvements to the
scoring rubric, the report template, or additional research heuristics for
specific niches.

## License

[MIT](LICENSE)
