# V — Validate: Testing & Fact-Checking

 **LEMAI: AI-L2 [I1,D2,W3,R2,V1,F2]**  



The Validation stage verifies that the artifact is correct, accurate, and meets its requirements. In writing, this means fact-checking claims, verifying sources, and confirming accuracy. In software, it means running tests, checking for regressions, and confirming that the system behaves as specified. Validation is the last line of defense before finalization.

---

| Activity | AI Level | Rationale |
|---|---|---|
| Manually verifying every claim by checking primary sources and running all tests by hand | 0 | Entirely human validation; no AI tools involved at any step |
| Using an AI static analysis tool to flag potential issues in a test suite for manual review | 1 | AI surfaces areas for human attention; all validation decisions remain with the human |
| Asking AI to locate a primary source that confirms or refutes a specific claim in a draft article | 1 | AI performs a targeted lookup; human evaluates the source and makes the final call |
| Generating a test suite with AI and reviewing each test case for correctness and coverage before running it | 2 | AI accelerates test creation; human validates the test logic before trusting results |
| Using AI to cross-reference every factual claim in an article against multiple sources, then personally verifying all flagged discrepancies | 2 | Human and AI share fact-checking duties; human resolves all conflicts independently |
| Running AI-generated test suites as the primary QA gate, with human review limited to cases that fail | 3 | AI drives the validation process; human involvement is exception-based |
| Delegating most fact-checking to AI and personally verifying only the highest-stakes or most ambiguous claims | 3 | AI handles the bulk of validation; human spot-checks rather than comprehensively verifies |
| AI agent autonomously runs end-to-end test validation and publishes a pass/fail verdict without human involvement | 4 | No human involvement in the validation process itself; human receives only the final verdict |
| AI system autonomously fact-checks every claim in a draft against a curated knowledge base before the article is published | 4 | Fully AI-native validation; human involvement is limited to reviewing flagged exceptions |
