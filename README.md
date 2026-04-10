# Labeling and Evaluating Modes of AI Usage (LEMAI)

*A Workflow Transparency and Specification Model for Human–AI Collaboration*

**By Robert Lemos, Lemos Associates LLC**

**© 2026 Lemos Associates LLC**

This work is licensed under the **Creative Commons Attribution 4.0 International License (CC BY 4.0)**.

**LEMAI: AI-L2 [I1,D2,W2,R2,V1,F1]**



## Problem Statement

Organizations have expressed a range of different AI strategies and different requirements for how they intend to use AI, but have trouble communicating their requirements. From publishers and journalism firms that state "Don't use AI" to software development firms that want as much agentic functionality as possible (as long as it works), the range of acceptable AI usage is a spectrum.

This framework aims to **enable transparency and standardization in policies around actual AI usage**. The intent of the framework is to allow content creators to be transparent about AI usage in a granular way and give companies and clients the ability to state AI-usage requirements. In addition, tool makers may be able to use the framework to evaluate their contribution to AI usage and create an additive system that could help automate the evalution of a workflow pipeline. 

#### Primary benefits

1. Allows content creators to **be transparent** in a well-defined way about their use of AI in their workflow.
2. Allows clients and content consumers to **set requirements and guidelines** on AI usage for requested content. 

#### Secondary benefits

3. Content tool providers can **determine the workflow stage that is impacted by their AI-based tool and at what level of AI usage**, and communicate that information to their creators to include in disclosures.
4. AI detectors — such as GPTZero, AI Detector, and Copyleaks — can be **potentially more granular about the workflow stage at which a content creator made use of AI**. For example, using an "AI reviewer" (i.e., AI at the Review stage) can be differentiated from using an LLM to produce whole copy (i.e., AI at the Work stage), since it's possible that the former could be more acceptable than the latter.



## Getting Started

The full framework discussion is in `docs/lemai-framework.md`.

An initial prompt for generating AI usage charts and short-form strings is in the `/prompts` directory. Just replace the `{{USER_INPUT}}` string with a description of your workflow's AI usage. For determining workflows in implied descriptions, I recommend a two step process:

1. ask your favorite LLM to describe explicityly the implied workflow, and
2. then ask it to generate the AI usage chart.



## Details

The Labeling and Evaluating Modes of AI Usage (LEMAI, pronounced LEE-mai) schema is derived from two components:

1. A workflow model

