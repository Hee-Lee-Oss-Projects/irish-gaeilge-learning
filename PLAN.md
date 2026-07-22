# PLAN — irish-gaeilge-learning

> Status: Draft · Version: 0.1.0 · Last updated: 2026-06-28 · Owner: TBD (acting maintainer: J. Carter) · Lane: donated

## Executive summary

`irish-gaeilge-learning` is a Hee-Lee Oss good-deed project that builds a **free, openly-licensed,
structured course for learning Irish (Gaeilge)** — spoken and written — aligned to the **CEFR**
and mapped to the **TEG** (Teastas Eorpach na Gaeilge) level descriptors, with **native-speaker
review of every piece of Irish that ships**. It exists to support **language revitalization**:
to give learners worldwide a high-quality, non-commercial path into a minority and endangered
language, and to give teachers and community groups a reusable Open Educational Resource (OER)
they can adapt freely.

The work runs in the **donated lane**: a human runs their own coding agent interactively to draft
lesson scaffolding, exercises, and supporting tooling, then opens PRs; the Hee-Lee Oss CLI only prepares
workspaces and opens PRs. The project is **medium risk tier** — the risk is **language accuracy**
and **cultural fidelity** in a living minority language. The binding control for that risk is a
**qualified native/near-near-native reviewer sign-off** on all Irish content before it is marked
delivered, plus a **second independent reviewer** for the highest-risk material (pronunciation,
dialect claims, grammar with negation/mutation).

Three constraints define this project's identity (see §3 and §5):

1. **No unreviewed AI-generated Irish ever ships.** The agent drafts *English-language scaffolding*
   (explanations, lesson sequencing, exercise structure) and may *propose* Irish, but **no Irish
   word, sentence, or audio caption is published without a qualified human reviewer's sign-off.**
   Flooding a fragile language with plausible-but-wrong machine Irish would actively harm the
   revitalization cause; refusing to do so is a feature, not a limitation.
2. **Dialect parity, not a "correct" dialect.** Irish has three living dialect groups — **Munster
   (Mumhain)**, **Connacht (Chonnacht)**, and **Ulster (Uladh)** — alongside *An Caighdeán
   Oifigiúil* (the official written standard). We teach the **written standard for spelling and
   grammar** and present **audio in all three dialects with explicit labels**, and we **never rank
   one dialect as more correct than another.** This is a locked decision (§3).
3. **Licence and provenance discipline, especially for audio.** Recorded human voice is both
   copyrighted performance and **personal data**. We use only (a) openly-licensed audio (e.g.
   Mozilla Common Voice Irish, CC0), (b) **newly recorded audio with signed consent and a
   performer release**, or (c) open synthetic speech **if and only if its licence permits
   redistribution**. We **never scrape** broadcasters or commercial courses. Content that cannot
   be correctly licensed, attributed, and provenance-tracked is not shipped.

Honest status note: **no partner organisation or pilot learner cohort is yet secured.** Until one
is, `verifiedNeed` is recorded as **`false`** on tasks whose value depends on a named beneficiary,
and the project's Definition of Shipped (adoption by real learners/a partner) cannot be fully met.
Securing a first partner and a pilot cohort is the top open dependency (§16, Roadmap M2).

## Problem & beneficiaries

**Who is helped.**
- **Adult and heritage learners worldwide** — including the large global Irish diaspora — who want
  to learn Irish but have no affordable, structured, audio-rich, openly-licensed path, especially
  outside Ireland where classes are scarce.
- **Parents and carers** supporting children in Gaelscoileanna / Gaeltacht schooling who are
  learning the language alongside them.
- **Teachers and community groups** (conversation circles, *ciorcail chomhrá*, diaspora cultural
  centres) who need free, adaptable OER they can localise and reuse without licensing fees.
- **Self-directed learners preparing for recognised assessments** who want CEFR/TEG-aligned
  practice material (the course is *aligned to*, not *accredited by*, TEG — see §3, §7).

The ultimate beneficiary outcome is **more people able to understand, speak, read, and write Irish
to a defined CEFR level**, contributing to the language's survival and everyday use.

**The need.** Irish is classified by UNESCO as **definitely endangered**. Demand to learn it is
large and global (it is among the most-studied languages on mass-market apps), but the high-quality,
**openly-licensed** supply is thin: most structured, audio-rich courses are commercial and
closed; most free material is fragmentary, dialect-inconsistent, or lacks native-speaker-verified
audio. Generic machine output is unsafe for a minority language — it mangles **initial mutations**
(*séimhiú/urú*), the **copula vs. *bí***, negation, and dialect-specific forms, and it has no
provenance or review. The gap is **accurate, attributed, reviewed, dialect-honest, free** material
that a learner can actually rely on and a teacher can actually adopt.

