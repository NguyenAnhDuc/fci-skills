---
name: docsmith
version: 1.0.0
description: "Create documentation following PRC-010 process. Use when asked to create, draft, or plan documentation for a product or project. Guides through audience analysis, documentation planning, sitemap creation, UX content standards, drafting, self-review, and product walkthrough."
author: fpt-smartcloud
license: MIT
repository: https://github.com/fpt-smartcloud/docsmith
keywords:
  - documentation
  - technical-writing
  - docs-for-developers
  - ux-writing
  - content-strategy
  - prc-010
categories:
  - documentation
  - writing
  - quality-assurance
disable-model-invocation: true
argument-hint: "[command] [product-name]"
---

# Docsmith — PRC-010: Documentation Creation Process

Standardized process for systematically creating, reviewing, and publishing documentation. Based on *Docs for Developers* (Bhatti et al., 2021) and *Strategic Writing for UX* (Podmajersky, 2019).

## Commands

Parse `$ARGUMENTS` to determine which command to run. If no command is given or the command is `help`, show the command reference table below.

| Command | Alias | Owner | Description |
|---------|-------|-------|-------------|
| `help` | `h` | — | Show this command reference |
| `start` | — | — | Begin the full process from the first human step |
| `audience` | `aud` | Human | Define audience and goals → Audience Profile |
| `plan` | `pl` | **AI** | Create documentation plan + traceability matrix |
| `review-plan` | `rp` | Human | Review and approve the documentation plan |
| `sitemap` | `sm` | **AI** | Create sitemap (folder structure, navigation, cross-links) |
| `voice` | `vc` | **AI** | UX content standards (voice chart, text patterns, scorecard) |
| `draft` | `dr` | **AI** | Draft documentation using content type templates |
| `edit` | `ed` | **AI** | Self-review edit (5 passes) |
| `walkthrough` | `wt` | **AI** | Product walkthrough (browser verification + screenshots) |
| `validate` | `val` | **AI** | Run walkthrough test cases only (no screenshots, no doc fixes) |
| `test` | `t` | **AI** | Create or update walkthrough test cases from existing docs |
| `verify` | `vf` | **AI** | Run all verification checks (edit passes + voice score + link/placeholder audit). Accepts optional doc path or glob to scope to one area. |
| `peer-review` | `pr` | Human | Peer review |
| `tech-review` | `tr` | Human | Technical review (optional) |
| `incorporate` | `inc` | **AI** | Incorporate review feedback into documents |
| `publish` | `pub` | Human | Approve and publish |

### Examples

```
/doc-create help
/doc-create start MyProduct
/doc-create plan MyProduct
/doc-create draft MyProduct
/doc-create validate MyProduct
/doc-create test MyProduct
/doc-create wt MyProduct
/doc-create verify MyProduct
/doc-create verify MyProduct docs/drafts/getting-started.md
/doc-create verify MyProduct docs/drafts/api-*
```

## Process Flow

```
audience (Human) → plan (AI) → review-plan (Human) → sitemap (AI) → voice (AI) → draft (AI) → edit (AI) → walkthrough (AI) → peer-review (Human) → [tech-review (Human, optional)] → incorporate (AI) → publish (Human)
```

**Decision points:**
- After `review-plan`: Plan approved? No → back to `plan`
- After `peer-review`: Passes review? No → back to `draft`
- After `peer-review`: Technical review needed? Yes → `tech-review` → `incorporate`

## Command Details

### `help`
Display the command reference table above. No other action.

### `start`
Begin the process. Explain that the first step (`audience`) is human-owned, show what needs to be done, and provide the audience profile template.

### `audience` (Human)
Provide the user with:
1. Instructions for defining audience and goals (gather existing knowledge, define user goals, identify target users, outline user needs, identify competitors, condense findings into personas and user stories)
2. The template: [templates/AUDIENCE_PROFILE_TEMPLATE.md](templates/AUDIENCE_PROFILE_TEMPLATE.md)
3. Ask user to provide the completed profile or answer questions interactively

