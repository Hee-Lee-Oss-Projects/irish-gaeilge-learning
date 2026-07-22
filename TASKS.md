# TASKS — irish-gaeilge-learning

> Status: Draft · Version: 0.1.0 · Last updated: 2026-06-28 · Owner: TBD (acting maintainer: J. Carter) · Lane: donated

The backlog for the `irish-gaeilge-learning` good-deed project. Read alongside
[PLAN.md](./PLAN.md). Milestones (M0–M3) match the roadmap there.

## How these tasks map to Hee-Lee Oss

Each task below becomes an **Hee-Lee Oss Task JSON** validated against
`packages/schema/src/schemas.ts`. Field mapping:

- **id** — stable slug id, e.g. `irish-gaeilge-learning-policy-001` (table column `ID`).
- **title** — the task title.
- **project** — always `irish-gaeilge-learning`.
- **type** — one of `code | research | writing | data | design-spec | maintenance` (table `Type`).
- **lane** — `donated` for all current tasks (no funded/API execution in v0.1). Any funded task
  would require `fundedBudgetUsd`; none here.
- **priority** — `high | medium | low`.
- **domain** — array, e.g. `["language-learning","irish","education","accessibility"]`.
- **riskTier** — `low | medium | high`. Any task that authors, reviews, or publishes **Irish
  content/audio is medium** (needs a qualified native-speaker reviewer); pure tooling/process/
  licensing tasks are **low** (table `Risk`). No task is `high` (no medical/legal/safety advice).
- **urgent** — boolean (default `false`; no live emergency).
- **deliverable** — `pr | dataset | document | translation` (table `Deliverable`). Course content
  units are delivered as `pr` (content-as-data merged to the repo); reference lists/manifests as
  `dataset`; policy/checklists/runbooks as `document`. (`translation` is unused — this project
  teaches a language rather than translating a fixed source text.)
- **tokenEstimate** — `small | medium | large` (table `Size`).
- **status** — `open | in-progress | review | delivered | done` (all start `open`).
- **context / objective** — why + what.
- **acceptanceCriteria[]** — checkable bullets (listed below tables for key tasks).
- **resources[]** — links/paths (allow-list, schema, source URLs, templates).
- **output** — path/description of the produced artefact.
- **requestor** — partner/requestor; `TO BE SECURED` until a partner is confirmed.
- **verifiedNeed** — boolean; **`false`** wherever value depends on an unsecured partner/cohort.
- **outputLicense** — **MIT** for code/tooling; **CC BY-SA 4.0** for original course content;
  **source-compatible** licence for any third-party asset (e.g. CC0 audio stays CC0 with
  attribution). Never a relicense of third-party material.

---

## Milestone M0 — Foundation & cold-start (no partner required)

Goal: lock policy, stand up the schema + gates + review machinery, and prove the whole pipeline on
**one fully reviewed A1 unit with dialect-labelled audio**. All M0 deliverables carry
`verifiedNeed: false`.

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
|---|---|---|---|---|---|---|---|
| irish-gaeilge-learning-policy-001 | Dialect-parity + standard policy + CEFR/TEG mapping doc (with non-accreditation disclaimer) | writing | small | low | document | — | Maintainer / Qualified reviewer |
| irish-gaeilge-learning-sources-001 | Source allow-list with per-source licence terms + snapshot hashes | data | small | low | dataset | — | Maintainer / Licence reviewer |
| irish-gaeilge-learning-schema-001 | Content schema (unit/item/exercise/review/provenance) + CI structural gate | code | medium | low | pr | policy-001 | Maintainer |
| irish-gaeilge-learning-license-gate-001 | Licence/provenance CI gate (build fails if any asset lacks verified licence/provenance) | code | small | low | pr | sources-001, schema-001 | Maintainer / Licence reviewer |
| irish-gaeilge-learning-audio-001 | Audio provenance + consent/performer-release manifest schema + template | design-spec | small | low | document | sources-001 | Maintainer / Licence reviewer |
| irish-gaeilge-learning-reviewers-001 | Reviewer checklist + qualification criteria + handoff template (COI/independence; 2nd-reviewer rule) | writing | small | low | document | policy-001 | Maintainer |
| irish-gaeilge-learning-unit-001 | First A1 unit (≥15 core items) drafted + native-speaker reviewed, dialect-labelled audio, published | writing | medium | medium | pr | policy-001, schema-001, license-gate-001, audio-001, reviewers-001 | Qualified reviewer (+2nd for pronunciation/mutation) |
| irish-gaeilge-learning-render-001 | Static-site renderer for units + a11y baseline checklist | code | medium | low | pr | schema-001 | Maintainer |

