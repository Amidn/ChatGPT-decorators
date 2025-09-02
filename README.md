# Table of Contents
- [Activate Decorators](#activate-decorators)
  - [Quick Start](#quick-start)
- [Decorators Overview](#decorators-overview)

# Activate Decorators

> **Quick Start**
>
> 1) Upload **ChatGPTdecorators.yml** (located in the Source folder) to the conversation and send:
>    ```
>    Read ChatGPTdecorators.yml as instructions
>    ```
>    
>    OR
>    
>    ```
>    Read, update and remember instructions based on ChatGPT decorators.yml file.
>    ```
>    (ChatGPT is fairly flexible about parsing; this is typically enough.)
>
> 2) Verify:
>    ```
>    @@Help
>    ```
>    You should see a meta header (author, version, GitHub) and the list of decorators.
>
> 3) Use decorators:
>    ```
>    @@chat @@Tone(technical) @@StepByStep
>    Explain neutrino oscillations for a graduate audience.
>    ```
>    ```
>    @@message @@OutputFormat(json)
>    Summarize the following text in one JSON object with keys: tl;dr, key_points.
>    ```
>
> 4) **Isolated / non-member projects** (Files + Instructions):
>    - Upload **ChatGPTdecorators.yml** to Files.
>    - In the Instructions box add:
>      ```
>      Read ChatGPTdecorators.yml as instructions
>      ```
>    - Test with `@@Help`.
>
> 5) **Stay up to date**: always check the latest version  
>    GitHub (latest): https://github.com/Amidn/ChatGPT-decorators

---

# Decorators Overview

## chat
The `chat` decorator enables conversational context, allowing the model to maintain memory of previous messages in a chat-like interaction.

```markdown
@@chat
You are a helpful assistant. Remember the user's preferences and respond accordingly.
```

## message
The `message` decorator is used to specify a single message or instruction for the model to respond to, without maintaining conversational context.

```markdown
@@message
Summarize the following article in one paragraph.
```

## clear
The `clear` decorator resets or clears the conversation history, ensuring the next response is generated with no prior context.

```markdown
@@clear
Forget all previous instructions and start fresh.
```

## Help
The `Help` decorator instructs the model to provide assistance or guidance on a specific topic or feature.

```markdown
@@Help
Explain how to use the search function in this application.
```

## InProcess
The `InProcess` decorator is used to indicate that a task is ongoing or to provide updates about a process that has not yet completed.

```markdown
@@InProcess
Currently gathering data. Please wait while I complete the analysis.
```

## FactCheck
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

## Polish
The `Polish` decorator asks the model to improve the clarity, grammar, and style of a given text without changing its meaning.

```markdown
@@Polish
this is a text with bad grammar and spelling. please fix it
```

## StepByStep
The `StepByStep` decorator instructs the model to break down its response into clear, logical steps.

```markdown
@@StepByStep
How do I change a flat tire?
```

## Reasoning
The `Reasoning` decorator prompts the model to show its reasoning process explicitly, making its logic and thought process transparent.

```markdown
@@Reasoning
Why is the sky blue?
```

## Assessment
The `Assessment` decorator asks the model to evaluate or critique something, such as an argument, plan, or piece of writing.

```markdown
@@Assessment
Assess the strengths and weaknesses of this business proposal.
```

## Synthesize
The `Synthesize` decorator instructs the model to combine information from multiple sources or ideas to create a cohesive summary or new insight.

```markdown
@@Synthesize
Combine the following articles into a single summary.
```

## RiskReport
The `RiskReport` decorator tells the model to identify and explain potential risks associated with a plan, decision, or scenario.

```markdown
@@RiskReport
What are the risks of investing in cryptocurrency?
```

## Confirm
The `Confirm` decorator asks the model to verify or validate information, instructions, or user input.

```markdown
@@Confirm
Did you receive my last message?
```

## OutputFormat
The `OutputFormat` decorator specifies the desired format for the model's output, such as JSON, table, or bullet points.

```markdown
@@OutputFormat(table)
List the top 5 programming languages and their main uses.
```

## Tone
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


## CodeCheck

The `CodeCheck` decorator analyzes code (any language, any size) to detect bugs, errors, mismatches, or incompatibilities.
It does not refactor or suggest improvements—it only reports problems.


```markdown
@@CodeCheck(language=python, strict=true)
import numpy as np
np.arange(5).shape()
```



## CodeGen
The `CodeGen` decorator generates **code, modules, or entire package scaffolds**.  
It can create a blueprint, scaffold, full implementation, repo extension, or shims between components.  
By default, it produces runnable code with tests and safe defaults.

```markdown
@@CodeGen(mode=scaffold, language=python, targets=['library','cli'])
Build an 'analysis' package with unit tests and CI.
```


## LangCoach
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