### `plan` (AI)
**Requires**: Completed audience profile
Read [process-reference.md](process-reference.md) § STEP-002. Use templates:
- [templates/DOCUMENTATION_PLAN_TEMPLATE.md](templates/DOCUMENTATION_PLAN_TEMPLATE.md)
- [templates/TRACEABILITY_MATRIX_TEMPLATE.md](templates/TRACEABILITY_MATRIX_TEMPLATE.md)

### `review-plan` (Human)
Present the documentation plan for human review. Explain approval criteria:
- Plan covers all critical user journeys
- Content types are appropriate
- Priorities are clear
Ask if approved or if feedback is needed (→ re-run `plan` with feedback).

### `sitemap` (AI)
**Requires**: Approved documentation plan
Read [process-reference.md](process-reference.md) § STEP-004. Define folder structure, navigation sidebar, cross-links, and reading order.

### `voice` (AI)
**Requires**: Approved documentation plan + audience profile
Read [subprocess-010a.md](subprocess-010a.md). Use templates:
- [templates/VOICE_CHART_TEMPLATE.md](templates/VOICE_CHART_TEMPLATE.md)
- [templates/UX_TEXT_PATTERNS_TEMPLATE.md](templates/UX_TEXT_PATTERNS_TEMPLATE.md)
- [templates/UX_CONTENT_SCORECARD_TEMPLATE.md](templates/UX_CONTENT_SCORECARD_TEMPLATE.md)

Runs the subprocess: define product principles (ask human) → build voice chart → review (ask human) → define UX text patterns → create content scorecard → approve (ask human).

### `draft` (AI)
**Requires**: Approved plan, sitemap, voice chart, UX text patterns
Read [process-reference.md](process-reference.md) § STEP-005. Use templates from:
- [templates/CONTENT_TYPE_TEMPLATES.md](templates/CONTENT_TYPE_TEMPLATES.md)

Draft each document in the plan. Use `![Caption](https://placehold.co/600x400)` for screenshot placeholders.

### `edit` (AI)
**Requires**: Draft documents
Read [process-reference.md](process-reference.md) § STEP-006. Perform 5 editing passes:
1. Technical accuracy
2. Completeness
3. Structure
4. Clarity and brevity
5. Voice compliance (score with content scorecard, minimum 70% to pass)

### `walkthrough` (AI) — Full walkthrough
**Requires**: Edited documents + live product access
Read [process-reference.md](process-reference.md) § STEP-007 and [tools-reference.md](tools-reference.md). Full workflow:
1. Create test cases from docs → [templates/WALKTHROUGH_TEST_CASE_TEMPLATE.md](templates/WALKTHROUGH_TEST_CASE_TEMPLATE.md)
2. Create screenshot capture plan
3. Execute test cases + capture screenshots in single browser pass
4. Replace all `placehold.co` placeholders with captured images
5. Fix any doc failures found
6. Record results → [templates/WALKTHROUGH_TEST_EXECUTION_TEMPLATE.md](templates/WALKTHROUGH_TEST_EXECUTION_TEMPLATE.md)
7. Verify zero `placehold.co` references remain

### `validate` (AI) — Verification only
**Requires**: Existing test cases + live product access
Run existing walkthrough test cases against the live product **without** modifying documentation or capturing screenshots. Purpose: quick re-check after product changes.
1. Read existing test cases from `docs/walkthrough/test-cases/`
2. Execute each test case against the live product using [tools-reference.md](tools-reference.md)
3. Record pass/fail results → [templates/WALKTHROUGH_TEST_EXECUTION_TEMPLATE.md](templates/WALKTHROUGH_TEST_EXECUTION_TEMPLATE.md)
4. Report failures with details (expected vs actual) but do NOT auto-fix docs
5. Recommend next steps for any failures

### `test` (AI) — Create/update test cases
**Requires**: Existing documentation
Extract verifiable claims from documentation and generate test cases. Does NOT execute them.
1. Scan all docs for verifiable claims (UI labels, navigation paths, URLs, procedures, API behaviors)
2. Generate test cases → [templates/WALKTHROUGH_TEST_CASE_TEMPLATE.md](templates/WALKTHROUGH_TEST_CASE_TEMPLATE.md)
3. Generate screenshot capture plan for any `placehold.co` placeholders
4. Save to `docs/walkthrough/test-cases/`
5. Report coverage summary by category