**Acceptance criteria — key M0 tasks**

`policy-001` (dialect + level policy)
- States the **locked dialect-parity rule**: An Caighdeán Oifigiúil for spelling/grammar; audio in
  **all three dialect groups (Munster/Connacht/Ulster) with explicit labels**; **no dialect ranked
  as more correct**; how divergent dialect forms are surfaced without implying error.
- Includes a **CEFR → TEG mapping table** (A1/A2/B1 to the corresponding TEG bands) and a verbatim
  **non-accreditation disclaimer** ("aligned to CEFR / mapped to TEG; not an official TEG,
  Department of Education, or Foras na Gaeilge product; no certificate is issued") to appear on
  every rendering.
- Reviewed by a qualified native-speaker reviewer for accuracy of the dialect/standard claims.

`sources-001` (allow-list)
- `sources/allow-list.yaml` lists ≥ 3 sources including **at least one CC0 audio/sentence source**
  (e.g. Mozilla Common Voice Irish) and one text source (e.g. Irish Wiktionary, CC BY-SA), each
  with: name, canonical URL, version/date, retrieval date, licence name + URL, **snapshot of licence
  text (SHA-256 `snapshotHash` + archive URL)**, derivatives-allowed flag, required attribution
  string, and usage restrictions.
- Each entry records `verifiedBy` + `verifiedDate`; any source with unclear/ND/non-redistributable
  terms (e.g. reference-only dictionaries, non-redistributable TTS, any broadcaster/textbook
  material) is marked **excluded** with a reason.
- File validates and passes CI structural checks.

`unit-001` (first A1 unit — the cold-start proof)
- One A1 unit (theme e.g. *Beannú / greetings & introductions*) with **≥ 15 core items**, each with
  `irishStandard`, `english`, `ipa`, per-dialect `dialectNotes`, and ≥ 3 typed exercises with answer
  keys + rationale.
- **Audio in all three dialect groups** for ≥ 90% of core items, each with a **complete provenance/
  consent manifest entry** (CC0 corpus clip, or new recording with signed consent + performer
  release; **adult speakers only**); no audio without provenance.
- Drafted by the agent (English scaffolding + proposed Irish); **agent `UNCERTAIN:` flags recorded**;
  **no sign-off while any flag is unresolved**.
- **Qualified native-speaker reviewer sign-off recorded in the PR**, reviewer independent of
  drafting; a **second independent reviewer** signs off on **pronunciation, initial mutations
  (séimhiú/urú), the copula, and any negation**, with a **back-translation/reverse-check QA pass**.
- Passes CI: schema structural gate **and** licence/provenance gate **and** a11y baseline checklist.
- Carries the non-accreditation disclaimer; `outputLicense: CC BY-SA 4.0` for authored content
  (audio per its source licence).

`license-gate-001` (CI licence/provenance gate)
- CI step validates that **every text and audio asset** in a unit has a verified licence,
  attribution, and provenance entry referencing an **allow-listed** source (or a consented new
  recording); the **build fails** if any is missing or if the output licence is incompatible with a
  source. This makes metric 4 ("100% licence/provenance") a hard, automated gate.

**M0 Definition of Done:** dialect/level policy + CEFR/TEG mapping (with disclaimer) merged; source
allow-list (≥ 3 verified sources incl. one CC0 audio source, each with snapshot hash) merged;
content schema + audio/consent manifest + **CI structural and licence/provenance gates green**;
reviewer checklist + qualification criteria + handoff template merged; **one A1 unit** reviewed
(two reviewers for high-risk items), with provenance-verified dialect-labelled audio, **published
via the renderer and passing the a11y checklist**. Partner/pilot deferred to M2 (all M0 deliverables
`verifiedNeed: false`).

---

## Milestone M1 — Repeatability & reviewer network

Goal: make the pipeline repeatable; recruit/qualify reviewers; complete the A1 module; ship
offline + SRS exports + a11y conformance. **Steward named** (governance prerequisite for M2).

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
|---|---|---|---|---|---|---|---|
| irish-gaeilge-learning-reviewers-002 | Recruit/qualify ≥2 reviewers (or a community/university partner) | research | medium | low | document | reviewers-001 | Maintainer / Steward |
| irish-gaeilge-learning-glossary-001 | Terminology/glossary standard anchored to authoritative references (reuse verified) | data | small | medium | dataset | sources-001, policy-001 | Qualified reviewer |
| irish-gaeilge-learning-module-a1-001 | Complete A1 module (≥6 units) reviewed + published | writing | large | medium | pr | unit-001 | Qualified reviewers (+2nd for high-risk) |
| irish-gaeilge-learning-offline-001 | Offline / low-bandwidth pack builder (HTML+audio+transcripts) | code | medium | low | pr | render-001 | Maintainer |
| irish-gaeilge-learning-srs-001 | Spaced-repetition export (Anki/CSV) from content schema | code | small | low | pr | schema-001 | Maintainer |
| irish-gaeilge-learning-a11y-001 | WCAG 2.2 AA conformance pass across published units | code | small | low | pr | render-001, module-a1-001 | Maintainer / a11y reviewer |
| irish-gaeilge-learning-watcher-001 | Source-change / link-rot watcher (re-fetch, re-hash, flag drift) | code | small | low | pr | sources-001 | Maintainer |
| irish-gaeilge-learning-runbook-001 | End-to-end pipeline runbook (draft → review → publish) | writing | small | low | document | unit-001, license-gate-001 | Maintainer |

**Acceptance criteria — key M1 tasks**

`reviewers-002`
- ≥ 2 qualified reviewers (native/near-native + teaching/linguistic competence) **or** a community/
  university partner committed to supply review capacity; COI + independence declarations on file;
  the **second-reviewer rule** for pronunciation/mutation/negation and the **disagreement →
  conservative-reading → escalation** rule documented and agreed.
- A **go / pivot / hold** decision point is recorded: if **no partner or reviewer base is secured by
  end of M1**, the maintainer makes an explicit decision before scaling content.

`module-a1-001`
- A complete A1 module of **≥ 6 units** covering the A1 can-do statements, each meeting the
  `unit-001` quality bar (review, dialect audio, provenance, exercises, a11y).
- Dialect parity target met for ≥ 90% of A1 core items; non-accreditation disclaimer present.
- All units pass schema + licence/provenance + a11y CI gates.

`glossary-001`
- A terminology standard mapping course vocabulary to **authoritative reference forms** (e.g.
  foclóir.ie / téarma.ie) — used to *check* spelling/terminology, **not copied** unless the dataset
  licence explicitly permits reuse (verified and recorded in the allow-list).
- Reviewed by a qualified reviewer for the standard/dialect distinctions.

`a11y-001`
- Published units meet **WCAG 2.2 AA**: audio has transcripts + captions, images have alt text,
  keyboard-navigable, sufficient contrast, dyslexia-friendly typography option; documented
  checklist passes in CI.

**M1 Definition of Done:** ≥ 2 reviewers (or partner) engaged with COI/independence/second-reviewer
rules documented; terminology standard merged; **full A1 module (≥ 6 units) reviewed + published**;
**offline pack + SRS export working**; **WCAG 2.2 AA** across published units; source-change/link-rot
**watcher operating**; pipeline runbook merged; **Steward named**.

---

## Milestone M2 — First partner & pilot (needs partner)

Goal: secure a partner + a consenting adult learner cohort; run a pre/post can-do pilot; deliver +
confirm adoption. **All tasks gated on a secured partner** (`verifiedNeed` flips to `true` only when
confirmed).

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
|---|---|---|---|---|---|---|---|
| irish-gaeilge-learning-partner-001 | Secure first partner + adult pilot cohort; agree scope + consent | research | medium | low | document | reviewers-002 | Steward / Maintainer |
| irish-gaeilge-learning-pilot-001 | Run A1 pilot with pre/post can-do measurement (consented, de-identified) | research | medium | medium | document | partner-001, module-a1-001 | Steward / Qualified reviewer |
| irish-gaeilge-learning-outcomes-001 | Publish aggregated/de-identified outcome report vs. PLAN metrics | writing | small | low | document | pilot-001 | Steward |

**Acceptance criteria — key M2 tasks**

`partner-001`
- Outreach (owned by acting maintainer → Steward) targets named candidate types (Conradh na
  Gaeilge, Glór na nGael, Gaeltacht co-ops/Údarás na Gaeltachta, TEG/Lárionad na Gaeilge, Oideas
  Gael, Gaeloideachas, diaspora cultural centres), aiming for **≥ 3 serious conversations by end of
  M1**.
- A named partner/requestor confirmed **in writing**; agreed first scope (A1) and an **adult**
  learner cohort with **informed consent** for minimal pre/post measurement; reviewer coverage
  confirmed. On completion, related tasks update `requestor` and `verifiedNeed: true`.
- **Pause/decision point:** if no partner is secured by end of M1, an explicit **go/pivot/hold**
  decision is made before pilot work proceeds.

`pilot-001`
- Pilot runs with the consented adult cohort using the A1 module; **pre/post can-do assessment**
  administered; learner data is **minimal, consented, de-identified**, with retention/deletion
  honoured; no person-level data published.

`outcomes-001`
- Aggregated/de-identified report against §4 metrics (attainment, completion, defects, dialect
  coverage, adoption, a11y); partner confirms adoption **in writing** (first true **Definition of
  Shipped** event).

**M2 Definition of Done:** partner secured (`verifiedNeed=true`); A1 module **delivered to and used
by** a consented adult cohort/partner; pre/post outcomes measured and published (de-identified);
partner adoption confirmed in writing.

---

## Milestone M3 — Scale (A2 + dialect breadth + sustained outcomes)

Goal: extend to A2, broaden dialect audio coverage, sustain quality + outcome tracking.

| ID | Title | Type | Size | Risk | Deliverable | Depends on | Reviewer |
|---|---|---|---|---|---|---|---|
| irish-gaeilge-learning-module-a2-001 | A2 module(s) reviewed + published (dialect parity maintained) | writing | large | medium | pr | module-a1-001, outcomes-001 | Qualified reviewers (+2nd for high-risk) |
| irish-gaeilge-learning-rotation-001 | Reviewer rotation + load balancing | maintenance | small | low | document | reviewers-002 | Maintainer |
| irish-gaeilge-learning-maint-001 | Source re-verification + audio/link maintenance cadence + consent-withdrawal procedure | maintenance | small | low | document | watcher-001 | Maintainer |
| irish-gaeilge-learning-outcomeslog-001 | Standing outcomes log (adoption, attainment, defects, reuse) | data | small | low | dataset | outcomes-001 | Steward |

**Acceptance criteria — key M3 tasks**

`maint-001`
- Documented cadence to re-verify allow-list source licences (via stored snapshots) and refresh
  audio/links; a **withdrawal procedure** to remove any asset whose licence changes to forbid reuse
  **or whose speaker withdraws consent**.

`outcomeslog-001`
- A maintained log capturing, per published module/cohort: adoption status, attainment/completion,
  post-publication critical defects (target 0), and documented teacher reuse; feeds PLAN §4 metrics.

**M3 Definition of Done:** A2 module(s) reviewed/published with dialect parity; reviewer rotation
operating; source/audio maintenance cadence + consent-withdrawal procedure in effect; outcomes log
live; named sustainability owner.

---

## Backlog / future

Sized but unscheduled:

- **(large) B1 module** — extend scope to CEFR B1 once A1/A2 outcomes justify it.
- **(medium, possibly funded — needs escrow) New native-speaker recording sessions** — commission
  clean, dialect-balanced, item-level audio with **signed consent + performer release** and **paid/
  credited speakers**. Recording is **human work**; any funded-lane spend would be a bounded
  alignment/transcription/normalisation compute job under a **hard `fundedBudgetUsd` cap**, never
  the recording itself. Out of scope for v0.1.
- **(medium) Teacher adaptation kits** — editable lesson plans + printable handouts wrapping the OER.
- **(medium) Additional accessible formats** — braille-ready text, large-print, audio-only course.
- **(medium) Children's track** — only with a guardian-consent + minors'-data framework (currently
  a non-goal; adults-only in v0.1).
- **(large) Pronunciation practice with feedback** — only if a licence-clear, reviewed open Irish
  speech model exists; separately risk-assessed.
- **(small) Common Voice contribution loop** — contribute reviewed sentences back to the CC0 corpus
  (give-back to the commons), pending licence/consent review.

---

## Example task JSON

Schema-valid Task JSON for the first M0 task. `verifiedNeed` is **false** (no partner/cohort
secured); `outputLicense` is **MIT** because this deliverable is **project tooling/policy metadata**,
not Irish course content (course content ships under **CC BY-SA 4.0**).

```json
{
  "id": "irish-gaeilge-learning-policy-001",
  "title": "Dialect-parity + standard policy and CEFR/TEG mapping document",
  "project": "irish-gaeilge-learning",
  "type": "writing",
  "lane": "donated",
  "priority": "high",
  "domain": ["language-learning", "irish", "education", "linguistics", "policy"],
  "riskTier": "low",
  "urgent": false,
  "deliverable": "document",
  "tokenEstimate": "small",
  "status": "open",
  "context": "irish-gaeilge-learning builds a free, openly-licensed, CEFR/TEG-aligned course for learning Irish (Gaeilge), spoken and written, to support language revitalization. Irish has three living dialect groups (Munster, Connacht, Ulster) alongside An Caighdean Oifigiuil (the official written standard). A course must take a principled, documented stance before any content is authored, or it will implicitly privilege one dialect and alienate speaker communities. The project is medium risk (language accuracy + cultural fidelity); this foundational policy task is itself low risk (process/policy), but is reviewed by a native-speaker reviewer for accuracy of its dialect/standard claims.",
  "objective": "Write the locked dialect-parity and written-standard policy and the CEFR-to-TEG level mapping, including a verbatim non-accreditation disclaimer, to govern all subsequent content authoring and review.",
  "acceptanceCriteria": [
    "States the dialect-parity rule: An Caighdean Oifigiuil for spelling/grammar; audio in all three dialect groups (Munster/Connacht/Ulster) with explicit labels; no dialect ranked as more correct",
    "Defines how divergent dialect forms are surfaced without implying any form is an error",
    "Includes a CEFR to TEG mapping table (A1/A2/B1 to the corresponding TEG bands)",
    "Includes a verbatim non-accreditation disclaimer (aligned to CEFR / mapped to TEG; not an official TEG, Department of Education, or Foras na Gaeilge product; no certificate issued) to appear on every rendering",
    "Reviewed and signed off by a qualified native/near-native Irish reviewer for accuracy of dialect/standard claims; reviewer COI declared",
    "Document validates against repo docs conventions and is referenced by the content schema task"
  ],
  "resources": [
    "C:/code/hee-lee-oss/planning/projects/irish-gaeilge-learning/PLAN.md",
    "C:/code/hee-lee-oss/CLAUDE.md",
    "CEFR level descriptors / can-do statements",
    "TEG (Teastas Eorpach na Gaeilge) level descriptors, Maynooth University",
    "An Caighdean Oifigiuil (2017) reference"
  ],
  "output": "docs/policy/dialect-and-levels.md plus a CEFR-TEG mapping table, referenced by the content schema",
  "requestor": "TO BE SECURED",
  "verifiedNeed": false,
  "outputLicense": "MIT"
}
```
