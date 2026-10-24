---
name: dz-new-feature
description: Skill describing how to create new feature. Use when user wants to: "add", "change", "fix" or "implement" something.
---

# dz-new-feature

Use following pattern:

1. Plan.
2. Interview.
3. Read.
4. Implement.
5. Critic.
6. Fix.

## When to use

Use when you need to implement a new feature, add something novel or make a significant change.

## Instructions

Perform steps in a given order, without ever going out of the loop:

1. Plan - determine scope (GLOSSARY: small/medium/large feature) and gather all required components.
2. Interview - ask user about WHAT needs to be build. Gather significant decision. Never assume user wants to do X if they didn't state it to you.
3. Read - read related codebase, find useful external packages, libraries or snippets. Never go blind!
4. Implement - write code down. Remember about general rules you need to follow.
5. Critic - never write code down thinking you are right. Read your implementation AGAIN.
  Ask yourself:
  - WHAT - what I just did?
  - WHY - why I did this? What was original goal?
  - HOW - how I did it? Is it a good implementation? Does it fit here?
  - UGLIES - what are drawbacks of my approach?
  - GOODIES - what I did right?
  - NO COMMENTS - is there lots of unnecessary comments? Does code comment itself?
  - RELATIONSHIPS - if I changed one feature, how does it affect other places in codebase? what about documentation?
  - VALIDATE - build and tests need to pass!
6. Fix - correct yourself based on answers in above questions.

**CRITICAL:** Do not stop the workflow. If user asks for another feature in same task, repeat the process!

### Code writting guide

1. No emojis! Never place emojis - text. TEXT!
2. Never use generic and over-verbose names for classes and methods - "process_text" is doing what? "CreatorSingleClientInvoiceFromUSA" is a shit naming too!
3. Do not ignore surrouding codebase - do not add apples to oranges. Try to fit with style to the codebase so it looks like one person was working on it!
4. Try/except (or try/catch) wrapped around everything is a bad practice!
5. Have some personality.
6. Calls that exist. Generated code invents plausible APIs. Plan to run it and check every import and method against real docs, because hallucinated calls are the tell that bites in production.

### Commenting guide

1. Comments should not duplicate the code.
2. Good comments do not excuse unclear code.
3. If you can't write a clear comment, there may be a problem with the code.
4. Comments should dispel confusion, not cause it.
5. Explain unidiomatic code in comments.
6. Provide links to the original source of copied code.
7. Include links to external references where they will be most helpful.
8. Add comments when fixing bugs.
9. Use comments to mark incomplete implementations.
10. Follow official Python/JS/C#/C++/Rust/GO documentation, commenting rules (JSDoc, Pydoc etc.)
