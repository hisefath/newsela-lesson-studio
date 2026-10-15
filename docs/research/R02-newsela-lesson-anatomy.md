---
id: R02
question: "What sections and lesson types make up a Newsela CA lesson (Spark, Core Reading, Core Writing, Academic Discussion, Showcase Writing, Flex), and which parts are fixed vs varying?"
asked_in: specs/M1-lesson-generation-review/brief.md#research-questions
unblocks: "REQ-07; lesson anatomy FRs"
answered_when: "at least two lesson types inspected on the partner's review site"
status: answered
confidence: high
supersedes: none
date: 2026-10-14
budget: 14/15 tool calls
researched_by: claude-code supervisor, claude-opus-5-5
---

# R02 Newsela CA lesson anatomy and lesson types

## Answer

Every Newsela CA Core lesson inspected (Spark, Reading, Writing) shares one fixed teacher-facing skeleton: a header
(type tag, title, minutes, focus / supporting CCSS and ELD standard chips), learning objectives, essential question(s),
"Connections to" four strands, a pacing table, routines, a numbered lesson sequence of timed segments ending in
Homework, and a lesson-texts card; the lesson type changes which segments and inner blocks appear (Reading and
Writing add a 10-minute Literacy Lab, vocabulary and a material list; Writing adds a prompt and checklist; Spark has
no Literacy Lab). Confidence: high, because three lessons and the unit list were read directly on the partner's own
review site. (S02.1, S02.2, S02.3, S02.4)

## Takeaway

A Newsela lesson is a fixed template with type-specific slots, so a generator should fill a known structure, not
write free prose.

## Findings

- **F1** [LB] A Spark lesson has: type tag, title, 50 min, Focus/Supporting CCSS and ELD chips (ELD codes carry
  .Em/.Ex/.Br proficiency suffixes), a student-lesson link, 3 learning objectives (Content, Language, Foundational
  Skills), essential questions, "Connections to" (Knowledge-Building, Enduring Understanding, Future Lessons, Unit
  Performance Task), a pacing table Launch 15 / Learning in Action 30 (Part A, Part B, each tagged with standards) /
  Look Back 5, routines, the sequence, and lesson texts — S02.1 (A), whole page
- **F2** [LB] A Reading lesson adds a "Literacy Lab" segment (10 min; pacing Launch 5 / Literacy Lab 10 / Learning in
  Action 30 / Look Back 5), a Vocabulary block (terms with student-friendly definitions), a Material List, and a
  Check for Understanding; anchor-text excerpts appear as short quotes with page numbers — S02.3 (A), pacing,
  Vocabulary, Lesson Sequence §2
- **F3** [LB] Unit 1 lists 45 lessons labelled SPARK, READING, WRITING, ACADEMIC DISCUSSION, MID-UNIT ASSESSMENT,
  END-UNIT ASSESSMENT, FLEX DAY and RESEARCH; 44 are 50 min and one is 55 min — S02.2 (A), All Lessons list
- **F4** [LB] A Writing lesson has the same skeleton plus, inside Learning in Action, a writing prompt, a drafting
  checklist and model-writing steps; Learning in Action parts carry their own minutes and standards — S02.4 (A),
  Lesson Sequence §3
- **F5** [LB] Inside segments, recurring blocks are: "Say these Directions", "Say", "Ask" with an exemplar student
  answer, Teacher Tip, Pulse Check (multiple choice, four options, each with a Correct/Incorrect rationale, tagged to
  standards), Reflection, Quick Write, collapsible "Integrated ELD Instructions" (purpose, language focus, say/ask
  frames, watch-for) and "Additional Student Support" (situation → try this, incl. "ready for extension") — S02.1
  (A), S02.3 (A), S02.4 (A), Lesson Sequence
- **F6** [LB] The partner's outline labels lessons Spark, Core Reading, Core Writing, Academic Discussion, Writing
  (Showcase), End-of-Arc Flex Day, plus a double-lesson variant; each row gives a text-dependent question, a
  description, text set, homework, focus standards, additional CA ELA standards, media-literacy standards, a
  performance-task skill, foundational-skills focus, vocabulary and designated ELD standards — S02.5 (A), header row
- **F7** Lesson Sequence ends with a Homework step, usually a journal prompt — S02.1 (A), S02.3 (A)

## Inferences

- **I1** from F1 + F2 + F4: pacing segment minutes sum to the lesson's minutes (15+30+5; 5+10+30+5), so "sums to the
  stated duration" is a checkable rule; confidence high for the three types read, unverified for Assessment/Flex.
- **I2** from F3 + F6: the outline's lesson-type vocabulary differs from the site's labels (Core Reading ↔ READING,
  End-of-Arc Flex Day ↔ FLEX DAY), so a mapping between them is needed; confidence high.
- **I3** from F2 + F5: anchor-text use in published lessons is short page-cited excerpts, not long passages
  (consistent with decode T-3); confidence medium (three lessons).

## Gaps

- ⚠ Anatomy of Academic Discussion, Assessment, Flex and Research lessons — why: cap reached — would close it: read
  one lesson of each type on the review site.
- ⚠ The student-facing lesson view was not inspected — why: out of scope for the teacher edition — would close it:
  open "Open Student Lesson".

## Handoffs

- write-prd: Which lesson types must generation support in the first build milestone (Spark/Reading/Writing only, or also Discussion and Flex)? — rests on F3, F6
- write-prd: Must Integrated ELD Instructions and Additional Student Support be generated, or left for reviewers? — rests on F5
- design-hld: How is the fixed skeleton with type-specific slots represented so the editor and the generator share it? — rests on F1, F2, F4, I1