**Verified need: TO BE SECURED.** The *category* need (endangered language, large unmet demand for
free quality material) is well-evidenced. But a **specific requesting partner, a target learner
cohort, and an agreed scope/priority** are **not yet secured.** Tasks are written so the project can
build reusable, partner-independent foundations (dialect policy, source allow-list, content schema,
review machinery, one reviewed A1 unit) **without** a partner, while flagging that
**pilot/adoption tasks are blocked** until a partner and cohort are confirmed.

**Partner org: TO BE SECURED.** Candidate partner/requestor types (none committed as of this
draft): community language organisations (e.g. Conradh na Gaeilge, Glór na nGael), Gaeltacht
co-operatives / *comharchumainn* and Údarás na Gaeltachta, Foras na Gaeilge, university Irish
departments and TEG/Lárionad na Gaeilge (Maynooth University), immersion providers (e.g. Oideas
Gael), the Gaelscoileanna network (Gaeloideachas), and diaspora Irish cultural centres. **No
organisation has endorsed, requested, or committed to this project.**

## Goals and non-goals

**Goals**
- Produce a **free, openly-licensed, structured Irish course** (text + audio) covering at least
  **CEFR A1** fully, with **A2** scoped, and a clear path to **B1**.
- Make every Irish artefact **native-speaker reviewed** and **provenance/licence verified** before
  publication — accuracy and cultural fidelity over speed.
- Honour **dialect parity**: standard spelling/grammar, all-three-dialect audio, no ranking.
- Deliver material that **teachers and community groups can adopt and adapt** (OER), and that
  **learners can use offline** and in low-bandwidth settings.
- Build the course as **structured data** (validated content schema) so it can be re-rendered to
  web, print, spaced-repetition decks, and accessible formats from one source of truth.
- Demonstrate **real learner outcomes** through a small pilot with pre/post can-do measurement.

**Non-goals (what this project will NOT do)**
- **It will not publish AI-generated Irish without native-speaker sign-off.** Ever. (§3, §5.)
- **It will not claim official accreditation.** It is **aligned to** CEFR and **mapped to** TEG
  descriptors; it is **not** an official TEG, Department of Education, or Foras na Gaeilge product,
  and it does not issue certificates.
- **It will not replace teachers, classes, or Gaeltacht immersion.** It is a complement and an
  on-ramp, framed as such.
- **It will not pick a "best" dialect** or present learner/standard pronunciation as the single
  correct speech.
- **It will not scrape or relicense copyrighted material** — no ripping audio/text from
  broadcasters (e.g. RTÉ, TG4, Raidió na Gaeltachta), commercial courses, or textbooks.
- **It will not record or publish minors' voices**, and will not collect person-level learner data
  beyond what a small, consented pilot strictly requires.
- **It will not be a chatbot or a live conversation partner** that generates unreviewed Irish on
  demand. (A reviewed, fixed-content practice tool is in scope; an open-ended Irish-generating LLM
  is not.)
- **It will not run in the funded lane in v0.1.** (Funded use is bounded and deferred — §6, §12.)

## Success metrics (outcomes)

Outcome-centric, beneficiary-first. Baselines are honestly **n/a (pre-pilot)** until a cohort
exists; targets are set for first measurement.

| # | Outcome metric | Baseline | Target (first window) |
|---|---|---|---|
| 1 | **Learner attainment** — pilot learners who meet the A1 can-do self/teacher assessment after completing the A1 module | n/a (pre-pilot) | ≥ 60% of pilot completers meet ≥ 80% of A1 can-do statements |
| 2 | **Completion** — pilot learners who finish the A1 module they start | n/a | ≥ 50% completion of started module (honest for self-paced OER) |
| 3 | **Accuracy / defect rate** — critical Irish-language errors found *after* publication per 100 reviewed items | n/a | 0 critical (mutation/negation/meaning-changing) errors post-publication; ≤ 1 minor/100 items |
| 4 | **Openness & provenance** — published assets with verified licence + provenance + reviewer sign-off | n/a | **100%** (hard gate — no exceptions; CI-enforced) |
| 5 | **Dialect parity** — A1 audio coverage across the three dialect groups for core vocabulary/phrases | n/a | All three dialects present for ≥ 90% of A1 core items, with dialect labels |
| 6 | **Adoption** — partner/teacher/community group that formally adopts the material for learners | 0 | ≥ 1 partner adopts the A1 module for a real learner group |
| 7 | **Accessibility** — content meeting WCAG 2.2 AA (captions, transcripts, keyboard, contrast) | n/a | 100% of published web units pass the a11y checklist |
| 8 | **Reuse** — downloads/forks/derivative uses by teachers (proxy for OER value) | 0 | tracked from launch; first 5 documented reuses |

We explicitly **avoid vanity metrics** (page views, "lessons generated"). A lesson that exists but
is unreviewed or unused counts as **zero**.

