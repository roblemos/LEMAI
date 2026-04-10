# Labeling and Evaluating Modes of AI Usage (LEMAI): Short Description

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



## Current Maturity Model Landscape

You can't drop a hat without hitting a maturity model these days. So far, the models for human-AI collaboration created by Gartner, Google, Microsoft, and OpenAI typically focus on overall enterprise-level adoption, integration, and maturity, and not workflow and deliverables, so I thought there would be space for another taxonomy/system.

### 1. Google's People + AI Guidebook

Reference: [Web site](https://pair.withgoogle.com/guidebook/)

Google’s People + AI (PAIR) Guidebook is a **design framework for human-centered AI systems**, focusing on UX principles like explainability, trust, feedback, and error handling. It helps teams build AI products that are usable and understandable, emphasizing how humans interact with AI rather than how AI is adopted or measured. In contrast, the LEMAI framework evaluates **where and how AI is used within workflows**, providing a structured, stage-based transparency and accountability lens.

- **Similarities:** Both emphasize responsible AI, human oversight, and trust in outputs
- **Differences:** Google = UX/design guidance for AI systems; LEMAI = workflow-level classification and usage transparency

### 2. AI Acceptable Use Policies (AUPs)

Reference: [TechTarget](https://www.techtarget.com/searchsecurity/tip/How-to-create-an-AI-acceptable-use-policy-plus-template); [Tenable](https://www.tenable.com/blog/security-for-ai-a-practical-guide-to-enforcing-your-ai-acceptable-use-policy)

AI Acceptable Use Policies (AUPs) — two examples from TechTarget and Tenable are linked above — are **governance frameworks that define how employees and systems are allowed to use AI tools** within an organization. They focus on risk management, compliance, and security controls, covering areas such as data handling, approved tools, prohibited use cases, and monitoring. These policies are designed to prevent misuse and reduce organizational risk. In contrast, the LEMAI framework evaluates how AI is actually used within a workflow, providing a transparent, stage-by-stage classification of AI involvement and associated risks rather than prescribing allowed behavior.

- **Similarities:** Both emphasize responsible AI use; address risk and governance; support organizational transparency; can be standardized and applied across teams
- **Differences:** AUPs = prescriptive rules and controls for AI usage; LEMAI = descriptive model of actual AI usage within workflows; AUPs define what should be allowed, while LEMAI reveals what actually happened and where risks exist

### 3. Gartner's AI Maturity Model & Roadmap Toolkit

Reference: [Web site](https://www.gartner.com/en/chief-information-officer/research/ai-maturity-model-toolkit)

Gartner’s AI Maturity Model & Roadmap Toolkit is an **enterprise planning framework** that benchmarks organizations across stages of AI maturity and provides a roadmap for scaling AI capabilities. It focuses on **strategy, governance, operating models, and investment alignment**, helping leaders prioritize initiatives and close capability gaps. In contrast, the LEMAI framework evaluates **AI usage within specific workflows**, offering granular transparency into how AI contributes at each stage rather than guiding enterprise transformation.

- **Similarities:** Both classify AI maturity; emphasize progression, governance, and responsible use
- **Differences:** Gartner = strategic roadmap and capability benchmarking; LEMAI = workflow-level usage classification and transparency scoring

### 4. ToS;DR Privacy Ratings

**Reference:** [Terms of Service; Didn't Read](https://tosdr.org/)

ToS;DR (Terms of Service; Didn’t Read) is a **community-driven privacy and terms-of-service rating system** that evaluates websites and services based on how their policies affect users. It assigns **letter grades (A–E)** derived from a set of analyzed clauses (e.g., data sharing, tracking, user rights), translating complex legal documents into a simplified, user-friendly score. The framework focuses on **user risk and fairness of policies**, helping people quickly understand whether a service respects their privacy. In contrast, the LEMAI framework evaluates **how AI is used within a workflow**, providing a structured, stage-by-stage breakdown of AI involvement and associated risks rather than judging the quality of a policy.

- **Similarities:** Both simplify complex systems into accessible scores; aim to improve transparency and user understanding; enable comparisons across entities; can be represented visually (grades vs. stage matrix)
- **Differences:** ToS;DR = evaluates **policy outcomes and user risk** using external analysis; LEMAI = describes **process behavior and AI usage** via self-disclosed workflow scoring; ToS;DR uses a **single aggregate grade**, while LEMAI provides a **multi-dimensional, stage-level breakdown** with explicit risk modeling

### 5. Content Credentials

**Reference:** [Adobe's Content Credentials site](https://helpx.adobe.com/creative-cloud/apps/adobe-content-authenticity/content-credentials/overview.html)

Content Credentials (from the Coalition for Content Provenance and Authenticity) are a **provenance and authenticity framework** that attaches cryptographically verifiable metadata to digital assets, documenting how content was created, edited, and by whom. It focuses on **file-level transparency and trust**, enabling verification of content origin and modification history. In contrast, the LEMAI framework evaluates **AI usage within workflows**, providing a stage-by-stage view of how AI contributes to content creation and where associated risks arise.

- **Similarities:** Both promote transparency and trust; distinguish human vs. AI involvement; support standardization; align with attribution and verification principles
- **Differences:** Content Credentials = **cryptographically verifiable provenance at the asset level**; LEMAI = **self-declared, workflow-level AI usage and risk model**; Content Credentials track *what happened to a file*, while LEMAI explains *how AI was used and where risks exist***

### 6. Google Cloud’s AI Adoption Framework 

Reference: [PDF](https://services.google.com/fh/files/misc/ai_adoption_framework_whitepaper.pdf)

Google Cloud’s AI Adoption Framework is a **maturity model for organizational AI capability**, mapping progress across themes like Learn, Lead, Scale, and Automate and phases from tactical to transformational . It evaluates **people, process, data, and technology readiness**, not specific workflows. In contrast, the LEMAI framework evaluates **AI usage within discrete workflows (I→F stages)**, focusing on transparency and accountability at the task level rather than enterprise capability.

- **Similarities:** Both classify AI maturity; emphasize progression, structure, and responsible adoption
- **Differences:** Google = org-level capability model; LEMAI = workflow-level usage and transparency scoring

### 7. OpenAI's' Human-in-the-Loop Spectrum

Reference: [Web site](https://openai.github.io/openai-agents-python/human_in_the_loop/)

OpenAI’s Human-in-the-Loop Spectrum defines **levels of human involvement in AI systems**, from full human control to autonomous agents with optional oversight. It focuses on **control, intervention points, and safety boundaries** in agent workflows, helping developers decide when humans should review, approve, or override AI actions. In contrast, the LEMAI framework evaluates **how much AI contributes across workflow stages**, emphasizing transparency and accountability rather than control mechanisms.

- **Similarities:** Both assess human vs AI roles; emphasize oversight, responsibility, and safe usage
- **Differences:** OpenAI = control spectrum within agent systems; LEMAI = stage-based workflow classification and transparency scoring

### 8. Microsoft's Guidelines for Human-AI Interaction

Reference: [Web site](https://www.microsoft.com/en-us/research/project/guidelines-for-human-ai-interaction/)

Microsoft’s Human-AI Interaction Guidelines are a **design and UX framework** outlining best practices for how AI systems should behave across stages (e.g., initial interaction, ongoing use, error handling). They emphasize **user expectations, transparency, feedback, and trust**, guiding how AI communicates and collaborates with humans over time. In contrast, the LEMAI framework evaluates **AI usage within workflows**, quantifying where AI contributes and how responsibility is distributed, rather than prescribing interaction behaviors.

- **Similarities:** Both emphasize transparency, trust, and clear human-AI roles
- **Differences:** Microsoft = interaction design principles for AI systems; LEMAI = workflow-level classification and usage transparency scoring

### 9. McKinsey's AI Governance and Maturity model

Reference: [Web site](https://www.mckinsey.com/capabilities/tech-and-ai/our-insights/tech-forward/state-of-ai-trust-in-2026-shifting-to-the-agentic-era)

McKinsey’s AI maturity model (as reflected in its State of AI research) is an **enterprise-level benchmarking framework**that assesses how organizations progress from experimentation to scaled, value-generating AI—now evolving toward **agentic AI systems embedded in operations**. It emphasizes **business impact, governance, trust, and scaling AI across functions**, helping executives align strategy, talent, and risk management. In contrast, the LEMAI framework evaluates **AI usage within specific workflows**, focusing on transparency, stage-level contribution, and accountability rather than organizational transformation.

- **Similarities:** Both emphasize maturity progression, trust, and responsible AI adoption
- **Differences:** McKinsey = enterprise adoption and value realization; LEMAI = workflow-level usage classification and transparency scoring

 

## Examples Scoring of Some AI-Usage Policies

### Arnold’s Pump Club Editorial Standards

Reference: [Web site](https://arnoldspumpclub.com/blogs/newsletter/arnold-schwarzenegger-s-200-000-gamble-and-how-one-word-keeps-him-focused)

> ...
> 
>Does AI play a role? Not for the primary content, but it is used in two ways. The main items are original content written by the APC team. The summaries at the end are AI-generated based on the human-written content above. We also use an AI tool to review our interpretations of the research and ensure scientific accuracy. We don’t assume AI is right, but we use technology to hold ourselves accountable.
> 
>...

```
AI-L1 [I1,D0,W0,R1,V1,F0]

        ⚙️      🧍
Ideate : ⬛🟦🟦🟦 AI: Limited summarizing; Human: Research, select topics, and frame editorial
Design : 🟦🟦🟦🟦 Human: Writes all core articles, commentary, and editorial pieces
Work   : 🟦🟦🟦🟦 Human: Fully responsible for producing, editing, and structuring content
Review : ⬛🟦🟦🟦 AI: Flags possible inaccuracies; Human: Evaluate AI feedback, apply edits
Valid  : ⬛🟦🟦🟦 AI: Assist interpreting accuracy; Human: Check facts, validate sources
Final  : 🟦🟦🟦🟦 Human: Makes all final calls on content, partnerships, and publication

Overall: ⬛🟦🟦🟦
- AI assists in some research and content-checking capacity; humans produce content and have tight control over editorial
```



### Quanta Magazine's AI Editorial Policy

Reference: [Web site](https://www.quantamagazine.org/ai-editorial-policy/)

> ...
>
> Artificial intelligence is not just a potential tool in our newsroom. It’s part of our mission to understand AI, [cover advances in the field](https://www.quantamagazine.org/tag/artificial-intelligence/) and [explain its origins and impact](https://www.quantamagazine.org/series/science-in-the-age-of-ai/) to our readers. We have been covering AI since well before GenAI tools became widely available, so we understand its capabilities, limitations and potential, and follow changes closely.
>
> ...

```
AI-L1 [I1,D1*,W0,R0,V0,F0]*

        ⚙️      🧍
Ideate : ⬛🟦🟦🟦  AI: background info, tools; Human: framing, reporting, direction  
Design : ⬛🟦🟦🟦  AI: minor assistance; Human: structure, editorial planning*  
Work   : 🟦🟦🟦🟦  Human: writing, creation, storytelling  
Review : 🟦🟦🟦🟦  Human: editing, revising, oversight  
Valid  : 🟦🟦🟦🟦  Human: fact-checking, verification, accuracy  
Final  : 🟦🟦🟦🟦  Human: publishing, formatting, accountability  
* Not enough information to determine AI-usage level

Overall: ⬛🟦🟦🟦  
- Human-led journalism, minimal AI assistance, strict editorial control
```



### Every.to's Editorial Guidelines

Reference: [Web site](https://every.to/guides/editorial-guidelines)

> ...
>
> AI is an integral part of how we achieve this mission. As AI develops, so has our use and the standards that we apply. These guidelines are meant to make our processes transparent and will evolve as we continue to experiment.
>
> ...

```
AI-L2 [I2,D2*,W2,R2,V2*,F1]

⬛ = AI-driven  
🟦 = Human-driven  

        ⚙️      🧍
Ideate : ⬛⬛🟦🟦  AI: brainstorming, research prompts; Human: direction, framing
Design : ⬛⬛🟦🟦  AI: suggest structure; Human: define editorial standards *
Work   : ⬛⬛🟦🟦  AI: draft text, metaphors; Human: author voice, shape
Review : ⬛⬛🟦🟦  AI: refine clarity, headlines; Human: edit, approve
Valid  : ⬛⬛🟦🟦  AI: analyze performance; Human: fact-check, accountability *
Final  : ⬛🟦🟦🟦  AI: formatting support; Human: publish, sign-off

* Not enough information to determine AI-usage level

Overall: ⬛⬛🟦🟦  
- Human-led writing with strong AI collaboration across stages
```



### Trail of Bits AI-Native Audit System Workflow

Reference: [Column](https://tldrsec.com/p/how-we-made-trail-of-bits-ai-native-so-far)

> ...
>
> At Trail of Bits, what this means concretely: our security expertise compounds as code. Every engagement we do, the skills and workflows we build make the next engagement faster. Every engineer operates with an arsenal of specialized agents built from 14 years of audit knowledge. That's not "we use AI." That's "AI is on the team."
>
> ...

#### Implied Workflow (AI-Native Audit System)

Since Trail of Bits does not have a stated policy, I tasked an LLM to create one based on the column by Clint Gibler and Dan Guido (linked above). It noted that the post describes a system-level workflow, not a single task and identified the implied workflow as:

##### 1. Ideation (Problem Framing + Targeting)

- Humans define audit scope, risks, and goals
- AI agents help explore attack surfaces and generate hypotheses

##### 2. Design (Workflow + Agent System Design)

- Humans design workflows, guardrails, and constraints
- AI contributes reusable “skills,” configs, and prior patterns

##### 3. Work (Execution via Agents)

- AI agents run analysis across codebases in parallel
- AI generates findings, drafts reports, surfaces vulnerabilities
- Humans orchestrate agents and guide execution

##### 4. Review (Human + AI Iteration)

- AI performs first-pass triage and clustering of issues
- Humans review outputs, refine, and prioritize findings

##### 5. Validation (Critical Human Oversight)

- Humans validate all findings before client delivery
- AI may assist with cross-checking or reproducing issues

##### 6. Finalization (Delivery + Knowledge Capture)

- Humans finalize reports and communicate results
- AI systems capture workflows as reusable “skills” and artifacts
- Outputs feed back into the system (compounding knowledge)

```
AI-L3 [I2,D2,W3,R3,V2,F2]

        ⚙️      🧍
Ideate : ⬛⬛🟦🟦  AI: surface risks, hypotheses; Human: scope, priorities  
Design : ⬛⬛🟦🟦  AI: reuse patterns, configs; Human: workflows, constraints  
Work   : ⬛⬛⬛🟦  AI: run agents, find bugs; Human: orchestrate, guide  
Review : ⬛⬛⬛🟦  AI: triage, cluster findings; Human: refine, prioritize  
Valid  : ⬛⬛🟦🟦  AI: assist checks; Human: verify, approve findings  
Final  : ⬛⬛🟦🟦  AI: package artifacts, reuse; Human: deliver, communicate  

Overall: ⬛⬛⬛🟦  
- AI agents execute audits; humans orchestrate, validate, and deliver
```



### New York City Small Business Chatbot

**Reference:** [The Markup](https://themarkup.org/artificial-intelligence/2024/03/29/nycs-ai-chatbot-tells-businesses-to-break-the-law)

#### Full Workflow Summary (Compact)

The demonstrates the utility of the LEMAI evaluation process for end-to-end automated workflows, an example of which are bespoke chatbot services. Using the description of the NYC chatbot from the linked article, the workflow of the chatbot is:

1. **Ideate** — User asks a business/legal question
2. **Design** — AI interprets intent + constructs response approach
3. **Work** — LLM generates answer (with possible hallucination)
4. **Review** — Weak or ineffective guardrails applied
5. **Validate** — No real validation against legal ground truth
6. **Finalize** — Output delivered as authoritative advice

**Note:** The LEMAI framework does not measure correctness, just AI involvement, so the fact the the Review and Validate stages are poor quality has no bearing on their scores. However, full automation with poor review and validation suggest high legal risk, as noted.

```
AI-L4 [I0,D3*,W4,R2*,V4,F4]
 
          ⚙️      🧍
Ideate   : 🟦🟦🟦🟦  Human: asks questions, defines intent
Design   : ⬛⬛⬛🟦  AI: intent parsing, routing; Human: system setup*
Work     : ⬛⬛⬛⬛  AI: generates answers, applies knowledge
Review   : ⬛⬛🟦🟦  AI: guardrails, filters; Human: limited oversight*
Validate : ⬛⬛⬛⬛  AI: automated validation, ineffective checks
Finalize : ⬛⬛⬛⬛  AI: delivers responses, user-facing output

* Not enough information to determine AI-usage level

Overall: ⬛⬛⬛⬛  
- Fully automated responses, no human validation, high legal risk
```



## Acknowledgments

I would like to thank Rik Farrow, Ming Chow, Dan Guido, and Fahmida Rashid for taking the time to review earlier drafts of this proposal and provide feedback. 
