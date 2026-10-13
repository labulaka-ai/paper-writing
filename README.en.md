<p align="right"><a href="https://github.com/labulaka-ai/paper-writing/blob/main/README.md">简体中文</a> | <strong>English</strong></p>

# paper-writing · Academic Paper Writing Skill

![License](https://img.shields.io/badge/license-MIT-blue.svg) ![Agent Skill](https://img.shields.io/badge/Agent%20Skill-SKILL.md-green) ![Docs](https://img.shields.io/badge/docs-中文%20%7C%20English-orange)

> Author: **Labulaka** (GitHub [@labulaka-ai](https://github.com/labulaka-ai)) · WeChat Official Account: 「时空AI深水区」 (Spatiotemporal AI Deep Dive)

[Why I built this](#why-i-built-this) · [My design](#my-design-one-core-method-several-reinforcements) · [Core mechanisms](#core-mechanisms) · [Repository layout](#repository-layout) · [Installation and use](#installation-and-use)

I'm a PhD candidate working on spatiotemporal big data. This skill is my own paper-writing workflow, distilled from drafting, revising, and surviving peer review, and packaged for AI agents (Claude Code and compatible skill runtimes). When it writes or revises an Introduction, Methodology, Results, Discussion, or Abstract, it first builds a **claim–evidence spine**, then drafts each section by its **functional modules**, calibrates every sentence with **language mechanics**, and only reports "ready to submit" after passing a set of **pre-submission gates**.

It is not a prompt collection. It is a workflow with adjudication rules: when structural models disagree, which one wins is written down; how strongly a claim may be stated is decided by its evidence grade, not by tone. Those rules are lessons I paid for, draft after draft.

---

## Why I built this

I have let general-purpose LLMs help me write plenty of drafts. Their failure modes are remarkably stable:

- **Structural patchwork** — every section looks plausible, but the Introduction's claims have no evidence in the Results, and each section states the research question differently;
- **Broken calibration in both directions** — overclaiming ("consistent with" upgraded to "demonstrates"), or **over-defensive writing**: measured facts hedged with "might", three hedging devices stacked in one sentence, contributions apologised for before any reviewer has objected;
- **Untrustworthy citations** — references generated from memory, citations attached to claims they don't support;
- **Language detail failures** — tense drifting so readers can't tell my work from prior work, articles that quietly change a sentence's meaning, "may not" confused with "cannot".

This skill exists to block those four failure classes with process and gates, before delivery.

## My design: one core method, several reinforcements

The core method is **functional modules + language mechanics**: for each section, first answer "what is this section for" (its functional modules and drafting flow), then "how exactly should each sentence say it" (tense, modality, connectives, articles, adverb placement, hedging — the language mechanics). This is the backbone of the whole system; when rules conflict, it wins.

Around that backbone I wired in the structural tools I actually use: the CARS three-move model and a title checklist for introductions, a five-component abstract model, per-section structure cards with ML/CV variants (method-paper introductions, abstract variants), venue templates and page-count conventions, and a cross-model review loop. Figures run through a separate two-stage workflow (Section 6 below); the chart-selection and styling tools it uses are external dependencies, not bundled here. This combination is what survived repeated use on my own manuscripts — everything in it is there because it blocks one of the four failure classes above.

## Workflow

**Step 0 · Spine before prose.** Produce a one-page `PAPER_PLAN`: a one-sentence contribution, a claim–evidence map (each claim ↔ its evidence ↔ figure/table ↔ **evidence grade**), a gap statement (it must be licensed by the literature review — never invented), and the venue-specific structure model and length budget.

**Step 1 · Section drafting, four passes per section.** My drafting order: Methodology → Results → Discussion → Introduction → Abstract (the abstract is written last). Every section goes through: ① functional modules → ② structure card (variant chosen by venue and paper type) → ③ language-mechanics check → ④ the section's self-check list. A delivered section draft must come with its self-check results, not just prose.

**Step 2 · Figures.** Figures are mostly final before the Results text is written: selection first, standards second, and the prose follows the final figures.

**Step 3 · Pre-submission gates.** Six gates (plus an anti-over-defense audit) are checked item by item; if any gate fails, the draft may not be reported as submittable. After major revisions, the relevant gates are re-run.

## Core mechanisms

### 1. Evidence grades E1–E4: claim strength follows evidence

Every claim is graded in `PAPER_PLAN`. The grade is also the unit of account for the hedging budget below.

| Grade | Meaning |
|---|---|
| E1 | Directly measured / observed in this paper |
| E2 | Strong inference, supported by multiple experiments or ablations |
| E3 | Weak inference, single or indirect evidence |
| E4 | Speculation / extrapolation beyond the evidence |

### 2. The hedging budget: an anti-over-defense mechanism

This is a hard rule I imposed after watching agents get timid on my own manuscripts. Hedging is a cost paid out of evidence, not free insurance. Miscalibration runs both ways: weak evidence in strong language is overclaiming; strong evidence in weak language is over-defense — both are distortions. The rules live in `references/language-mechanics.md` §3:

| Evidence grade | Hedging budget |
|---|---|
| E1 | **0 layers**: state it plainly; no "may / might / suggest" |
| E2 | ≤ 1 layer |
| E3 | 1–2 layers |
| E4 | Must hedge, and say plainly that it is speculative |

Five supporting rules:

- **One device per sentence**: at most one hedging device per sentence; "suggest + may + appears" stacks are allowed only on E4 claims;
- **No hedging facts**: measured values, method facts, and direct observations take no hedges — hedging protects inferences, not facts;
- **Write at full strength first, downgrade only for a named gap**: draft each claim at the strongest version the evidence supports; every downgrade must name the evidence gap forcing it (which experiment, which control is missing). No named gap, no downgrade;
- **Never soften a contribution sentence**: if a claim is too strong, narrow its scope (say exactly where it holds) instead of weakening its tone;
- **Defensive-pattern blacklist**: self-deprecating openers ("although our method is simple..."), "we only...", self-diminishing adjectives, and filler hedges like "it should be noted that..." are banned without evidence; genuine limitations live in exactly one place — the Limitations section.

Before submission, the draft also passes **Gate 3B, the defense audit** (`references/gates.md`): every hedge in the manuscript is marked, checked against its claim's evidence grade, and delivered as a **hedging audit table** alongside the draft. It pairs with Gate 3, which hunts overclaiming — one gate for too strong, one for too weak.

### 3. The language-mechanics toolbox

Organised by tool in `references/language-mechanics.md`; I run it item by item during the language pass of any section:

- **Tense semantics**: tense marks attitude and attribution — citing prior work in the present tense tells the reader you treat it as established truth, the past tense as a finding of its time; standard procedures (present) vs. my own operations (past) are checked at every switch;
- **Modal-verb truth-value calibration**: six functions (ability / possibility / probability / virtual certainty / advice / necessity), each verb weighted, including the pairs everyone confuses: "may not" (possibly not) ≠ "cannot" (impossible), "must" = "no other explanation", "did not need to" ≠ "need not have", "should" (advice to the community) vs. "will" (my own plans);
- **The hedging ladder**: bridge verbs (`suggest / indicate / imply` < `demonstrate / prove`), the standard move for problem data (acknowledge it, hedge its impact, pivot to what holds), and a ban on upgrading "consistent with" into "demonstrates";
- **Connectives, with misuse warnings**: no sentence-initial "so"; "conversely / on the contrary" imply one side is wrong — use "whereas / while" for neutral contrast; "However / Although" are the gap signals in an introduction;
- **Articles a / the**: changing the article changes the claim — "may hide a connection" (one may exist, unseen) vs. "may hide the connection" (it exists and is hidden);
- **Adverb placement in three steps**: against sentences that are grammatically perfect and semantically wrong;
- **Section-dependent passive voice, plus stand-in subjects**: the Introduction may not describe my own work in agentless passive ("This paper presents..."); in Methods the passive is standard but must carry an attribution system ("In this study, ..." / "As described by X, ...") so mine and theirs never blur.

### 4. Section modules at a glance

| Section | Skeleton |
|---|---|
| Introduction | A four-step funnel: field significance → background & literature → the gap (licensed by the review; no blanket negations) → this paper; reinforced with the CARS moves and a title checklist |
| Methodology | The goal is to **persuade, not to record**: precise record + justification + professionalism; the attribution system is this section's lifeline; every module carries Motivation / Mechanism / Evidence |
| Results | A four-module menu: opening guide → core presentation (explicit figure invitations, only key results in detail, evaluative language) → problem data → a closing bridge sentence (no stronger than `suggest / indicate / imply`); ordering follows the evidence ladder, not experiment chronology |
| Discussion | A reverse funnel in four modules: revisit → map onto the literature → contributions & implications (rival explanations handled before generalising) → limitations & future work; conclusions pass a claim check |
| Abstract | Written last; two models (structured, one module per sentence / merged); the abstract is "the shortest evidence chain" and must stand alone in a database |

### 5. Pre-submission gates (`references/gates.md`)

1. **Citation verification**: every citation is checked against its source and must support the claim it hangs on; BibTeX entries come through a verification chain (DBLP → CrossRef), never from model memory; zero leftover `[VERIFY]` markers;
2. **Verbatim RQ consistency**: the research question reads identically in abstract, introduction, methods, and discussion; core terms are never renamed mid-paper;
3. **Claim–evidence alignment**: every experiment has an argumentative job; jobless ones are cut, shrunk, or moved to an appendix; over-strong claims are narrowed to what the evidence supports;
4. **Gate 3B, defense audit**: see above;
5. **Reverse outline**: reading only the first sentence of every paragraph should reconstruct a coherent miniature of the paper;
6. **Cross-model review**: a different model family reviews the draft; comments are triaged by severity; includes a five-pass writing-quality self-check;
7. **Venue template / pages / disclosure**: template, page-count conventions (ML conferences vs. IEEE differ), citation commands, and the AI-use disclosure placement are checked against the target venue's current policy.

### 6. Two-stage figures (`references/figures.md`)

My figures go in two stages: **selection first** — candidate layouts and colour schemes are laid out side by side (freely combinable: A's layout with C's palette), rendered with my own data, and compared against the samples; **standards second** — the chosen design is produced to publication-grade house style with vector export conventions. On top of that: four text–figure rules (invite the reader to look, detail only the key results, set the reading with evaluative language, never repeat numbers between text and captions) and anchor-figure rules (the overview figure anchors the Methods section; the main-result figure and the abstract together decide whether a reviewer keeps reading). The tools behind these stages (plot-is-all-you-need, figures4papers) are installed separately and are not bundled in this repository; figures in their galleries may be referenced for layout and colour only, never reproduced.

## Repository layout

```
paper-writing/
├── SKILL.md                        # Entry point: workflow, routing, operating rules
├── README.md                       # Chinese version
├── README.en.md                    # This file
├── LICENSE
└── references/
    ├── introduction.md             # Funnel, CARS, method-paper variants, title checklist
    ├── methodology.md              # Persuasion goals, attribution system, module triad
    ├── results.md                  # Four-module menu, evidence ladder, statistics discipline
    ├── discussion.md               # Reverse funnel, rival explanations, claim check
    ├── abstract.md                 # Two models, tense division, five components, ML/CV variants
    ├── language-mechanics.md       # Tense / modals / hedging budget / connectives / articles / adverbs / passive
    ├── figures.md                  # Selection, standards, text–figure rules, anchor figures
    └── gates.md                    # Pre-submission gates incl. the defense audit
```

## Installation and use

Clone or copy this repository into your agent's skills directory (for Claude Code, e.g. `~/.claude/skills/paper-writing/`), keeping `SKILL.md` and `references/` in their relative layout.

Example triggers (Chinese or English):

- "Help me revise this Introduction — the gap feels unconvincing"
- "How should I structure the Methods section? Here are my experiment logs"
- "My abstract is too long; compress it to under 250 words"
- "Run the pre-submission gates on this draft" / "Do a defense audit"
- "What chart should this result be?" → routes into the two-stage figure workflow (the two companion tools must be installed separately)

Scope: conference papers (CVPR / ICCV / NeurIPS / ICML and similar) and journal manuscripts. **Not** for explainer or popular-science articles — a different genre, where this skill's claim–evidence discipline would be over-tight.

## Status, honestly

I use this in my own paper workflow (core method frozen in October 2026). Two disclosures:

- **The hedging budget and the defense audit are new (2026-10-10)**, already wired into the workflow and gates; their full effect awaits my first complete manuscript run through them, and I will update this section afterwards;
- This skill provides a writing process and checklists — it does not replace domain judgement or the experiments themselves; time-sensitive items (citation records, venue policies) should be verified against the official sources at submission time.

## License

MIT — see `LICENSE`. If you redistribute or adapt this skill, please keep the author attribution line in the files.

---

**Author**: Labulaka ([@labulaka-ai](https://github.com/labulaka-ai)), PhD candidate in spatiotemporal big data
**WeChat Official Account**: 「时空AI深水区」 — paper explainers and first-hand tests at the intersection of spatiotemporal data and AI
