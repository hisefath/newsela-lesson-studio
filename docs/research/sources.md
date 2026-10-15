# Sources

Append-only log of every source read for `docs/research/`. One row per read; a source keeps its S-id forever
(reading it again appends a new row with the same S-id and the new date). Never edit, renumber or delete a row.

Tiers: **A** primary/official · **B** reputable secondary · **C** community or generated (never carries a
load-bearing claim). A load-bearing claim needs 1 Tier-A or 2 independent Tier-B sources.

<!-- Row shape: | S01.1 | <title, no pipes> | <url, or repo path + locator> | A | <YYYY-MM-DD> | R01 F1: <claim, 12 words max> | -->

| S-id | title | url | tier | date read | supports |
|---|---|---|---|---|---|
| S-id | title | url | tier | date read | supports |
| S01.1 | CDE Common Core State Standards landing page (last reviewed 2026-02-24) | https://www.cde.ca.gov/re/cc/ | A | 2026-10-14 | R01 F1: CDE links the CA CCSS ELA/Literacy PDF and a standards search app |
| S01.2 | California Common Core State Standards: ELA & Literacy (CDE, modified March 2013) | https://www.cde.ca.gov/be/st/ss/documents/finalelaccssstandards.pdf | A | 2026-10-14 | R01 F2-F5: official CA CCSS text, code format, CA additions, RL.6.9 |
| S01.3 | California English Language Development Standards K-12 (CDE, adopted Nov 2012) | https://www.cde.ca.gov/sp/el/er/documents/eldstndspublication14.pdf | A | 2026-10-14 | R01 F6-F8: official CA ELD text, Parts I-III, grade 6 standards |
| S01.4 | Invitation to Submit: 2026 ELA/ELD Instructional Materials Follow-Up Adoption (CDE) | https://www.cde.ca.gov/CI/rl/im/documents/itselaeld2026.docx | A | 2026-10-14 | R01 F9-F10: Program Type 1 = Basic ELA (K-8); 2026 follow-up adoption |
| S01.5 | 2014 ELA/ELD Framework, Chapter 12: Criteria for Instructional Materials (CDE) | https://www.cde.ca.gov/ci/rl/cf/documents/elaeldfwchapter12.pdf | A | 2026-10-14 | R01 F11-F12 R08 F1-F3: Program 1 definition; five evaluation categories |
| S08.1 | EdReports report overview: Fishtank ELA 6-8 (2021) | https://edreports.org/reports/overview/fishtank-ela-6-8-2021 | A | 2026-10-14 | R08 F4: three gateways, rating labels, review tool v2.0 current |
| S08.2 | EdReports 3-8 ELA Quality Instructional Materials Tool Evidence Guides (updated 2016-08-30) | https://cdn.edreports.org/legacy/files/3-8%20ELA%20Combined%20Evidence%20Guides_2.pdf | A | 2026-10-14 | R08 F5: indicator-level wording 1a-1q and 2a-2h (legacy tool) |
| S08.3 | Student Achievement Partners: Reviewing Instructional Materials webinar (WA OSPI, 2014) | https://files.nwesd.org/jlongchamps/CD_Meetings/5.9.14/WA_OSPI_IMET_Webinar043014.pdf | A | 2026-10-14 | R08 F6-F7: IMET ELA non-negotiables; EQuIP rubric for lessons and units |
| S02.1 | Newsela Threads & Themes ELA Core 6th Grade, Unit 1 Lesson 1 (Spark) | https://ca-2026-review.newsela.com/course/cmkfw4elj004k8a90yvyfyfb8/unit/ck73kftqkdhaojqgqft3acmy/lesson/c0c4tx7u3mnezs5w9u8vzvi1 | A | 2026-10-14 | R02 F1: Spark lesson anatomy; pacing 15/30/5 = 50 min |
| S02.2 | Newsela Threads & Themes ELA Core 6th Grade, Unit 1 lesson list | https://ca-2026-review.newsela.com/course/cmkfw4elj004k8a90yvyfyfb8/unit/ck73kftqkdhaojqgqft3acmy/lessons | A | 2026-10-14 | R02 F3: 45 lessons, eight lesson-type labels, durations |
| S02.3 | Newsela Threads & Themes ELA Core 6th Grade, Unit 1 Lesson 4 (Reading) | https://ca-2026-review.newsela.com/course/cmkfw4elj004k8a90yvyfyfb8/unit/ck73kftqkdhaojqgqft3acmy/lesson/cju7dy9lebtn7bgy64apy6y0 | A | 2026-10-14 | R02 F2: Literacy Lab, Vocabulary, Material List, page-cited excerpts |
| S02.4 | Newsela Threads & Themes ELA Core 6th Grade, Unit 1 Lesson 7 (Writing) | https://ca-2026-review.newsela.com/course/cmkfw4elj004k8a90yvyfyfb8/unit/ck73kftqkdhaojqgqft3acmy/lesson/cjxmb6wwn2haijekua0u2byq | A | 2026-10-14 | R02 F4: writing prompt, checklist, ELD and support drawers |
| S02.5 | Partner sample unit outline G6 U3 (CSV export) | docs/source/raw/sample-unit-outline-G6-U3.csv (gitignored) | A | 2026-10-14 | R02 F6: outline columns and lesson-type labels |
| S03.1 | Newsela homepage | https://newsela.com/ | A | 2026-10-14 | R03 F1, F2: product list; "Trusted by 1,000+ Districts Nationwide" |
| S03.2 | CDE Review Panel Advisory Report: Newsela Threads & Themes ELA for California (Program Type 1, Grades 6–8) | https://www.cde.ca.gov/ci/rl/im/documents/newsela6thru8.docx | A | 2026-10-14 | R03 F4, F6; R04 F5: Type 1 recommended, advisory, cited lesson ids |
| S03.3 | CDE Review Panel Advisory Report: Newsela Threads & Themes ELA and ELD for California (Program Type 2, Grades 6–8) | https://www.cde.ca.gov/ci/rl/im/documents/newselathdsths6thru8.docx | A | 2026-10-14 | R03 F5; R04 F5: Type 2 recommended; digital TE/SE plus resources |
| S03.4 | Newsela Threads & Themes product page | https://newsela.com/products/threads-and-themes | A | 2026-10-14 | R03 F3: blended core curriculum grades 6–8 for California |
| S03.5 | Newsela Greenhouse job board (public API, 12 open jobs) | https://boards-api.greenhouse.io/v1/boards/newsela/jobs | A | 2026-10-14 | R03 F8, F9: open roles; contractor SWE builds AI-integrated features |
| S03.6 | Newsela careers page | https://newsela.com/careers | A | 2026-10-14 | R03 F2, F10: 90% of US schools, 20M students, fully remote |
| S04.1 | SBE November 2025 Agenda Item 15: Guidance for the 2026 ELA/ELD Follow-up Adoption | https://www.cde.ca.gov/be/ag/ag/yr25/documents/nov25item15.docx | A | 2026-10-14 | R04 F1, F2: TK–8 follow-up adoption; final action Nov 2026; last adoption 2015 |
| S01.4 | CDE 2026 ELA/ELD Follow-up Adoption Information and Training for Publishers (ITS) | https://www.cde.ca.gov/CI/rl/im/documents/itselaeld2026.docx | A | 2026-10-14 | R04 F3, F4: added to 2015 list; materials frozen May 15 2026; price list |
| S04.3 | CDE Review Panel Advisory Report: McGraw Hill Summit! California (Type 2, 6–8) | https://www.cde.ca.gov/ci/rl/im/documents/mcgrawhillsummit6thru8.docx | A | 2026-10-14 | R04 F5: McGraw Hill recommended grades 6–8 |
| S04.4 | CDE Review Panel Advisory Report: Inquiry by Design ELA with ELD California Edition (Type 2, 6–8) | https://www.cde.ca.gov/ci/rl/im/documents/inquirybydesign6thru8.docx | A | 2026-10-14 | R04 F5: Inquiry by Design recommended grades 6–8 |
| S04.5 | CDE Review Panel Advisory Report: Savvas myPerspectives ELA with myVoice ELD (Type 2, 6–8) | https://www.cde.ca.gov/ci/rl/im/documents/savvasmvoicepers6thru8.docx | A | 2026-10-14 | R04 F5: Savvas Type 2 recommended grades 6–8 |
| S04.6 | CDE Review Panel Advisory Report: Savvas myPerspectives ELA California (Type 1, 6–8) | https://www.cde.ca.gov/ci/rl/im/documents/savvasmyperstype16thru8.docx | A | 2026-10-14 | R04 F5: Savvas Type 1 recommended grades 6–8 |
| S04.7 | CDE Review Panel Advisory Report: Imagine Learning StudySync California (Type 2, 6–8) | https://www.cde.ca.gov/ci/rl/im/documents/imaginestudysync6thru8.docx | A | 2026-10-14 | R04 F5: StudySync Type 2 recommended grades 6–8 |
| S04.8 | CDE Review Panel Advisory Report: Imagine Learning StudySync California (Type 1, 6–8) | https://www.cde.ca.gov/ci/rl/im/documents/imaginelrng6thru8.docx | A | 2026-10-14 | R04 F5: StudySync Type 1 recommended grades 6–8 |
| S04.9 | CDE Review Panel Advisory Report: HMH Into Literature California (Type 2, 6–8) | https://www.cde.ca.gov/ci/rl/im/documents/hmhedco6thru8.docx | A | 2026-10-14 | R04 F5: HMH recommended grades 6–8 |
| S04.10 | CDE Review Panel Advisory Report: ThinkCERCA Core ELAR for Grades 6–8 (Type 2) | https://www.cde.ca.gov/ci/rl/im/documents/thinkceraelaeld6thru8.docx | A | 2026-10-14 | R04 F5: ThinkCERCA Type 2 recommended grades 6–8 |
| S04.11 | CDE Review Panel Advisory Report: ThinkCERCA Core ELAR California Edition (Type 1, 6–8) | https://www.cde.ca.gov/ci/rl/im/documents/thinkcercacorelar6thru8.docx | A | 2026-10-14 | R04 F5: ThinkCERCA Type 1 recommended grades 6–8 |
| S04.12 | CDE Review Panel Advisory Report: Open Up Resources EL Education 6–8 California (Type 1) | https://www.cde.ca.gov/ci/rl/im/documents/openupresources7thru8.docx | A | 2026-10-14 | R04 F5: EL Education recommended grades 7–8 only |
| S04.13 | NCES Digest of Education Statistics Table 203.40: enrollment by grade and state, Fall 2022 | https://nces.ed.gov/programs/digest/d23/tables/dt23_203.40.asp | A | 2026-10-14 | R04 F6: CA grade 6/7/8 enrollment 438,570 / 440,251 / 436,134 |
| S04.14 | Johnson County Post: Shawnee Mission approves $3.5M for new elementary ELA curriculum (2022-03-28) | https://johnsoncountypost.com/2022/03/28/shawnee-mission-english-language-arts-curriculum-143585/ | B | 2026-10-14 | R04 F7: K–6 McGraw-Hill materials about $40 per student per year |
| S05.1 | Partner brief (portal), Lesson Content Generation and Editing/Approval Workflow v1 | docs/source/raw/portal-brief.md §Project brief, §Performance (gitignored) | A | 2026-10-14 | R05 F1: 4 units of ~40 lessons, grades 6-8; 20+ reviewers |
| S05.2 | Sample unit outline G6 U3, The Lightning Thief (partner Google Sheet export) | docs/source/raw/sample-unit-outline-G6-U3.csv rows 1-57 (gitignored) | A | 2026-10-14 | R05 F3: 42 lesson rows; R07 F6: novel cited by chapter and pages |
| S05.3 | Google Docs Editors Help: share files (edit limit) | https://support.google.com/docs/answer/2494822 | A | 2026-10-14 | R05 F5: a Google file edits on up to 100 tabs or devices |
| S05.4 | Yjs documentation home | https://docs.yjs.dev/ | A | 2026-10-14 | R05 F6: Yjs CRDT merges concurrent edits without conflicts |
| S05.5 | Education Week, Text-Review Group Shares First Look at Its Process (Loewus, 2014-11-04) | https://www.edweek.org/teaching-learning/text-review-group-shares-first-look-at-its-process/2014/11 | B | 2026-10-14 | R05 F7: EdReports reviews in teams of four, weekly meeting |
| S05.6 | INFOhio EdReports learning pathway page | https://infohio.org/campus/learning-pathways/course/edreports/understanding-the-review-process | C | 2026-10-14 | R05 none: page held no review-process content |
| S06.1 | Editorial Freelancers Association, Editorial Rates (2026 Rate Chart) | https://the-efa.org/rates | B | 2026-10-14 | R06 F3: curricula secondary school $80-115 per hour |
| S06.2 | EFA, 2026 Editorial Rate Chart release (2026-03-24) | https://www.the-efa.org/2026-editorial-rate-chart/ | B | 2026-10-14 | R06 F4: survey Nov 2025-Jan 2026, 1,100+ respondents, guidance only |
| S06.3 | BLS Occupational Outlook Handbook, Instructional Coordinators | https://www.bls.gov/ooh/education-training-and-library/instructional-coordinators.htm | A | 2026-10-14 | R06 F5: median $37.23 per hour, May 2025 |
| S06.4 | Karl Kapp, How long does it take to develop one hour of e-learning (2009 update) | https://karlkapp.com/how-long-does-it-take-to-develop-one/ | C | 2026-10-14 | R06 F6: 49-89 hours per hour of instructor-led training |
| S07.1 | U.S. Copyright Office, Circular 21: Reproduction of Copyrighted Works by Educators and Librarians | https://www.copyright.gov/circs/circ21.pdf pp.4-8 | A | 2026-10-14 | R07 F1-F4: section 107 factors; classroom guidelines 1,000 words or 10% |
| S07.2 | U.S. Copyright Office Fair Use Index (updated July 2026) | https://www.copyright.gov/fair-use/ | A | 2026-10-14 | R07 F5: no set word count or percentage is automatically fair |
| S07.3 | Fishtank Learning, Grade 6 ELA archived unit: The Lightning Thief and Greek Mythology | https://fishtanklearning.org/curriculum/ela/6th-grade/archive-the-lightning-thief-greek-mythology | A | 2026-10-14 | R07 F7: lessons mapped to chapters; no novel excerpts printed |
| S07.4 | UnboundEd ELA Grade 6 Module 1 Unit 1 Lesson 3 page | https://lessons.unbounded.org/ela/grade-6/module-1/unit-1/lesson-3 | C | 2026-10-14 | R07 none: page shell only, no materials list readable |
