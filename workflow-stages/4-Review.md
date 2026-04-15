# R — Review: Editing, Revising & Code Review

 **LEMAI: AI-L2 [I1,D2,W3,R2,V1,F2]**  



The Review stage applies critical judgment to the artifact produced in the Work stage. In writing, this means editing for clarity, argument strength, and accuracy. In software, it means code review for correctness, maintainability, and security. The quality of review directly determines how many defects or weaknesses pass through to later stages. Particular activities are assigned labels to refer back to them. The labels are typically, workflow stage, type of process (Dev = development, Creat = Creative), AI usage level, and a letter to make the label distinct.

---

| Activity | AI Level | Rationale |
|---|---|---|
| Reading through a draft or pull request and making all edits and comments manually | 0 | Entirely human review; no AI tools involved |
| **R:Dev:1-A** — Asking AI to check a specific function for a known class of bug or security vulnerability | 1 | AI performs a targeted check on human-identified scope; human makes all decisions about what to change |
| **R:Creat:1-A** — Running a draft through an AI grammar tool and manually accepting or rejecting each stylistic suggestion | 1 | AI provides suggestions reactively; human retains full judgment on what to accept |
| **R:Dev:2-A** — Using AI to summarize a pull request diff and flag potential issues, then manually verifying each flagged item | 2 | Human and AI share the review workload; human verifies all AI-flagged items independently |
| **R:Creat:2-A** — Asking AI to mark up a draft article with inline comments on clarity and argument strength, then personally deciding what to address | 2 | AI augments coverage and speed of review; human applies judgment to every recommendation |
| **R:Dev:3-A** — Using an AI code review tool to evaluate a PR and accepting the majority of its recommendations with only selective manual verification | 3 | AI leads the review; human provides a high-level pass rather than line-by-line judgment |
| **R:Creat:3-A** — Having AI perform a full structural and stylistic review of a draft and accepting most recommendations without reading every suggestion | 3 | AI makes most review decisions; human spot-checks rather than adjudicating each item |
| **R:Dev:4-A** — AI agent reviews, approves, and merges pull requests without any human involvement | 4 | Fully automated review pipeline; no human in the loop |
| **R:Creat:4-A** — AI system autonomously reviews and redlines all content, delivering only filtered output to human editors | 4 | AI acts as the sole reviewer; humans never see the unfiltered artifact |
