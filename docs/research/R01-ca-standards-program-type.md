---
id: R01
question: "What is the canonical, citable source for CA CCSS ELA/Literacy grades 6–8 and CA ELD standards (codes + definitions), and what does \"Program Type 1\" mean in California's ELA/ELD adoption?"
asked_in: specs/M1-lesson-generation-review/brief.md#research-questions
unblocks: "REQ-02, REQ-03; how standards are known to the product"
answered_when: "an official CDE source lists codes and text, and an official source defines Program Type 1"
status: partial
confidence: medium
supersedes: none
date: 2026-10-14
budget: 15/15 tool calls
researched_by: Claude Code, claude-opus-5-5
---

# R01 Canonical CA ELA/ELD standards source and Program Type 1

## Answer

The canonical sources are two CDE PDFs: the "California Common Core State Standards: English Language Arts & Literacy" (SBE-adopted August 2010, modified March 2013) and the "California English Language Development Standards, Kindergarten Through Grade 12" (SBE-adopted November 2012). Neither is machine-readable data, but both extract cleanly to text. "Program Type 1" is CDE's "Basic ELA (K–8)" category in the 2026 ELA/ELD follow-up adoption, defined in Framework chapter 12 as the comprehensive grade-level ELA program that makes sure students master the CA CCSS for ELA. It requires CA ELD Standards alignment only for Programs 2, 3 and 5, not for Program 1. Confidence: medium, because every finding rests on Tier-A CDE text, but no official source uses the dotted code format in the outline (`ELD.PI.6.6`, `W.6.2.c`), and `RL.6.9.a` does not exist in the official grade 6 text. (S01.2, S01.3, S01.4, S01.5)

## Takeaway

California publishes its ELA and English-learner standards as two official PDFs. "Program Type 1" is the state's label for a regular grade-level ELA curriculum, as opposed to the combined ELA plus English-learner version.

## Findings

- **F1** [LB] CDE's Common Core page links the CA CCSS ELA/Literacy publication PDF ("Modified Mar-2013") and a "Search the California Content Standards" web app at www2.cde.ca.gov/cacs/. It points to the ELD standards from /sp/el/er/eldstandards.asp. — S01.1 (A), ELA/Literacy section and footer links
- **F2** [LB] The CA CCSS for ELA/Literacy were adopted by the SBE August 2, 2010 and modified March 13, 2013. They are published by CDE (© 2013, ISBN 978-0-8011-1740-4). The PDF's metadata shows a modification date of 2024-11-06. — S01.2 (A), title page and Publishing Information
- **F3** [LB] Grade-specific standards are identified by strand, grade and number "(or number and letter, where applicable)". The document's own examples are "RI.4.3" and "W.5.1a", with no dot before the letter. — S01.2 (A), "How to Read This Document"
- **F4** [LB] California additions to the standards appear "in boldface text followed by the abbreviation 'CA.'" — S01.2 (A), "How to Read This Document"
- **F5** [LB] Grade 6 RL standard 9 reads "Compare and contrast texts in different forms or genres … in terms of their approaches to similar themes and topics" and has no lettered substandards. Grade 6 L.4 does have a lettered "b" ("Use common, grade-appropriate Greek or Latin affixes and roots…"). — S01.2 (A), Reading Standards for Literature 6–12 p.48; Language Standards 6–12
- **F6** [LB] The CA ELD Standards K–12 were adopted by the SBE in November 2012 (November 7, 2012 per S01.5). They are organized in Part I "Interacting in Meaningful Ways", Part II "Learning About How English Works" and Part III "Using Foundational Literacy Skills". — S01.3 (A), title page and Chapter 1; S01.5 (A), Category 1 criterion 2
- **F7** [LB] For grade 6, Part I lists numbered standards 1–12 under Collaborative (1–4), Interpretive (5–8) and Productive (9–12). Standard 6 is "Reading closely literary and informational texts and viewing multimedia…". Each row maps to "Corresponding CA CCSS for ELA/Literacy" codes such as RL.6.1–7, 9–10. Part II lists standards 1–7, and 4 is "Using nouns and noun phrases". — S01.3 (A), Chapter 3 Grade 6, pp.86–87
- **F8** The ELD standards define three proficiency levels: Emerging, Expanding and Bridging. The publication describes the CA CCSS coding order as domain, grade level and standard number (e.g. RL.1.5). It gives no equivalent dotted code for ELD standards. — S01.3 (A), Chapter 1 and Chapter 5 note 5
- **F9** [LB] The 2026 ELA/ELD Follow-Up Adoption Invitation to Submit lists "Program Type 1: Basic ELA (K–8)", "Program Type 2: Basic ELA/ELD (K–8)", Type 3 Basic Biliteracy, Type 4 Intensive Intervention (1–8) and Type 5 Specialized ELD (4–8), plus TK and partial-strand types. — S01.4 (A), "Program Types and Participation Fees"
- **F10** [LB] The ITS says reviewers' criteria "are found in chapter 12 of the ELA/ELD Framework". It says the SBE adopts in November 2026, adding to the 2015 list, and that submissions must exclude references to national or other-state standards. — S01.4 (A), "Overview of Content Requirements and Review Procedures"
- **F11** [LB] Framework chapter 12 defines Program 1 Basic ELA as "the comprehensive curriculum in English language arts for kindergarten through grade eight". It is intended to ensure all students master the CA CCSS for ELA and addresses students "at or near grade level". Program 2 adds integration of the CA ELD Standards and designated ELD materials. — S01.5 (A), pp.1010–1011, program descriptions
- **F12** [LB] Under Category 1, Programs 1, 2 and 3 must show alignment with all CA CCSS for ELA. Alignment with the CA ELD Standards is required for Programs 2, 3 and 5. Category 4 (Universal Access) applies to all programs and names English learners. — S01.5 (A), Category 1 criteria 1–2; category overview

