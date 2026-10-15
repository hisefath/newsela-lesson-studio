---
id: R07
question: "How much of a copyrighted anchor text may lesson materials quote, and how do published curricula reference novels?"
asked_in: specs/M1-lesson-generation-review/brief.md#research-questions
unblocks: "FR on excerpts"
answered_when: "an authoritative fair-use or publisher-practice source"
status: answered
confidence: high
supersedes: none
date: 2026-10-14
budget: 11/15 tool calls
researched_by: Claude Code, claude-opus-5-5
---

# R07 Quoting a copyrighted anchor novel in lessons

## Answer

US law sets no safe word count: the Copyright Office says fair use is decided case by case on four factors, and the
1976 classroom guidelines (a floor for teachers copying in non-profit schools, at most 1,000 words or 10% of a prose
work, whichever is less) do not cover a commercial publisher and bar copying that substitutes for buying the book or
is directed by higher authority. Published curricula, including the partner's own sample outline, handle a novel like
*The Lightning Thief* by naming an edition (ISBN) and pointing lessons at chapters and page ranges while students read
their own or class copies, and they print only public-domain or short excerpts. Confidence: high, because every
load-bearing claim rests on Tier-A sources (U.S. Copyright Office, the partner's outline, a publisher's own unit).
(S07.1, S07.2, S05.2, S07.3)

## Takeaway

There is no magic number of words you may quote from a novel, so lesson materials point students to chapters and
pages in their own copy of the book instead of reprinting it.

## Findings

- **F1** [LB] Section 107 lists four fair-use factors: purpose and character (including commercial versus nonprofit educational use), nature of the work, amount and substantiality used, and effect on the market for the work — S07.1 (A), Circular 21 p.4, § 107
- **F2** [LB] The classroom-copying guidelines allow, for multiple classroom copies, a prose excerpt of not more than 1,000 words or 10% of the work, whichever is less, with a 500-word minimum; each copy needs a copyright notice — S07.1 (A), Circular 21 p.6, Agreement on Guidelines for Classroom Copying, Brevity ii
- **F3** [LB] The guidelines apply to not-for-profit educational institutions and state "the minimum and not the maximum standards of educational fair use"; they also require spontaneity (the individual teacher's own decision) and limit copying to two excerpts per author and nine instances per course per term — S07.1 (A), Circular 21 pp.6–7, Agreement preamble, Spontaneity, Cumulative Effect
- **F4** [LB] The guidelines prohibit copying that substitutes for anthologies or for the purchase of books, copying "directed by higher authority", and copying from consumable works such as workbooks — S07.1 (A), Circular 21 p.7, III Prohibitions
- **F5** [LB] The Copyright Office says there is no formula for a percentage, word, line or page count that may be used without permission; nonprofit educational uses are more likely, but not automatically, fair; using a work's "heart" can weigh against fair use even if small; creative works weigh against fair use more than factual ones — S07.2 (A), U.S. Copyright Office Fair Use Index (updated July 2026), About Fair Use
- **F6** [LB] The partner's sample outline names the anchor novel with one ISBN edition (9780786838653) and ties Core Reading lessons to a chapter plus a page range (e.g. Lesson 4: Chapter 1, pp. 1–8); its other text-set entries are short excerpts of older myths and epics (Iliad, Aeneid, Popol Vuh, Zanzibar Tales) and Newsela articles — S05.2 (A), sample outline CSV, title row and columns "Lesson Description", "Text Set Choice"
- **F7** [LB] Fishtank Learning's Grade 6 unit lists *The Lightning Thief* (Hyperion, 2005) as a core text, maps one chapter per lesson from Lesson 4 (Ch. 1) to Lesson 27 (Ch. 22) across 28 lessons, tells teachers to order the books, and reproduces no passages from the novel on the unit page — S07.3 (A), that publisher's own practice, Fishtank unit page, Unit Prep and Lesson Map


## Inferences

- **I1** from F1 + F3 + F4 + F5: Newsela lessons are commercial materials written by a publisher, not a teacher's spontaneous copy, so the 1,000-word / 10% guideline is not a safe harbour for them; fair use for any quoted novel text would rest on the four factors alone, with factor 1 (commercial) and factor 2 (creative novel) weighing against it. High confidence in the reading of the sources; not legal advice.
- **I2** from F6 + F7: two independent Tier-A curricula (the partner's outline and Fishtank) reference the anchor novel by edition, chapter and page range rather than reprinting it, and use short public-domain texts as excerpts. High confidence this is common practice for this novel; how widely beyond these two is not measured.
- **I3** from F5 + F6: because page numbers depend on the edition, a lesson that cites pages is only correct for the ISBN the outline names (9780786838653); other editions would need chapter-only references. Medium confidence.

## Gaps

- ⚠ Does Newsela hold a licence from the rights holder of *The Lightning Thief* to quote or display novel text in lessons, and what limit does it set? — why: no Tier-A source found (not in the partner brief) — would close it: ask the partner
- ⚠ How do EL Education / EngageNY materials for the same novel list it (one copy per student, trade-book list)? — why: unread: lessons.unbounded.org pages loaded only a shell (S07.4); unread: OSSE unit overview PDF (404) — would close it: read the EL Education Grade 6 Module 1 materials list
- ⚠ Is a generated paraphrase or summary of a chapter in a lesson acceptable to the partner, versus only page pointers? — why: no source addresses it — would close it: ask the partner

## Handoffs

- write-prd: May generated lessons print any words from the copyrighted anchor novel, and if so up to what limit, or must they reference only edition, chapter and page range? — rests on F2, F4, F5, I1
- write-prd: May generated lessons print public-domain excerpts (myths, epics) in full within the lesson, as the sample outline's text sets do? — rests on F6, I2
- design-hld: Should the lesson data model store anchor-text references as edition (ISBN) + chapter + page range, separate from printed excerpts with their source and copyright status? — rests on F6, F7, I3