## Scope

**In scope**
- Course **content as structured data**: CEFR/TEG-tagged units (vocabulary, dialogue, grammar
  notes, cultural notes, exercises) for **A1** (full), **A2** (scoped), groundwork for **B1**.
- **Audio**: native-speaker pronunciation per item, dialect-labelled (Munster/Connacht/Ulster),
  sourced/recorded under verified licence + consent; aligned to text; with transcripts.
- **Pronunciation support**: IPA and per-dialect pronunciation notes per core lexical item.
- **Exercises**: typed, auto-checkable where possible (matching, ordering, cloze, listening,
  dictation), reviewed for correctness.
- **Outputs/renderings** from the single source: open **web course** (static site), **offline/
  low-bandwidth packs** (downloadable), **spaced-repetition export** (Anki/CSV), and
  **accessible formats**.
- **Tooling**: content schema + validation, licence/provenance CI gate, audio provenance/consent
  manifest, reviewer sign-off workflow, link-rot/source-change watcher.
- **A small pilot** with consenting adult learners and pre/post can-do measurement (M2+).

**Out of scope**
- Full B2/C1/C2 levels (future; B1 only scoped).
- Live conversation/chatbot generation of unreviewed Irish (non-goal, §3).
- Speech *recognition*/automatic pronunciation scoring (no reliable open Irish ASR assumed; out of
  scope for v0.1; could be a future, separately-reviewed module).
- Official certification/exam delivery.
- Children's product / classroom LMS integration (future; current pilot is adults only to avoid
  minors' data).
- Translating copyrighted literature or broadcaster content.

## Solution approach & architecture

A **content-as-data pipeline**, not a bespoke app. One reviewed source of truth renders to many
formats; every gate is enforced in CI.

**Components**
1. **Content schema (the spine).** TypeScript/JSON-Schema-defined model for a learning unit:
   - `unit`: id, CEFR level (`A1`/`A2`/`B1`), TEG-band mapping, can-do statements, topic, theme.
   - `items[]`: lexical/phrase entries with `irishStandard` (An Caighdeán spelling), `english`,
     `partOfSpeech`, `grammarNotes`, `ipa`, `dialectNotes` (per-dialect pronunciation/usage),
     `audioRefs[]` (each with provenance — see audio manifest), `culturalNote` (optional).
   - `exercises[]`: typed (`cloze`/`match`/`order`/`listen`/`dictation`/`mcq`), with answer keys
     and rationale, all reviewable.
   - `review`: `status`, `reviewerId`, `reviewerCredential`, `reviewDate`, `secondReviewerId`
     (required for pronunciation/dialect/negation items), `agentFlags[]` (unresolved
     `UNCERTAIN:` notes block sign-off).
   - `provenance` / `license` block on every asset.
2. **Audio provenance & consent manifest.** Per audio file: `source` (CC0 corpus | new recording |
   open TTS), `licence`, `attribution`, `speakerConsentRef` (for new recordings: signed consent +
   performer release on file), `dialect`, `speakerIsAdult: true`, `snapshotHash`, `recordingDate`.
   **No audio without a complete manifest entry.**
3. **Validation + gates (CI).** (a) **Structural gate** — every unit validates against the schema,
   has a CEFR tag, reviewer sign-off, and no unresolved agent flags. (b) **Licence/provenance gate**
   — every text/audio asset has a verified licence, attribution, and provenance; build **fails**
   otherwise. (c) **A11y gate** — published units pass the accessibility checklist.
4. **Renderers.** Static-site generator (e.g. Astro/Eleventy) → open web course; an offline pack
   builder (zipped HTML+audio+transcripts) for low-bandwidth use; a spaced-repetition exporter
   (Anki/CSV); accessible exports.
5. **Source allow-list.** Per-source licence terms file (mirrors the proven `vital-info-translations`
   pattern), with snapshot hashes and a **source-change/link-rot watcher**.
6. **Reviewer workflow.** Checklist + handoff template; sign-off recorded in the PR; COI/independence
   rules; second-reviewer and (for grammar-critical items) a back-translation QA pass.

**Tech stack.** TypeScript, ESM, pnpm workspaces. Content authored as JSON/YAML validated by the
schema. **Code: MIT.** **Content: CC BY-SA 4.0** by default (share-alike keeps derivatives open and
is compatible with Wikimedia-sourced text); individual assets carry the **source-compatible**
licence where stricter (e.g. CC0 audio stays CC0-attributed). No relicensing of third-party
material.