## Inferences

- **I1** from F3 + F5 + F7: The outline's codes look like project-local spellings of official codes, not official ones. `W.6.2.c` would be official `W.6.2c`, and `ELD.PI.6.6` reads as ELD Part I, grade 6, standard 6. `RL.6.9.a` matches no grade 6 standard in the CA CCSS text, so either it is an error or it comes from another source. High confidence on RL.6.9, medium on the ELD reading.
- **I2** from F11 + F12: A Program Type 1 lesson must align to CA CCSS for ELA. ELD-standard tags, as the outline uses them, go beyond Program 1's Category 1 requirement and look more like Program 2. Program 1 still has to give English learners access under Category 4. Medium confidence, because the partner's own meaning of "Program Type 1" was not read.
- **I3** from F2 + F6: Both standards documents are PDFs, so a product that "knows" the standards would need its own extracted table of codes and text built from them. CDE's search app (F1) may offer a structured alternative, but it was not read. Medium confidence.

## Gaps

- ⚠ Is there an official dotted code format for ELD standards (e.g. `ELD.PI.6.6`) and for lettered substandards with a dot (`W.6.2.c`)? — why: no Tier-A source read uses them — would close it: read the 2014 ELA/ELD Framework grade 6–8 chapter (ch. 6) or the partner's outline source
- ⚠ Where does `RL.6.9.a` come from? — why: no grade 6 RL.9 substandard in S01.2 — would close it: ask the partner, or check the CA CCSS grade 6 text again in the CDE search app
- ⚠ Does the CDE "Search the California Content Standards" app (www2.cde.ca.gov/cacs/) give machine-readable codes and text? — why: cap reached, unread — would close it: open the app and check for export or an API
- ⚠ What do the CDE ELD standards landing page and the 2015 ELA/ELD adoption FAQ's Program Type 1 section add? — why: unread: https://www.cde.ca.gov/sp/el/er/eldstandards.asp and https://www.cde.ca.gov/ci/rl/im/elaeldadoptionfaqs.asp (bot-challenge/CAPTCHA page; not bypassed) — would close it: a human opens them in a browser
- ⚠ Does the partner mean CDE's Program Type 1 (Basic ELA) exactly, or loosely "CA Core ELA grades 6–8"? — why: partner material not read in this pass — would close it: ask the partner (R03)

## Handoffs

- write-prd: Should the product's standards catalogue use the official CDE code spelling (`W.6.2c`) or the outline's dotted spelling (`W.6.2.c`), and how should unknown codes like `RL.6.9.a` be handled? — rests on F3, F5, I1
- write-prd: Does "Program Type 1" in scope mean CA CCSS ELA alignment only, or ELA plus ELD (closer to Program 2)? — rests on F11, F12, I2
- design-hld: Where should the standards text live (an extracted table built from S01.2 and S01.3 PDFs, or a lookup against CDE's search app), and how is its version recorded? — rests on F1, F2, F6, I3