2. An evaluation of AI usage as a 0-4 ranking (expanding Dan Guido's 3 levels)


The model and ranking can be combined to create a short-form description of AI usage in a workflow. A more detailed long-form version includes a visual representation, and an HTML/JSON schema can be created for machine readability. 

### a. Workflow Model

The model generalizes the workflow for content creation into six stages. The workflow model should work for all sorts of content-creation efforts, from books and articles, to software development and data analysis.

| Code | Stage                                           |
| ---- | ----------------------------------------------- |
| I    | Ideate — Idea Generation / Brainstorming        |
| D    | Design — Structure / Architecture               |
| W    | Work — Writing / Coding                         |
| R    | Review — Editing / Revising / Code Review       |
| V    | Validate — Testing / Fact-checking              |
| F    | Finalize — Formatting / Publishing / Deployment |



### b. AI Usage Evaluation Model

In the past, I've used the terms "AI-assisted" and "AI-augmented" to typically talk about different level of AI usage in coding tasks, and many companies have introduced "AI-native" as a marketing term. Intuitively, AI-assisted means less use of AI than AI-augmented. Dan Guido of Trail of Bits further refined this intuition in [a recent column](https://tldrsec.com/p/how-we-made-trail-of-bits-ai-native-so-far) to three levels:

1. **AI-assisted** — Using AI to accomplish small, easily defined tasks.
2. **AI-augmented** — Redesign your workflow to put agents in the loop, often to generate intial content that the human then reviews. 
3. **AI-native** — A structural shift, where AI is a core participant and not a tool occasional involved in the process.

I've expanded that to include a base case of no AI (but not necessarily no _automation_) and expanded the late-stage definitions of AI usage to include an AI-automated category, which extends beyond AI-Native workflows to include pieplines that are almost entirely AI automated.

| Level | Name         | Description                                                  | Common AI Tasks                                              |
| ----- | ------------ | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 0     | Human Only   | No AI usage                                                  | **Non-AI functions OK:** Search engine, inline code completion, spell/grammar checking |
| 1     | AI-Assisted  | AI answers targeted questions; refines human-provided materials | **No finished deliverable components:** Document summarization, transcription, code review, internet search using LLMs, initial analysis of data sets |
| 2     | AI-Augmented | Human + AI co-create; AI provides options; loose feedback loop | **Output/refine deliverable fragments:** Write content fragments, refactor code, create detailed project plan, run test/scripts on command, create code for specific steps in analysis notebook |
| 3     | AI-Native    | AI produces initial deliverable; human checks; tight feedback loop | **Produce draft deliverables:** Write and test code from plan, write articles with input from human, create website from specs, create complete data analysis in notebook |
| 4     | AI-Automated | AI operates end-to-end with metrics for evaluation; complete AI system | **Produce finished deliverable or system:** Chatbot that answers questions, automated threat analysis and response, maintain AI-authored blog, functional data analysis and make decisions based on analysis |



### c. Short form

The short form of the LEMAI framework is intendeded as a way to state inline the score or policy for a particular piece of content. Given a user-provided workflow description, a user (or AI system) can create the short form by a simple process:

1. Assign a level (0–4) for each stage (I, D, W, R, V, F)

2. Produce a LEMAI classification in this format:
    AI-L# [I#,D#,W#,R#,V#,F#]

3. Assign an overall level, L#, by taking the median (rounded up) of all six components, or — if there are two components that are high outliers — that value, **whichever is highest**.

   a. [I2,D2,W3,R2,V2,F1] -> L2     # median = 2

   b. [I2,D1,W3,R3,V1,F1] -> L3     # median = 1, but two '3' outliers make it level 3

4. Add a single-line statement covering the broad strokes of the policy/usage. Examples:

   - "AI assists in some research and content-checking capacity; humans produce content and have tight control over editorial"
   - "AI agents execute audits; humans orchestrate, validate, and deliver"

#### i. Typical Journalism Policy

- AI-L1 [I1,D1,W0,R0,V0,F0]

- AI used only for research, transcription; all content human-written and verified

#### ii. Typical Software-Development or Data-Science Policy

- AI-L2 [I2,D2,W3,R2,V2,F1] 
- AI-assisted development with full human review and validation.

#### iii. Typical AI Instantiated Workflow (such as chatbot request)

- AI-L4 [I0,D2,W4,R3,V4,F4] 
- Human requests information; AI performs all work with some Human review of output

For clarity, the shortform can **prepend the LEMAI tag, but the tag is not necessary**, unless other similar descriptive frameworks are present in the ecosystem. For example:

LEMAI: AI-L2 [I1,D2,W2,R2,V1,F1]



### d. Long form

The long-form statement is suitable for site-wide policy statements, declarations to clients, or inclusion in README.md files. It's also suitable as initial declarations to audiences that might not otherwise understand the short form. It adds the following two components:

1. an emoji-based chart suitable for terminal output or inclusion in Markdown file, using black squares for AI work and blue for Human work, and more complete names for each workflow stage, and
2. a per workflow stage statement (10 words or less) of the AI and Human components of that stage.

#### i. Typical Journalism policy

```
AI-L1 [I1,D0,W0,R0,V1,F0]

        ⚙️      🧍
Ideate : ⬛🟦🟦🟦  Human: Find topics, pitch articles; AI: Search, summarize docs/news 
Design : ⬛🟦🟦🟦  Human: Create pitch, interview sources, read reports; AI: transcribe interviews
Work   : 🟦🟦🟦🟦  Human: Write draft
Review : 🟦🟦🟦🟦  Human: Edit draft, several close readings, verify facts, names, and data
Valid  : 🟦🟦🟦🟦  Human: Check all quotes against audio, use grammar/spellcheck tools
Final  : 🟦🟦🟦🟦  Human: Enter components and publish in system

Overall: ⬛🟦🟦🟦
- AI used only for research and transcription; all content human-written and verified
```

#### ii. Typical software-development or data-science policy


`````
AI-L2 [I2,D2,W3,R2,V2,F1]  

        ⚙️      🧍
Ideate : ⬛⬛🟦🟦  AI: Analyze approaches to solve problem; Human: Create engineering spec
Design : ⬛⬛🟦🟦  AI: Generate spec (claude.md, README.md); Human: Iterately improve spec
Work   : ⬛⬛⬛🟦  AI: Agent generates code; Human: Checks code suits purpose
Review : ⬛⬛🟦🟦  AI: Identify errors and propose fixes; Human: Identify issues to fix
Valid  : ⬛⬛🟦🟦  AI: Human identies logic and functionality issues; AI: Fix issues
Final  : ⬛🟦🟦🟦  Human: Determines final checks; AI: May be used to automate checks

Overall: ⬛⬛🟦🟦
- AI-assisted development with full human review and validation.
`````

#### iii. Typical AI Instantiated Workflow (such as chatbot request)

```
AI-L4 [I0,D2,W4,R3,V4,F4]
 
          ⚙️      🧍
Ideate   : 🟦🟦🟦🟦  Human: asks questions, defines intent
Design   : ⬛⬛🟦🟦  AI: intent parsing, routing; Human: refines request based on feedback
Work     : ⬛⬛⬛⬛  AI: generates answers, applies knowledge
Review   : ⬛⬛⬛🟦  AI: guardrails, filters; Human: limited oversight, responds to errors
Validate : ⬛⬛⬛⬛  AI: automated validation, although veracity hard to determine
Finalize : ⬛⬛⬛⬛  AI: delivers responses, user-facing output

Overall: ⬛⬛⬛⬛  
- Fully automated responses, no human validation, high legal risk
```



### e. HTML/JSON tags

For easy machine readability, the following schema can be used for embedded tags in web pages. Ideally, this would be generated and included by the CMS or other appropriate tool.

``` HTML
<p
  class="lemai-score"
  data-lemai-version="1.0"
  data-lemai-overall="2"
  data-lemai-ideate="2"
  data-lemai-design="2"
  data-lemai-work="3"
  data-lemai-review="2"
  data-lemai-validate="2"
  data-lemai-finalize="1"
  data-lemai-json='{
    "version": "1.0",
    "overall": 2,
    "stages": {
      "ideate": 2,
      "design": 2,
      "work": 3,
      "review": 2,
      "validate": 2,
      "finalize": 1
    }
  }'
>
  LEMAI: AI-L2 [I2,D2,W3,R2,V2,F1]
</p>
```



## Discussion

Over the past two years, concerns have increased over the use of AI to produce both creative works (articles, newsletters, and books) and functional works (software development and data science analyses). Different parties in the creative ecosystem have expressed different concerns, highlighting a significant problem: While AI usage is obviously a spectrum, no well-defined way exists to express different levels of usage.

Authors, for example, are worried about competing with AI slop. They are also worried about using any tools that incorporate AI because their resulting work my be identified as AI-generated. For an author, this could easily result in a publishing ban. Can an author use an LLM to brainstorm their book ideas? Can they use an AI-based editing service to edit their manuscript? The lack of granularity in policies has resulted in a lack of deeper consideration of these issues.

Software developers are at the opposite end of the spectrum. They aim to use AI as much as possible, but a human remains a necessary part of development. The question is what is the right balance? Again, a standardized way of talking about AI usage in the workflow can help advance the discussion.

This framework **does not intend to judge what is the appropriate level of AI usage** for a specific deliverable. Instead, the aim is to provide a language that can facilitate the discussion between content creators and their clients or audiences. Content creators can be transparent about their use of AI. Media outlets, businesses, and other organizations can be specific about their requirements and policy. Third-party providers of services can use the system to designate how their system may add AI artifacts into the workflow, or specify where AI was detected in the workflow. 

While companies have started producing templates for AI acceptable use policies, the problem is that these policies are non-standard, hard to parse, and far from transparent. They tend to satisfy compliance standards but do not clearlyt communicate AI usage to users and do not support per-workflow differences in AI usage. 

I hope this approach will solve that.



## Outstanding Issues

Here is an incomplete list of issues that are left to be resolved:

### 1. Self-declaration is a weakness

Relying on content creators to self-declare their use of AI is not rigorous. This framework relies on content creators wanting transparency. 

**Considerations:** The current format is intended for good-faith transparency of AI usage. Until — and if — AI detection technology evolves, or a rigorous pipeline is established that labels content with AI levels at each workflow stage, self declaration is the only way forward.

### 2. Current levels lack rigorous definitions

What constitutes Level 1 usage at the Design stage? What constitutes Level 2 at the Review stage. The framework currently lacks rigorous definitions of AI usage at each stage. 

**Consideration:** This will likely have to be considered and established through consensus. Initial definitions of AI usage at each stage will be published. After debate, I think they will eventually be hammered out and a grading methodology established through exemplars.



## Other Models and In-Depth Examples

The full framework document in the `docs/` folder has a comparison to other AI usage and maturity models and several in-depth examples of applying the LEMAI framework.



## Acknowledgments

I would like to thank Rik Farrow, Ming Chow, Dan Guido, and Fahmida Rashid for taking the time to review earlier drafts of this proposal and provide feedback. 
