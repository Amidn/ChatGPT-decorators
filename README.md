# Table of Contents
- [Activate Decorators](#activate-decorators)
  - [Quick Start](#quick-start) — Load Decorators, Verify Setup, Use Decorators, ChatGPT Plus Project, Stay Up to Date
- [Decorators Overview](#decorators-overview)
  - [Controller decorators](#controller-decorators) — chat, message, clear, Help, InProcess
  - [Verification decorators](#verification-decorators) — FactCheck, CiteSources, CodeCheck, MedProof
  - [Structure decorators](#structure-decorators) — Polish, StepByStep
  - [Method decorators](#method-decorators) — Reasoning, Assessment, Synthesize, CodeGen
  - [Error-handling decorators](#error-handling-decorators) — RiskReport
  - [User-confirmation decorators](#user-confirmation-decorators) — Confirm
  - [Output & Tone decorators](#output--tone-decorators) — OutputFormat, Tone
  - [Language-learning decorators](#language-learning-decorators) — LangCoach
# Activate Decorators

  ## Quick Start

  ### Load Decorators
 
```markdown
Read ChatGPTdecorators.yml as instructions
```

**OR**

```markdown
Read, update and remember instructions based on ChatGPT decorators.yml file.
```
(ChatGPT is fairly flexible about parsing; this is typically enough.)
 
  ### Verify Setup 

   Verify using:
     ```
     @@Help
     ```
     You should see a meta header (author, version, GitHub) and the list of decorators.
 
  ### Use decorators 
     ```
     @@chat @@Tone(technical) @@StepByStep
     Explain neutrino oscillations for a graduate audience.
     ```
     ```
     @@message @@OutputFormat(json)
     Summarize the following text in one JSON object with keys: tl;dr, key_points.
     ```
  ### ChatGPT Plus Project
   **Isolated / non-member projects** (Files + Instructions):
     - Upload **ChatGPTdecorators.yml** to project files.
     - In the Instructions box add:
       ```
       Read ChatGPTdecorators.yml as instructions
       ```
     - Test with `@@Help`.
 
  ### Stay up to date
  
    always check the latest version  
     GitHub (latest): https://github.com/Amidn/ChatGPT-decorators

---

# Decorators Overview

## Controller decorators

### chat
The `chat` decorator enables conversational context, allowing the model to maintain memory of previous messages in a chat-like interaction.

```markdown
@@chat
You are a helpful assistant. Remember the user's preferences and respond accordingly.
```

### message
The `message` decorator is used to specify a single message or instruction for the model to respond to, without maintaining conversational context.

```markdown
@@message
Summarize the following article in one paragraph.
```

### clear
The `clear` decorator resets or clears the conversation history, ensuring the next response is generated with no prior context.

```markdown
@@clear
Forget all previous instructions and start fresh.
```

### Help
The `Help` decorator instructs the model to provide assistance or guidance on a specific topic or feature.

```markdown
@@Help
Explain how to use the search function in this application.
```

### InProcess
The `InProcess` decorator is used to indicate that a task is ongoing or to provide updates about a process that has not yet completed.

```markdown
@@InProcess
Currently gathering data. Please wait while I complete the analysis.
```


## Verification decorators

### FactCheck
The `FactCheck` decorator instructs the model to verify the accuracy of statements or claims, and provide sources or corrections if necessary.

```markdown
@@FactCheck
Is it true that the Great Wall of China is visible from space?
```

## CiteSources
The `CiteSources` decorator tells the model to include citations or references for any factual information provided in its response.

```markdown
@@CiteSources
List three recent studies about the effects of caffeine, and cite your sources.
```


### CodeCheck

The `CodeCheck` decorator analyzes code (any language, any size) to detect bugs, errors, mismatches, or incompatibilities.
It does not refactor or suggest improvements—it only reports problems.


```markdown
@@CodeCheck(language=python, strict=true)
import numpy as np
np.arange(5).shape()
```

### MedProof
The `MedProof` decorator (aliases: `@@MedFacts`, `@@ClinCheck`, `@@MedCheck`) performs evidence-focused health queries using only clinically credible sources. It **always** prints a bold disclaimer at the top, then outputs three clearly separated sections with horizontal rules.

**What it does**
- Searches reputable medical sources (e.g., Cochrane, WHO, NICE, FDA/EMA labels, NIH/CDC, PubMed-indexed RCTs and systematic reviews).
- Prioritizes high-quality evidence (guidelines/meta-analyses/RCTs), with optional filters for region, recency, and minimum evidence grade.
- Quantifies real-world impact when available (ARR/RRR, NNT/NNH), and states external-validity limits (e.g., lab vs. typical use).
- Flags hype, advertising claims, and common myths in a dedicated caveat section.
- Lists key contraindications/red flags and reminds the reader to seek professional care.
- Ends with a concise, practical conclusion.

**Always-printed disclaimer (appears first)**
**This summary is for information only, not medical advice. Always consult a clinician.**  
**The internet has misleading claims; use caution.**

**Output format (three sections separated by lines)**
1) **Evidence-based Findings**  
   ---
2) **Caveats & Fake Claims**  
   ---
3) **Conclusion & Practical Notes**  
   ---

**Usage examples**

```markdown
@@MedProof
Is caffeine shampoo effective for androgenic alopecia?
```

```markdown
@@MedProof(region=EU, recency_years=5, min_evidence_grade=A)
Do weight-loss "metabolism patches" work?
```

**Parameters (optional)**
- `region`: `auto|US|EU|UK|WHO` (prefer guidelines/evidence from that region)
- `recency_years`: integer (default `7`)
- `min_evidence_grade`: `A|B|C` (default `B`; A=guidelines/systematic reviews, B=RCTs, C=observational/consensus)
- `include_rcts_only`: boolean (default `false`)
- `report_effect_size`: boolean (default `true`)
- `fake_news_scan`: boolean (default `true`)
- `contraindications`: boolean (default `true`)

## Structure decorators

### Polish
The `Polish` decorator asks the model to improve the clarity, grammar, and style of a given text without changing its meaning.

```markdown
@@Polish
this is a text with bad grammar and spelling. please fix it
```

### StepByStep
The `StepByStep` decorator instructs the model to break down its response into clear, logical steps.

```markdown
@@StepByStep
How do I change a flat tire?
```

## Method decorators

### Reasoning
The `Reasoning` decorator prompts the model to show its reasoning process explicitly, making its logic and thought process transparent.

```markdown
@@Reasoning
Why is the sky blue?
```

### Assessment
The `Assessment` decorator asks the model to evaluate or critique something, such as an argument, plan, or piece of writing.

```markdown
@@Assessment
Assess the strengths and weaknesses of this business proposal.
```

### Synthesize
The `Synthesize` decorator instructs the model to combine information from multiple sources or ideas to create a cohesive summary or new insight.

```markdown
@@Synthesize
Combine the following articles into a single summary.
```

### CodeGen
The `CodeGen` decorator generates **code, modules, or entire package scaffolds**.  
It can create a blueprint, scaffold, full implementation, repo extension, or shims between components.  
By default, it produces runnable code with tests and safe defaults.

```markdown
@@CodeGen(mode=scaffold, language=python, targets=['library','cli'])
Build an 'analysis' package with unit tests and CI.
```

## Error-handling decorators

### RiskReport
The `RiskReport` decorator tells the model to identify and explain potential risks associated with a plan, decision, or scenario.

```markdown
@@RiskReport
What are the risks of investing in cryptocurrency?
```


## User-confirmation decorators

### Confirm
The `Confirm` decorator asks the model to verify or validate information, instructions, or user input.

```markdown
@@Confirm
Did you receive my last message?
```


## Output & Tone decorators

### OutputFormat
The `OutputFormat` decorator specifies the desired format for the model's output, such as JSON, table, or bullet points.

```markdown
@@OutputFormat(table)
List the top 5 programming languages and their main uses.
```

### Tone
The `Tone` decorator instructs the model to adopt a specific tone in its response.

**Available styles**
- `formal`
- `casual`
- `friendly`
- `technical`
- `humorous`
- `neutral`
- `scientific`
- `academic`
- `argumentation`
- `educational`
- `motivational`
- `storyteller`
- `meditational`

**Examples**

```markdown
@@Tone(friendly)
Welcome a new user to the platform.
```

```markdown
@@Tone(scientific)
Explain neutrino oscillations, using precise terminology and evidence-based statements.
```

```markdown
@@Tone(academic)
Draft a 150-word abstract on black hole thermodynamics with formal style.
```

```markdown
@@Tone(argumentation)
Defend the use of Bayesian inference in astrophysical data analysis with clear premises and a conclusion.
```

```markdown
@@Tone(motivational)
Write a short note encouraging a student before exams.
```

```markdown
@@Tone(storyteller)
Describe the birth of the universe as a short narrative for a general audience.
```

```markdown
@@Tone(meditational)
Guide a brief, calming breathing exercise in 5 lines.
```

## Language-learning decorators




### LangCoach
The `LangCoach` decorator is designed for language learning.  
It asks a simple question in the target language, and the learner replies in either the target or their native language (depending on level).  
This encourages active practice and self-expression.

**Usage examples**

```markdown
@@LangCoach(English)
```


Question (in English):
Do you think it is more important to save money for the future, or to spend it now to enjoy life? Why?

Instructions:
Please write about one paragraph (or more if you wish) in English. After your reply, I will give you detailed feedback on grammar, word choice, expressions, and overall clarity, and then ask you a follow-up question.


```markdown
@@LangCoach(German, news)
```
Frage (auf Deutsch):
Was ist für dich wichtiger: mehr Geld zu verdienen oder mehr Freizeit zu haben? Warum?

👉 Bitte antworte in Deutsch mit ungefähr einem Absatz (oder zwei, wenn du möchtest). Danach gebe ich dir Feedback zu Grammatik, Wortwahl, Redewendungen und Vorschläge für bessere Alternativen – plus eine kurze Zusammenfassung und eine Anschlussfrage.
