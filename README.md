
# How to Use (Quick Start)

1) Load the YAML into the chat  
   - Upload **ChatGPTdecorators.yml** to the conversation.  
   - Send:  
     ```
     Read ChatGPTdecorators.yml as instructions
     ```  
   - ChatGPT is flexible about parsing; this line is usually enough to activate the decorators.

2) Verify it’s loaded  
   - Send:
     ```
     @@Help
     ```
   - You should see a header with author/version and a list of decorators.

3) Use decorators  
   - Examples:
     ```
     @@chat @@Tone(technical) @@StepByStep
     Explain neutrino oscillations for a graduate audience.
     ```
     ```
     @@message @@OutputFormat(json)
     Summarize the following text in one JSON object with keys: tl;dr, key_points.
     ```

4) In isolated/non-member projects (with a Files section + Instructions box)  
   - Upload **ChatGPTdecorators.yml** under Files.  
   - In the **Instructions** box add:  
     ```
     Read ChatGPTdecorators.yml as instructions
     ```  
   - Then test with `@@Help`.

5) Always fetch the latest version  
   - Check the repo for updates before you start a new session:  
     **GitHub (latest):** https://github.com/Amidn/ChatGPT-decorators


     
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
The `Tone` decorator instructs the model to adopt a specific tone in its response, such as formal, friendly, or humorous.

```markdown
@@Tone(friendly)
Welcome a new user to the platform.
```
