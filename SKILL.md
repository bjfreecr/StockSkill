---
name: supply-chain-bottleneck-hunter
description: Use when the user asks to find supply chain chokepoints, identify monopoly/duopoly suppliers, do Serenity-style industry bottleneck analysis, or hunt for undervalued companies sitting on structural supply constraints in any industry. Triggers: "find bottlenecks in X", "supply chain chokepoint", "卡脖子", "bottleneck analysis", "供应链瓶颈", "what are the critical suppliers for X".
---

# Supply Chain Bottleneck Hunter

## Overview

Six-phase methodology for identifying structural chokepoints in any industry's supply chain. Based on the approach used by Serenity (@aleaborteddit) to find single/duopoly suppliers at critical nodes where switching costs are prohibitive, certification cycles are long, and the market has not yet priced the revenue inflection. Only output publicly traded companies.

Core principle: find the "AXTI Moment" — a tiny company sitting on an irreplaceable bottleneck that the entire industry must route through, before institutional capital piles in.

## The Six Phases

Execute in strict order. Each phase feeds the next.

### Phase 1: Define the End Product

Define the terminal product or service. Identify its key subsystems (max 4-6). Build a table:

```
| Subsystem | Function | Differentiation from industry standard |
```

Also note the demand context: what is the projected demand growth (e.g., units/year CAGR, TAM expansion rate)? A bottleneck's severity = supply constraint × demand growth rate. A tight but flat market is less interesting than a moderately tight market growing 100% YoY.

This is the anchor. Everything reverses from here.

### Phase 2: Reverse-Map the Supply Chain

For each subsystem, trace backward layer by layer until you reach raw materials. Build a tree:

```
Terminal Product
  ├── Subsystem A
  │   ├── Component A1 → Material A1a → Raw input
  │   └── Component A2 → Material A2a → Equipment A2b
  ├── Subsystem B
  │   └── Component B1 → ...
  └── Manufacturing equipment
      ├── Tool X
      └── Tool Y
```

Focus on the layers that differ from the current industry standard — those are where bottlenecks hide.

### Phase 3: Bottleneck Scoring (per node)

Score each supply chain node on four dimensions. Score 1-3 on each. **Only advance nodes scoring ≥10 to Phase 4.**

| Dimension | Score 1 (commodity) | Score 2 (tight) | Score 3 (chokepoint) |
|-----------|---------------------|-----------------|----------------------|
| **Supplier count** | ≥5 suppliers | 2-4 suppliers | 1 supplier / tight duopoly |
| **Switching cost** | < 3 months, < $1M | 3-12 months, $1-50M | >12 months, >$50M or impossible |
| **Certification cycle** | None / weeks | 6-18 months | 2-5+ years |
| **Technical barrier** | Standard process | Specialized IP/patents | Fundamental physics/materials constraint |

**Overlap rule**: If a node scores 3 on both "switching cost" AND "technical barrier" for the same reason (e.g., node is physically irreplaceable), do NOT double-count. Cap one at 2. The reason must be distinct to score 3 on both.

**Equipment supplier override**: If a piece of manufacturing equipment has <100 units installed globally and 18+ month lead time for new orders, AND it is required for the terminal product, add +2 to its final score. This catches TC Bonders, EUV scanners, hybrid bonders, and similar tooling bottlenecks that the base scoring system undervalues.

Score interpretation:
- **15-16 (🔴 Critical)**: Structural monopoly, no alternative, long cert cycle. Publish as Tier 1.
- **13-14 (🔴 High)**: Tight duopoly, very high switching cost. Publish as Tier 1.
- **10-12 (🟡 Potential)**: Few suppliers, alternatives exist but are slow/expensive. Publish as Tier 2.
- **<10**: Skip — not a real bottleneck.

### Phase 4: Technical Deep-Dive (for 🔴 and 🟡 nodes)

For each advanced node, verify the bottleneck is structural, not temporary:

1. **Search technical sources**: For early-stage tech — academic papers (Google Scholar, arXiv), patents (Google Patents). For commercialized tech — industry reports (SemiconductorX, Digitimes, EE Times, Nikkei Asia), supplier earnings call transcripts, investor presentations, trade press
2. **Find independent confirmations**: CEO earnings call quotes, government shortage reports, industry association statements, Reuters/Bloomberg trade coverage. At least one external source per bottleneck
3. **Track timeline**: when was this bottleneck first identified? By whom? Has it worsened or eased over time?
4. **Assess alternatives**: what are the substitute technologies/materials? How far along are they? Estimate TRL (Technology Readiness Level: 1-9) and timeline to viability
5. **Demand context**: briefly note the demand growth trajectory for the terminal product (e.g., AI capex forecasts, deployment roadmaps). A bottleneck's severity = supply constraint × demand growth rate
6. **Recursive check (optional)**: what constrains THIS bottleneck's ability to expand? If the answer is another single-supplier, note it as a meta-bottleneck