**Key decisions (locked).**
- **An Caighdeán Oifigiúil** for written standard; **all three dialects** in audio with labels (§3).
- **Human review is a hard gate**, not advisory.
- **Content is data first**, presentation second (durability, reuse, accessibility).
- **Adults-only** content/voices/pilot in v0.1 (avoids minors' data).
- **Terminology anchored to authoritative references** (e.g. *foclóir.ie* / *téarma.ie*) — subject
  to per-source licence verification (§7).

## Data, licensing & compliance

**This is the most important section. The posture is conservative: if a licence or provenance
cannot be verified, the asset is excluded.**

**Source allow-list.** No source is used until it appears on `sources/allow-list.yaml` with: name,
canonical URL, version/date, retrieval date, **licence name + URL + snapshot of the licence text
(SHA-256 hash + archive URL)**, derivatives-allowed flag, required attribution string, and any
usage restrictions. Entries record `verifiedBy` + `verifiedDate`; anything unclear is **excluded
with a reason**.

**Candidate sources (all licences TO VERIFY per source before use):**
- **Mozilla Common Voice — Irish**: voice clips and sentences typically **CC0**. Strong candidate
  for audio and example sentences. Verify the current release licence and that clips used are CC0.
- **Wiktionary / Wikipedia (Irish)**: text under **CC BY-SA** — compatible with our CC BY-SA 4.0
  content licence; requires attribution + share-alike.
- **An Caighdeán Oifigiúil (2017)** — the official written standard (Houses of the Oireachtas /
  Government of Ireland): used as the **reference standard** for spelling/grammar. **Verify reuse
  terms** before quoting substantial text; facts/rules about the standard are not themselves
  copyrightable, but verbatim text may be.
- **Dictionary/terminology references (*foclóir.ie*, *téarma.ie*, Gaois corpora — Foras na Gaeilge /
  Maynooth)**: used to *check* spelling/terminology. **Do not copy entries**; treat as reference
  unless the specific dataset licence explicitly permits reuse (verify; many are reference-only).
- **Open synthetic speech (e.g. ABAIR, Trinity College Dublin)**: only if its licence permits
  **redistribution** of generated audio (TO VERIFY — likely restricted); otherwise excluded.
- **Originally authored content** (our explanations, exercises, dialogues, newly recorded audio):
  licensed **CC BY-SA 4.0** (audio newly recorded under consent may be released CC BY-SA or CC0 as
  agreed with the speaker).

**Explicitly excluded:** any audio/text scraped from **RTÉ, TG4, Raidió na Gaeltachta**,
commercial apps/courses, or textbooks; any source with non-derivative (ND) terms for content we
need to adapt; any controlled-access or person-identifying dataset.

**Privacy / PII (voice is personal data).**
- Recorded human voice is **personal data** (GDPR). For **new recordings**: a signed **consent +
  performer release** is required and stored (reference id in the manifest), the speaker is
  **informed of the open licence and redistribution**, retains a **right to withdraw**, and is
  **credited** (and, where appropriate, **paid** — see §6/§15). **No minors.**
- For corpus audio (e.g. Common Voice): rely on the corpus's own consent/licence (CC0) and use
  only as its terms allow.
- **Pilot learner data** (M2+): collect the **minimum** needed for pre/post can-do measurement,
  **consented**, **aggregated/de-identified** in any published outcome report, never sold, with a
  retention/deletion policy. No person-level learner data is published.
- **No secrets/PII in logs, receipts, or committed files** (Hee-Lee Oss rule).

**Attribution.** Every published unit ships an `attribution.txt` / provenance block listing each
asset's source, licence, and required attribution verbatim. Share-alike obligations (CC BY-SA) are
honoured downstream.

## Quality, review & risk gates

**Risk tier: medium** (language accuracy + cultural fidelity in a living minority language).

**Required review before any Irish content is "delivered":**
- **Reviewer 1 — qualified language reviewer:** native or near-native Irish speaker **with teaching
  or linguistic competence** (e.g. a *múinteoir Gaeilge* / qualified Irish teacher or linguist),
  **independent of the drafting step** (COI declared). Completes the reviewer checklist; sign-off
  recorded in the PR.
- **Reviewer 2 — second independent reviewer (mandatory for high-risk items):** required for
  **pronunciation/dialect claims, initial mutations (séimhiú/urú), the copula, and any negation or
  meaning-critical grammar**. For such items a **back-translation / reverse-check QA pass** is also
  performed before sign-off.
- **Cultural-notes review:** any cultural/heritage note is reviewed by a culturally-competent
  reviewer to avoid stereotype, error, or appropriation.
- **Agent uncertainty flags:** the drafting agent records `UNCERTAIN: …` flags; **no sign-off while
  any flag is unresolved.**
- **Disagreement rule:** reviewer disagreement is reconciled; if unresolved, escalate to a third
  reviewer/maintainer; the **more conservative/standard reading wins** and the decision is recorded
  in `review`.

**Automated gates (CI):** structural schema validation, licence/provenance completeness,
accessibility checklist. A unit cannot be published if any gate is red.

**Definition of Shipped (project-level).** Acceptance criteria met **and** CI green (schema +
licence/provenance + a11y) **and** native-speaker reviewer sign-off (two reviewers for high-risk
items) **and** the material **actually delivered to and used by** real learners or an adopting
partner. Until a partner/cohort exists, units can reach **"delivered (reviewed, published, open)"**
but the **full Definition of Shipped (adoption/outcome) is pending** (`verifiedNeed: false`).

## Roadmap & milestones

Phased, with measurable **exit criteria**. M0 is a thin, partner-independent foundation; later
phases scale and require a partner.

**M0 — Foundation & cold-start (no partner required).**
Goal: lock policy, stand up the schema + gates + review machinery, and prove the whole pipeline on
**one fully reviewed A1 unit with dialect-labelled audio**.
*Exit criteria:* dialect policy + CEFR/TEG mapping doc merged; source allow-list (≥ 3 verified
sources incl. one CC0 audio source) with snapshot hashes; content schema + audio provenance/consent
manifest + **CI structural and licence/provenance gates green**; reviewer checklist + qualification
criteria + handoff template merged; **one A1 unit** (≥ 15 core items) drafted, **native-speaker
reviewed (two reviewers for pronunciation/mutation items)**, with provenance-verified audio in
**all three dialects** for core items, published to the web renderer, passing the a11y checklist.
All M0 deliverables carry `verifiedNeed: false`.

**M1 — Repeatability & reviewer network.**
Goal: make the pipeline repeatable; recruit/qualify reviewers; complete the A1 module.
*Exit criteria:* ≥ 2 qualified reviewers (or a community/university partner) engaged with COI +
independence + second-reviewer rules documented; terminology/glossary standard anchored to
authoritative references; **full A1 module** (≥ 6 units) reviewed and published; **offline/
low-bandwidth pack** + **spaced-repetition (Anki/CSV) export** working; **WCAG 2.2 AA** conformance
across published units; source-change/link-rot watcher operating; pipeline runbook merged. **Steward
named** (governance prerequisite for M2).

**M2 — First partner & pilot (needs partner).**
Goal: secure a partner + a consenting adult learner cohort; run a pre/post can-do pilot; deliver
and confirm adoption.
*Exit criteria:* a named partner/requestor confirmed in writing (related tasks flip to
`verifiedNeed: true`); a small consented pilot cohort recruited; **pre/post can-do measurement**
run; **A1 module delivered to and used by the cohort/partner**; outcome report published
(aggregated/de-identified) against the §4 metrics; partner confirms adoption in writing (first true
**Definition of Shipped** event).

**M3 — Scale (A2 + dialect breadth + sustained outcomes).**
Goal: extend to A2, broaden dialect audio coverage, and sustain quality + outcome tracking.
*Exit criteria:* A2 module(s) reviewed/published; dialect parity targets met for A2 core items;
reviewer rotation operating; outcomes log live and feeding the metrics table; source
re-verification + audio/link maintenance cadence in effect; named sustainability owner.

**M4 — (future) B1 + ecosystem.** B1 scope, expanded recorded-audio sets (possibly funded
recording sessions under a hard cap), teacher adaptation kits, additional accessible formats. See
TASKS backlog.

## Work breakdown

The itemised backlog — milestone task tables, sizes, risk, dependencies, reviewers, acceptance
criteria, and the milestone Definitions of Done — lives in **[TASKS.md](./TASKS.md)**. Each task
maps to a Hee-Lee Oss Task JSON validated against `packages/schema/src/schemas.ts`. The first robust
backlog spans **M0–M3 with 23 tasks across 4 milestones**, plus a sized-but-unscheduled backlog.

## Governance, roles & stakeholders

- **Maintainer (acting):** J. Carter — owns the repo, schema, gates, and merges until a permanent
  maintainer is named (**Owner: TBD**).
- **Qualified reviewers (rotation):** native/near-native Irish speakers with teaching/linguistic
  competence; sign off all Irish content; rotation + load-balancing established in M1/M3. COI and
  independence rules are binding.
- **Cultural reviewer(s):** culturally-competent reviewer(s) for cultural/heritage notes.
- **Community advisory (target):** representation from **Gaeltacht / native-speaker community** to
  keep the project serving — not extracting from — the language community; advises on dialect
  balance, cultural fidelity, and priorities. **TO BE SECURED.**
- **Steward (last-mile owner):** owns partner relationship, pilot delivery, and confirming real
  adoption/outcomes. **TO BE NAMED** (governance prerequisite for M2).
- **Partner / requestor:** **TO BE SECURED** (candidate types in §2).
- **Decision-making:** dialect/standard/cultural disputes resolved by the conservative-reading +
  escalation rule (§8) with community-advisory input; changes to locked decisions go through a
  documented, public decision record.

## Dependencies & integrations

- **External datasets/sources:** Mozilla Common Voice (Irish), Wiktionary/Wikipedia (Irish),
  An Caighdeán Oifigiúil reference, authoritative dictionary/terminology references (foclóir.ie /
  téarma.ie / Gaois), and possibly open synthetic speech (ABAIR) — **each gated by §7 licence
  verification.**
- **Human dependencies:** qualified reviewers (critical-path — the project cannot ship Irish without
  them); a community advisory; a partner + pilot cohort (M2+); optionally paid native-speaker
  voice talent for new recordings.
- **Tooling/libraries:** static-site generator (Astro/Eleventy), schema validator (Ajv),
  spaced-repetition export format (Anki/CSV), audio normalisation tools — all open-source.
- **Hee-Lee Oss pieces:** the CLI (workspace prep + PRs, donated lane), the Task schema
  (`packages/schema`), and Hee-Lee Oss governance/guardrails (CLAUDE.md, good-deed-definition.md).
- **No funded-lane / API-key dependency in v0.1** (donated lane only; funded use deferred — §6/§12).

## Risks & mitigations

| Risk | Likelihood | Impact | Mitigation | Owner |
|---|---|---|---|---|
| AI produces plausible-but-wrong Irish (mutations, copula, negation) that ships | High | High | Hard human-review gate; second reviewer + back-translation for grammar-critical items; agent `UNCERTAIN` flags block sign-off; no unreviewed Irish ever published | Maintainer / Reviewers |
| Dialect bias — one dialect treated as "correct," alienating communities | Medium | High | Locked dialect-parity policy; all-three-dialect audio with labels; community-advisory oversight; conservative-reading dispute rule | Maintainer / Community advisory |
| Licence/provenance failure (esp. audio/voice) → IP or privacy breach | Medium | High | Source allow-list + snapshot hashes; CI licence/provenance gate (build fails); consent+performer release for new recordings; no scraping; conservative exclusion | Maintainer / Licence reviewer |
| Privacy breach in voice or pilot-learner data (GDPR) | Medium | High | Adults-only; signed consent + withdrawal right; minimal, de-identified pilot data; no PII in logs/commits; retention/deletion policy | Steward / Maintainer |
| No partner / no learners secured → no real outcome | High | High | `verifiedNeed:false` until secured; partner outreach owned by Steward; explicit go/pivot/hold decision point at end of M1; foundations built partner-independently | Steward |
| Reviewer scarcity / single-reviewer bottleneck | Medium | Medium | Recruit ≥ 2 reviewers in M1; rotation + load balancing; partner with a university/community org for reviewer supply | Maintainer / Steward |
| Cultural insensitivity / appropriation in cultural notes | Low–Med | High | Cultural-review gate; community advisory; conservative framing; "complement not replacement" stance | Cultural reviewer |
| Over-claiming accreditation (CEFR/TEG) | Medium | Medium | Explicit "aligned/mapped, not accredited; not official" disclaimer on every rendering; no certificates issued | Maintainer |
| Source/link rot or upstream licence change | Medium | Medium | Snapshot hashes; source-change/link-rot watcher; re-verification cadence; withdrawal procedure if licence changes | Maintainer |
| Harm to linguistic environment (flood of low-quality learner Irish) | Medium | High | No unreviewed Irish; quality-over-quantity metric (unreviewed = zero); native-speaker gate; community oversight | Maintainer / Community advisory |
| Scope creep (B2/C1, ASR, chatbot) diluting quality | Medium | Medium | Explicit non-goals; A1-first; later levels gated on prior-level outcomes | Maintainer |

## Security & privacy

- **Threat surface:** the project ships static content + data; no live user accounts in v0.1. Main
  surfaces are (a) third-party asset licences/provenance, (b) **voice = personal data**, and (c)
  pilot-learner data (M2+).
- **Secrets handling:** no API keys required (donated lane, no funded execution in v0.1). Any future
  funded use carries a hard per-task budget cap and **never writes keys to logs/receipts/commits**.
- **PII:** voice recordings handled per §7 (consent, performer release, withdrawal, adults-only,
  manifest). Pilot data minimal, consented, de-identified in publication, with retention/deletion.
- **Abuse/misuse prevention:** refuse and flag any attempt to use the pipeline to generate
  unreviewed Irish at scale, to scrape copyrighted sources, or to record/publish without consent.
  The "no unreviewed Irish" and "no scraping" rules are enforced socially (review) and technically
  (CI gates + allow-list).
- **Integrity:** snapshot hashes on sources/audio detect tampering or upstream drift.

## Sustainability & maintenance

- **Who maintains after delivery:** the named **maintainer** (TBD) + a **reviewer rotation** keep
  content correct; the **steward** owns the partner relationship and outcome tracking; the
  **community advisory** keeps the project aligned with the language community.
- **Content durability:** content-as-data means re-rendering is cheap; the source-change/link-rot
  **watcher** flags upstream drift; a **re-verification cadence** re-checks source licences and
  refreshes audio links; a **withdrawal procedure** removes any asset whose licence changes to
  forbid reuse, or whose speaker withdraws consent.
- **Outcome tracking:** an **outcomes log** records adoption, pilot can-do results, post-publication
  defects, and teacher reuse — feeding the §4 metrics over time.
- **Funding posture:** the project is non-commercial OER. Optional, **bounded** funding (e.g. paying
  native-speaker voice talent, or a small funded-lane budget-capped alignment/transcription job) is
  possible later (§12), never to the benefit of a for-profit and always under a hard cap.

## Open questions

1. **Partner & cohort:** which organisation(s) will request/adopt, and what is the first agreed
   scope and target learner group? (Top dependency; blocks M2.) **TO BE SECURED.**
2. **Audio strategy:** how much can rely on **Common Voice (CC0)** vs. requiring **new consented
   recordings** for clean, dialect-balanced, item-level pronunciation? Budget/effort for recording?
3. **TTS:** does any open Irish synthetic-speech licence (e.g. ABAIR) permit redistribution of
   generated clips? If not, exclude. **TO VERIFY.**
4. **Terminology reuse:** what exactly may be reused from foclóir.ie / téarma.ie / Gaois (vs.
   reference-only)? **TO VERIFY per dataset.**
5. **Dialect balance:** in cold-start, is full three-dialect audio feasible for every item, or do we
   set a phased coverage target with community-advisory input?
6. **Reviewer supply & compensation:** can reviewers be volunteer (community), academic
   (partnership), or do they need a stipend? Affects M1 timing.
7. **Standard vs. dialect spelling:** edge cases where common dialect forms diverge from An
   Caighdeán — how surfaced without implying error? (Policy detail for M0.)

## References

- `C:\code\hee-lee-oss\CLAUDE.md` — Hee-Lee Oss work rules, lanes, quality bar, refusal guardrails.
- `C:\code\hee-lee-oss\docs\good-deed-definition.md` — the 5 criteria + risk tiers.
- `C:\code\hee-lee-oss\packages\schema\src\schemas.ts` — the Task JSON schema TASKS.md maps to.
- `C:\code\hee-lee-oss\planning\ROADMAP.md` — portfolio context (Track 4; this project listed as
  ⚪ selected, medium risk).
- `C:\code\hee-lee-oss\planning\projects\vital-info-translations\{PLAN,TASKS}.md` — the proven
  licence/provenance + review-gate pattern this plan adapts.
- CEFR (Common European Framework of Reference for Languages) — level descriptors / can-do
  statements.
- TEG (Teastas Eorpach na Gaeilge), Lárionad na Gaeilge, Maynooth University — the recognised
  CEFR-aligned Irish proficiency framework this course maps to (alignment only; not accreditation).
- An Caighdeán Oifigiúil (2017) — the official written standard for Irish.
- Mozilla Common Voice (Irish) — candidate CC0 audio/sentence source (licence to verify per
  release).
- Foras na Gaeilge / Maynooth references: *foclóir.ie*, *téarma.ie*, Gaois corpora (reference;
  reuse to verify). ABAIR (Trinity College Dublin) — candidate open synthetic speech (licence to
  verify).

---

## Appendix A — Improvements applied

Per the planning process, an initial draft was written, then critiqued for 25 specific
improvements, all of which were applied to the plan and tasks above (and in TASKS.md). The list is
retained here so the work is visible.

1. **Dialect-parity as a locked decision**, with a concrete rule (standard spelling/grammar;
   all-three-dialect audio with labels; never rank dialects). *Applied: §3 constraint 2, §6 key
   decisions, metric 5.*
2. **TEG mapping with explicit non-accreditation disclaimer** (aligned/mapped, not official).
   *Applied: §1, §3 non-goals, §7, References, plus a dedicated mapping doc task.*
3. **"No unreviewed AI-generated Irish ships" as a binding refusal.** *Applied: §1 constraint 1,
   §3, §5, §8, risk table.*
4. **Audio provenance + consent manifest schema** (not just licence — consent, performer release,
   dialect, adult flag, hash). *Applied: §6, §7, task -audio-001.*
5. **GDPR/voice-as-PII handling** (consent, withdrawal, adults-only, de-identified pilot data).
   *Applied: §7, §10, risk table, non-goals.*
6. **Second-reviewer + back-translation QA gate** for mutation/negation/dialect-critical items
   (adapted from vital-info-translations). *Applied: §8, reviewer tasks.*
7. **Accessibility (WCAG 2.2 AA) as a first-class, gated requirement** (captions/transcripts/
   dyslexia-friendly). *Applied: §6 a11y gate, metric 7, M1 exit criteria, task -a11y-001.*
8. **Offline / low-bandwidth packs** (reaches rural Gaeltacht + diaspora with poor connectivity).
   *Applied: §6, scope, M1, task -offline-001.*
9. **Reviewer qualification + COI/independence criteria.** *Applied: §8, §11, task -reviewers-001.*
10. **"Do no harm to the linguistic environment" non-goal + metric** (unreviewed = zero).
    *Applied: §3, §4, risk table.*
11. **Spaced-repetition export (Anki/CSV)** for retention outcomes. *Applied: §6, scope, M1,
    task -srs-001.*
12. **Pilot outcomes study design** (pre/post can-do, consented cohort, baseline+target).
    *Applied: §4, §9 M2, task -pilot-001 / -outcomes-001.*
13. **Content schema validated in CI** (every unit: CEFR tag, provenance, reviewer sign-off, no
    open flags). *Applied: §6, §8, task -schema-001.*
14. **Licence/provenance CI gate that fails the build.** *Applied: §6, §7, metric 4, task
    -license-gate-001.*
15. **Source allow-list with per-source licence verification + snapshot hashes.** *Applied: §7,
    task -sources-001.*
16. **Cultural-notes review gate** (avoid stereotype/appropriation). *Applied: §8, §11, risk table.*
17. **Terminology standard anchored to authoritative references** (foclóir.ie/téarma.ie), reuse
    verified. *Applied: §6, §7, M1, task -glossary-001.*
18. **"Not official / not a replacement for teachers/immersion" framing on every rendering.**
    *Applied: §2 non-goals, §7, risk table.*
19. **Community advisory with Gaeltacht/native-speaker representation** (non-extractive
    governance). *Applied: §11, risk table, open questions.*
20. **Sustainability: maintainer + reviewer rotation + source re-verification + link-rot watcher +
    consent-withdrawal procedure.** *Applied: §15, M1/M3, task -watcher-001 / -maint-001.*
21. **IPA + per-dialect pronunciation field per core item** (precise, reviewable). *Applied: §6
    schema, scope.*
22. **Measurable per-milestone exit criteria** (concrete artefacts/counts, not vague goals).
    *Applied: §9.*
23. **Explicit "no scraping copyrighted broadcasters/textbooks" rule with named examples.**
    *Applied: §3, §7 exclusions, non-goals, risk table.*
24. **Metrics baseline table with honest "n/a (pre-pilot)" baselines + first-window targets + an
    outcomes log.** *Applied: §4, §15.*
25. **Lane-boundary clarity** (donated-only v0.1; bounded, budget-capped funded use deferred; paid
    voice talent is human work, not API spend). *Applied: §6 non-goals, §12, §14, §15, backlog.*

## Review sign-off

A completeness/correctness review was performed on the revised plan and tasks:

- **Metrics measurable?** Yes — §4 gives 8 outcome metrics with honest baselines (`n/a (pre-pilot)`
  / 0) and first-window targets; an outcomes log (§15) tracks them. Vanity metrics explicitly
  rejected.
- **Gates enforceable?** Yes — three CI gates (schema, licence/provenance, a11y) plus the human
  review gate; licence/provenance gate fails the build; Definition of Shipped requires real
  adoption.
- **Risks owned + mitigated?** Yes — §13 table has Likelihood/Impact/Mitigation/Owner for 11 risks,
  including the headline accuracy, dialect, licence, and privacy risks.
- **Licence / PII / expert-review guardrails present?** Yes — §7 (allow-list, snapshot hashes,
  conservative exclusion, no scraping, voice-as-PII, adults-only, de-identified pilot data) and §8
  (native-speaker sign-off + second reviewer for high-risk items) satisfy Hee-Lee Oss guardrails for a
  medium-risk minority-language project.
- **Sequencing sound?** Yes — M0 is partner-independent (policy, schema, gates, one reviewed unit);
  M1 makes it repeatable + recruits reviewers; M2 requires a secured partner (`verifiedNeed` flips
  to `true`); M3 scales. A go/pivot/hold decision point sits at end of M1.
- **Tasks schema-valid?** Yes — all required fields present and enum values valid; the example Task
  JSON in TASKS.md was checked field-by-field against `packages/schema/src/schemas.ts`
  (`verifiedNeed: false`, no partner; `outputLicense: MIT` for tooling).
- **Fixes made during review:** clarified that the example task's licence is MIT (tooling, not Irish
  content, which is CC BY-SA 4.0); added the explicit go/pivot/hold decision point to M2 partner
  task; ensured every "TO BE SECURED / TO VERIFY" item is flagged rather than assumed.

**Outstanding human decisions:** secure a partner + pilot cohort (blocks M2); verify per-source
licences (Common Voice release, ABAIR/TTS redistribution, foclóir.ie/téarma.ie reuse); decide
reviewer compensation model; name a permanent maintainer and steward.