### `verify` (AI) — Comprehensive verification

**Requires**: Draft or edited documents. Optionally: voice chart, UX text patterns, content scorecard.

Run all verification checks on the entire documentation set or a specific subset. This is a standalone quality gate that combines all automated checks from `edit`, `voice`, and structural audits into a single pass.

**Scope**: Pass an optional file path or glob pattern after the product name to limit verification to specific docs. If omitted, verifies all docs.

```
/doc-create verify MyProduct                              # all docs
/doc-create verify MyProduct docs/drafts/getting-started.md  # single doc
/doc-create verify MyProduct docs/drafts/api-*               # glob pattern
```

**Checks performed** (in order):

| # | Check | Source | Action on Failure |
|---|-------|--------|-------------------|
| 1 | **Technical accuracy** — instructions produce promised results, jargon explained, names correct | `edit` pass 1 | List issues with file:line references |
| 2 | **Completeness** — no `[TODO]`/`[TBD]` remaining, all environments covered, version limits noted | `edit` pass 2 | List gaps |
| 3 | **Structure** — follows content type template, headers logical, prerequisites/next-steps present | `edit` pass 3 | List deviations |
| 4 | **Clarity & brevity** — no unnecessary words, consistent terms, no idioms/biased language | `edit` pass 4 | List suggestions |
| 5 | **Voice compliance** — score against voice chart using content scorecard (min 70%) | `edit` pass 5 | Report score per doc |
| 6 | **Link audit** — all internal cross-references resolve, no broken links | structural | List broken links |
| 7 | **Placeholder audit** — search for `placehold.co`, `[TODO]`, `[TBD]`, `[PLACEHOLDER]` | structural | List remaining placeholders with locations |
| 8 | **Traceability check** — every doc maps to a user story, no orphan docs, no uncovered stories | plan | Report gaps |
| 9 | **Sitemap consistency** — docs match sitemap paths, navigation order intact | plan | List mismatches |
| 10 | **Template compliance** — each doc follows its declared content type template structure | structural | List missing sections |

**Output**:
- Verification report saved to `docs/walkthrough/verify-report-[YYYY-MM-DD].md`
- Summary table: check name, status (pass/warn/fail), issue count
- Per-doc breakdown if scoped to multiple files
- Overall pass/fail verdict (pass = zero failures, warnings OK)
- If voice chart/scorecard exist, include per-doc voice scores

**Does NOT**:
- Modify any documentation (read-only)
- Execute browser-based walkthrough (use `walkthrough` or `validate` for that)
- Capture screenshots

### `peer-review` (Human)
Provide the user with:
1. What kind of feedback to give (structural, technical, clarity)
2. How to provide feedback
3. After feedback received, ask: approved? → `publish` or `tech-review`. Not approved? → back to `draft`.

### `tech-review` (Human)
Explain when technical review is needed (multi-system integrations, unfamiliar domains, safety-critical). Ask user to provide SME feedback.

### `incorporate` (AI)
**Requires**: Review feedback
Read [process-reference.md](process-reference.md) § STEP-010. Process feedback one reviewer at a time, prioritize what helps the user most for contradictions.

### `publish` (Human)
Provide the user with a publication checklist:
1. Final sign-off on content quality
2. Coordinate with code/product release if applicable
3. Publish to documentation platform
4. Announce to users

## File Organization

All documentation outputs should be saved under a project-specific directory:
```
docs/
├── plan/
│   ├── audience-profile.md
│   ├── documentation-plan.md
│   ├── traceability-matrix.md
│   └── sitemap.md
├── standards/
│   ├── voice-chart.md
│   ├── ux-text-patterns.md
│   └── content-scorecard.md
├── drafts/
│   └── [doc-name].md
├── walkthrough/
│   ├── test-cases/
│   └── executions/
└── images/
```
