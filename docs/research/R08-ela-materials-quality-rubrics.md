---
id: R08
question: "What published quality criteria for ELA instructional materials (e.g. state or independent review rubrics) could act as a review checklist?"
asked_in: specs/M1-lesson-generation-review/brief.md#research-questions
unblocks: "approval checklist FRs, SM-02"
answered_when: "an official or widely used rubric read"
status: partial
confidence: medium
supersedes: none
date: 2026-10-14
budget: 13/15 tool calls
researched_by: Claude Code, claude-opus-5-5
---

# R08 Published ELA materials quality rubrics usable as a review checklist

## Answer

Three published rubrics fit:

1. **California's own criteria** (Tier A, and the ones that apply to the CA adoption). These are the five evaluation categories in chapter 12 of the 2014 ELA/ELD Framework: standards alignment, program organization, assessment, universal access, and instructional planning and teacher support. Category 1 must be fully met.
2. **EdReports' three gateways:** text quality and complexity, building knowledge, and usability. Its indicators include, for example, "Most questions, tasks, and assignments are text-specific".
3. **Student Achievement Partners' tools.** These are the IMET, with ELA non-negotiables such as text complexity, text-dependent questions and writing to sources, and the EQuIP rubric for lessons and units.

Confidence: medium, because all three were read in Tier-A form, but only in older versions: EdReports' 2016 legacy guide and SAP's 2014 webinar. The current EdReports v2.0 and IMET v3 wording was not read. (S01.5, S08.1, S08.2, S08.3)

## Takeaway

California's adoption criteria, EdReports' gateways and the IMET/EQuIP rubrics are the standard public yardsticks for judging ELA curriculum. Each one breaks "good" into named, checkable criteria that a reviewer could tick off.

## Findings

- **F1** [LB] California evaluates K–8 ELA/ELD instructional materials in five categories: (1) ELA and ELD Content/Alignment with the Standards, (2) Program Organization, (3) Assessment, (4) Universal Access, and (5) Instructional Planning and Teacher Support. — S01.5 (A), "Criteria for Instructional Materials Aligned to the Standards"
- **F2** [LB] Materials that fail Category 1 "will not be considered suitable for adoption". All Category 1 criteria for the program type must be met in core materials. Programs "must have strengths in each of categories 2 through 5". — S01.5 (A), category overview
- **F3** [LB] Category 1 includes concrete criteria: proper grammar and spelling (EC 60045), high-quality reading selections, and incorporating the Framework's five themes (Meaning Making, Language Development, Effective Expression, Content Knowledge, Foundational Skills). Category 2 includes 180 days of content and a scope and sequence aligned to the standards. — S01.5 (A), Category 1 criteria 3, 6, 7; Category 2 criteria 1–2
- **F4** [LB] EdReports grades 6–8 ELA reports are organized as Gateway 1 "Text Quality and Complexity", Gateway 2 "Building Knowledge" and Gateway 3 "Usability". Ratings are Meets, Partially Meets and Does Not Meet Expectations. EdReports states its current review tool is v2.0. — S08.1 (A), report header and gateway summary
- **F5** [LB] The EdReports 3–8 ELA evidence guide (updated 2016-08-30) gives indicator-level criteria. Examples:
  - 1a: anchor texts are "of publishable quality and worthy of especially careful reading"
  - 1c: texts have appropriate grade-level complexity
  - 1g: "Most questions, tasks, and assignments are text-specific"
  - 1h: sequences of text-dependent questions build to a culminating task
  - 1i: protocols for evidence-based discussion
  - 1k: on-demand and process writing
  - 1n: explicit grammar and conventions instruction
  - 2a–2h: knowledge building, vocabulary and research projects
  — S08.2 (A), Indicators 1a–1q, 2a–2h
- **F6** [LB] Student Achievement Partners presents the IMET's ELA/Literacy non-negotiables as:
  - Complexity, Range and Quality of Texts
  - Text-Dependent and Text-Specific Questions
  - Scaffolding and Supports
  - Foundational Skills (grades 3–5)
  - Writing to Sources
  - Speaking and Listening
  - Language

  The IMET separates non-negotiable criteria from "alignment criteria and indicators of quality". — S08.3 (A), pp.9, 20–21 (2014)
- **F7** [LB] The same toolkit names the IMET as the tool for comprehensive curricula. It names the "EQuIP Rubric for Lessons and Units" for lesson plans and units of instruction in ELA/literacy. — S08.3 (A), p.8 "Types of Tools in the Toolkit"

## Inferences

- **I1** from F1 + F2 + F3: California's criteria judge whole programs, not single lessons. Applied per lesson, Category 1 (standards alignment, grammar and spelling, text quality) and Category 4 (access for English learners and other groups) map most directly. Categories 2, 3 and 5 are mostly unit- or program-level. Medium confidence.
- **I2** from F5 + F6: EdReports and IMET overlap heavily: text quality and complexity, text-dependent questions, evidence-based discussion and writing from sources. That overlap is the part both independent-style rubrics agree on. High confidence that they overlap; the exact current wording was not read.
- **I3** from F7: Of the rubrics read, EQuIP is the one aimed at a single lesson or unit, which is the grain a lesson reviewer works at. Its criteria themselves were not read. Low confidence.

## Gaps

- ⚠ What is the exact current EdReports ELA 6–8 v2.0 indicator wording? — why: only the 2016 legacy guide (S08.2) was read; v2.0 is current per S08.1 — would close it: read the ELA 6–8 v2.0 review tool and evidence guide on edreports.org
- ⚠ What is the full current IMET (Version 3, Aug 2015) ELA 3–12 text, and EQuIP's ELA criteria? — why: unread: https://achievethecore.org/aligned/wp-content/uploads/2015/08/IMET_Version3_ELA_3-12_August-2015.pdf and achievethecore.org/file/821 returned an HTML login/CAPTCHA page instead of the PDF — would close it: a human downloads them from achievethecore.org
- ⚠ Has the 2025 ELA/ELD Follow-Up Adoption Guidance (SBE, 2025-11-06) added criteria beyond chapter 12? — why: named in S01.4 but not read — would close it: read that guidance document on cde.ca.gov
- ⚠ Does Newsela use any of these rubrics internally? — why: partner material not read in this pass — would close it: ask the partner (R03)
- option: run anthropic-skills:deep-research for a broader sweep of other state rubrics (e.g. Louisiana, Texas IMRA)

## Handoffs

- write-prd: Should the approval checklist be built from California's chapter 12 categories, from the EdReports/IMET overlap, or from both, and which items apply per lesson rather than per unit? — rests on F1, F2, F5, F6, I1, I2
- write-prd: Is SM-02 measured against a named published rubric (which version), so the checklist can be cited? — rests on F4, F5, Gaps
- design-hld: Should checklist items be stored as versioned data with a source citation per item, so a rubric update does not need a code change? — rests on F4, F5