### Phase 5: Target Screening (public companies only)

Filter to publicly traded companies only. For each, retrieve:

- Ticker, exchange, market cap, recent stock price, YTD performance
- Institutional ownership (top 3 holders, % institutional, trend direction)
- Certification stage: **pre-cert → certifying → ramping → mature**
- Revenue inflection estimate: when does the bottleneck translate to revenue?
- **Financial health snapshot** (optional, for ≥$1B companies): FCF margin, debt/equity ratio, R&D as % of revenue. Critical for judging whether the company can fund capacity expansion

Flag and skip: private companies, subsidiaries of larger conglomerates without pure-play exposure, companies where the bottleneck represents <10% of revenue.

### Phase 6: Investment Analysis Output

Structure every 🔴 and 🟡 bottleneck in this exact format:

```
### 🔴/🟡 [Bottleneck Name] — Supply Chain Score: XX

**Position**: [Layer] of [Subsystem]
**Supplier count**: N suppliers | **Switching cost**: [time/cost] | **Cert cycle**: [duration]

**Why it's a bottleneck** (2-3 sentences):
[Technical explanation of why this is structural, not temporary]

**The "海峡" analogy** (1 sentence):
[Like __ is the Strait of Hormuz for __, this is the chokepoint for __.]

**Public companies at this bottleneck**:

| Ticker | Name | Mkt Cap | Price | YTD | Cert Stage | Rev Inflection |
|--------|------|---------|-------|-----|------------|----------------|
| [TICKER] | [Name] | [$XXB/M] | [$XX] | [+/-XX%] | [stage] | [quarter/year] |

**What's priced in** (2-3 sentences):
[Is the market already aware? Is this an overcrowded trade or under-the-radar?]

**Institutional ownership trend**:
- [TICKER]: Top holders [A, B, C], institutional % [XX%], trend [accumulating/distributing/flat]

**Independent verification**:
- [Source, date]: "[Quote from CEO/government/industry report]"

**Catalyst timeline**:
| Timeframe | Event | Impact |
|-----------|-------|--------|
| [Q/N} | [Catalyst] | [Expected effect] |

**Bear case / risk factors** (2-3 bullets):
- [Alternative technology risk]
- [Regulatory/geopolitical risk]
- [Capacity/execution risk]
```

## Quick Reference

| Phase | Key Question | Output |
|-------|-------------|--------|
| 1. Define | What are we mapping? | Subsystem table |
| 2. Reverse-map | What does it take to make this? | Supply chain tree |
| 3. Score | Is this a real bottleneck? | Scored node list |
| 4. Deep-dive | Is it structural or temporary? | Verified thesis with sources |
| 5. Screen | Which are public and pure-play? | Filtered company list |
| 6. Output | What should an investor know? | Formatted bottleneck cards |

## Common Mistakes

| Mistake | Fix |
|---------|-----|
| Skipping scoring and calling everything a bottleneck | Every node MUST be scored. Only nodes ≥10 advance. |
| Listing private companies or conglomerate subsidiaries | Phase 5: filter to public pure-play only. Flag private ones but don't list them. |
| No independent verification — just the analyst's opinion | Phase 4 rule: at least one external source per bottleneck. |
| Ignoring "what's priced in" — assumes all bottlenecks are hidden gems | Phase 6 requires explicit assessment of market awareness. |
| Chasing nodes at the raw material layer that are commodity cyclical rather than structural | Phase 3: supplier count = 1-2 BUT switching cost low → NOT a bottleneck. |
| Omitting the bear case | Every bottleneck card must have risk factors. Serenity openly flags his own risks. |
| Using ChatGPT/LLM for technical analysis without source verification | Serenity: "Photonics is nuanced. Using ChatGPT will make you miss all the details." Search primary tech sources. |
| Under-scoring equipment suppliers with <100 units globally installed | Use the equipment override (+2) for tooling with <100 units and 18+ month lead time. |
| Double-counting switching cost and technical barrier for the same root cause | If both are 3 for the same reason, cap one at 2. |
| Ignoring demand side — bottleneck severity = supply constraint × demand growth | Phase 4 step 5: always note demand trajectory. A loose bottleneck in a 100x demand scenario is tighter than a tight bottleneck in a flat market. |
