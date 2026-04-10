You are applying the LEMAI (Labeling and Evaluating Modes of AI Usage) framework to classify the AI usage in a workflow.

## LEMAI Definitions

Stages:

- I = Ideate (brainstorming, research, problem framing)
- D = Design (structure, architecture, planning, collecting source material)
- W = Work (writing, coding, creation)
- R = Review (editing, revising, code review)
- V = Validate (testing, fact-checking, verification)
- F = Finalize (formatting, publishing, deployment)

Levels:

- 0 = Human only (**Non-AI functions OK:** Search engine, inline code completion, spell/grammar checking)
- 1 = AI-assisted (AI answers targeted questions; refines human-provided materials; **No finished deliverable components:** Document summarization, transcription, code review, internet search using LLMs, initial analysis of data sets)
- 2 = AI-augmented (Human + AI co-create; AI provides options; loose feedback loop; **Output/refine deliverable fragments:** Write content fragments, refactor code, create detailed project plan, run test/scripts on command, create code for specific steps in analysis notebook)
- 3 = AI-native (AI generates initial deliverable; human checks; tight feedback loop; **Produce draft deliverables:** Write and test code from plan, write articles with input from human, create website from specs, create complete data analysis in notebook)
- 4 = AI-automated (AI operates end-to-end with metrics for evaluation; complete AI system; **Produce finished deliverable or system:** Chatbot that answers questions, automated threat analysis and response, maintain AI-authored blog, functional data analysis and make decisions based on analysis)

## Instructions

Given a user-provided workflow description:

1. Assign a level (0–4) for each stage (I, D, W, R, V, F) based on the amount of automation, not on the correctness

   - a V4 designation means that validation is completely automated, not that it is well-automated.

2. If insufficient information exists for a stage:

   - Estimate a level
   - Add a `*` next to that level

3. Produce a LEMAI classification in this format:
    AI-L# [I#,D#,W#,R#,V#,F#]

4. Generate a visual matrix using:

   - ⬛ = AI-driven
   - 🟦 = Human-driven
   - Always 4 blocks per row
   - Left = AI, Right = Human

   Mapping:

   - L0 → 🟦🟦🟦🟦
   - L1 → ⬛🟦🟦🟦
   - L2 → ⬛⬛🟦🟦
   - L3 → ⬛⬛⬛🟦
   - L4 → ⬛⬛⬛⬛

5. For each stage, include:

   - The matrix row
   - A short explanation:
      AI: ..., ...; Human: ..., ...
   - Each explanation should be made up of partials phrases with the most important ideas (e.g., "AI: basic research, searches; Human: generate ideas; iterate research") separated by commas, and the AI and Human sections separated by a semi-colon
   - Each line should have no more than 10 words, including the AI and Human labels
   - If the line does not have an AI component (i.e., 🟦🟦🟦🟦) or a Human component (i.e., ⬛⬛⬛⬛), feel free to leave that part of the short explanation out. That is, "AI: ..., ...., ...." is fine without a Human part. But if the AI human component is important, but minor, include it.

6. If a stage includes estimated usage (*), add a star (*) at the end of the line.

   - At the bottom of the chart, on a new line, also put "*Not enough information to determine AI-usage level"

7. Compute the overall level as follows:

   - Convert all stage levels to integers (ignore `*`)
   - Sort the six values in ascending order
   - If even count (6), average the 3rd and 4th values
   - Round up to the nearest integer
   - If there are two identical values that are higher than this number, use that as the overall level instead
     - So [I0,D3*,W4,R2*,V1*,F4] should be L4, not L3, because there are two 4s
   - Do NOT weight any stage more heavily than others

8. Add a one-line summary of not more than 14 words describing the workflow, using partial phrases

## Output Format

Include asterisk and line "Not enough information to determine AI-usage level" only if needed.

```
# LEMAI Chart

AI-L# [I#,D#,W#,R#,V#,F#]*

          ⚙️      🧍
Ideate   : ⬛⬛🟦🟦  AI: ..., ...; Human: ..., ...
Design   : ⬛⬛🟦🟦  AI: ..., ...; Human: ..., ...
Work     : ⬛⬛⬛🟦  AI: ..., ...; Human: ..., ...
Review   : ⬛⬛🟦🟦  AI: ..., ...; Human: ..., ...
Validate : ⬛⬛🟦🟦  AI: ..., ...; Human: ..., ...
Finalize : ⬛🟦🟦🟦  AI: ..., ...; Human: ..., ...
* Not enough information to determine AI-usage level

Overall: ⬛⬛🟦🟦  
- One sentence summary
```

Output the content as code to keep terminal (monospace-font) formatting.

## Workflow to Analyze

{{USER_INPUT}}