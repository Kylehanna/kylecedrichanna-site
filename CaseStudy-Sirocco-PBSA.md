# Case Study — Building an In-House Due Diligence & Market Analysis Engine for a Real Estate Investment Team

**Asset class:** Purpose-Built Student Accommodation (PBSA)
**Engagement type:** Custom analytics build for a former client
**System:** Sirocco — Real Estate Investment Intelligence Platform
**Role:** Sole architect and builder (data pipeline, models, agent layer, application)

---

## The headline

A real estate investment team wanted its own analysts to move earlier and diligence deals faster — without outsourcing judgment to a black-box vendor. I designed and built the system that did it: a predictive engine that forecasts housing demand from labor-market leading indicators, wrapped in an analyst-facing workflow that turns model output into underwriting memos, market briefings, and risk flags. The PBSA book was the proving ground. Sirocco is the expanded, climate-aware version of that build.

---

## The context — the problem I was solving

The client was a real estate investment team that ran diligence the way most mid-market shops do: fragmented tools, institutional memory, and analyst hours. Deal screening lived in spreadsheets. Market conviction lived in people's heads. Predictive insight, where it existed at all, sat disconnected from the day-to-day workflow.

Their objective was not "buy a data subscription." It was **to enhance their internal staff's capabilities around due diligence and market analysis** — to give their own analysts a repeatable, defensible, model-grounded way to answer the two questions that drive every deal:

1. *Where is demand building before the market has priced it in?*
2. *Does this specific deal survive diligence once we pressure-test it?*

We anchored the build on **Purpose-Built Student Accommodation (PBSA)** — an asset class where demand is unusually legible if you know where to look. PBSA absorption is driven by enrollment trends, the employment gravity of a university-and-health anchor, and in-migration into the metro. Those are exactly the kinds of signals that show up in labor and migration data *before* they show up in permits, rents, or broker comps. It was the right asset class to prove that leading indicators beat lagging ones.

---

## What I built — Sirocco

Sirocco is a quantitative research platform that forecasts residential and student-housing demand across **926 U.S. metro markets (CBSAs)** and then puts that forecast directly into the hands of the analysts doing the diligence.

The core thesis is simple and testable: **labor markets lead housing markets by roughly two to six quarters.** Where employment is tightening, where in-migration is accelerating, and where an area's economic anchor is strengthening, housing demand — including student housing — builds before supply responds. Model that lead time and you can point capital at markets before they clear.

It was built to function like a Bloomberg Terminal for a real estate investment team: one place where market signal, deal underwriting, and risk all live together.

---

## How it works — the mechanism

Sirocco has two layers.

### 1. The predictive core

The forecasting engine models building-permit activity — the cleanest available proxy for where housing supply is about to be needed — as a function of employment dynamics.

- **Data foundation:** BLS Quarterly Census of Employment and Wages (926 CBSAs, 2,340 industries, 2019–2025), U.S. Census Building Permit Survey, IRS county-to-county migration flows, and ACS demographics.
- **Feature engineering:** roughly 150 employment-derived signals grounded in Shimer (2005) labor-market matching theory — labor-market tightness, matching efficiency, Beveridge-curve position, employment hysteresis, and a cross-industry skill-mismatch index, each computed across multiple quarterly lags.
- **Model:** gradient-boosted trees (XGBoost) predicting log-permit activity per market, trained on 2022–2023 and validated on a **2024–2025 holdout** across 474 markets with matched employment and permit data.
- **Output:** for any of the 926 metros, an analyst gets employment momentum, labor tightness, a next-quarter demand forecast, actual-vs-predicted permit tracking, and a market opportunity ranking.

For the PBSA question specifically, this is the difference between "we think this university town is growing" and "the labor and migration signals underneath this market point to student-housing undersupply, and here's the forecast that says so."

### 2. The analyst workflow layer

A forecast is only useful if it changes what an analyst does on a Tuesday. So the second layer turns model output plus deal inputs into finished analytical work — the part that directly upgrades internal staff capability:

- **Market Intelligence** — answers executive-level questions on valuation support, supply risk, and migration risk for any market, with the evidence attached.
- **Investment Memo** — turns market signal and deal terms into an underwriting-style memo with a clear recommendation (advance, pursue with guardrails, or hold for diligence).
- **Underwriting** — scores the deal itself: stabilized NOI, DSCR, debt yield, equity multiple, and exit value, adjusted by the market's demand and risk signals.
- **Scenario Simulation** — projects bear / base / bull operating ranges over 12–18 month and 5–10 year horizons.
- **Portfolio Risk** — flags distress, liquidity, cap-rate, and climate exposure across saved deals.
- **Report Generation** — produces IC memos, lender summaries, and investor briefs from the same underlying case.

The point of this layer was never to replace the analysts. It was to make a two-person team diligence like a ten-person one — standardizing the market read, removing the "it depends who you ask" problem, and cutting the time between "interesting market" and "committee-ready memo."

### The climate angle

The risk layer already treats supply-pipeline, demand-volatility, rent-momentum, cap-rate, and downside probability as weighted, quantifiable exposures. That framework is where the climate thesis plugs in directly: physical and transition climate risk are, structurally, just additional demand and supply shocks with a longer horizon — insurability, migration pull-and-push, energy and retrofit cost, and regulatory drag. The same leading-indicator machinery that reads labor-driven demand can read climate-driven demand displacement. That extension is the reason for the rebrand.

---

## What it proves

- **I can take an asset class from raw public data to a working decision system.** Sirocco is an end-to-end build — data ingestion, feature engineering grounded in published labor economics, a validated ML model, and a usable application — not a slide deck.
- **I build for the operator, not the demo.** The system's value is that it changed how a real investment team could screen markets and underwrite deals, in their own workflow, with their own judgment still in charge.
- **I connect quantitative modeling to money decisions.** The through-line runs from BLS employment data all the way to a DSCR and an IC recommendation. That translation — from signal to underwriting to decision — is the hard part, and it's the part I own.
- **The methodology generalizes.** PBSA was the proving ground because its demand drivers are legible, but the same leading-indicator engine applies across residential asset classes and, with the climate extension, across longer-horizon risk.

---

## The Sirocco expansion

The original build proved the core: labor-market leading indicators, forecast into housing demand, delivered to analysts as finished diligence. Sirocco is where I take that further than the original scope allowed:

- **A climate demand-and-risk thesis** layered onto the existing risk engine — treating physical and transition climate risk as forecastable demand and supply signals, not ESG boilerplate.
- **A relationship layer** so that partners, lenders, and LPs connect to live market predictions, not a static CRM.
- **A deeper agentic workflow suite** so more of the diligence-to-decision pipeline runs as a standardized, auditable process.

This is the same architecture, expanded with the things I would build differently now — and it's the reference for how I approach any commercialization-grade analytics system: start from a real operator problem, ground the model in defensible theory and public data, validate it honestly on a holdout, and put it where the decision actually gets made.

---

*Interested in a system like this for your team? [Start with an AI-Readiness Check](https://kylecedrichanna.com) or book an intro call.*
