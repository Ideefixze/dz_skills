---
name: dz-analyze
description: Skill describing a path agent should take when any analysis task is being performed or expected. Use when a heavy decision has to be taken, a conclusion has to be drawn or a detailed approach is needed. 
---

# dz-analyze

Analysis requires a deep and thorough scientific approach to the topic. The approach must not be biased by the internal LLM thought process and should be based on sources of truth that are made by other humans to reduce error and make decision-making easier.

First, a goal has to be set, like: 
- "Decide A vs B"
- "Find benefits of using X"
- "Is Y worth using in this project"
- "Does Z reach speed of 3.5 seconds per call".

After the goal is set, a few hypotheses have to be proposed by you that are both positive and negative:

- "use A",  "use B",  "use A but fallback to B", "use B but fallback to A", "use neither"
- "X is good for the performance",  "X is safe",  "X has health benefits",  "X is widely used by people",  "X costs are high compared to others",  "X can cause memory leaks",  "X hurts your liver"
- "Y can be used for...",  "Y shouldn't be used for..."
- "Z call takes 3.5 seconds every time", "Z call can take more than 3.5 seconds"

After the hypotheses are defined, you must find proofs that support each of the hypotheses. More proofs make hypotheses more strongly backed up, making a decision easier to make. Make a comprehensive list. NEVER provide your own internal knowledge, ALWAYS back it up by another source.

Find proofs that would be sources of truth for hypotheses, in:
- existing project files
- in external sources (webpages, books, blogs etc.)
- scientific papers (arXiv, Google Scholar etc.)
- experiments (running a simulation)
- real-world examples, use cases
- user's preference, local context
- common opinions on forums (Reddit, Stack Overflow etc.)

Gather all proofs for all hypotheses and show them in a single document (.md file).
Try to determine if certain source of truth might contain conflict of interest or a bias.
Do not go into specific details, instead, provide links or human-made sources of truth.
Then draw a final conclusion, by including all your findings. This conclusion should not be comprehensive - an abstract-sized text for human to get a general overview of the problem and a decision with short WHY and HOW.

## Instructions

1. Find a goal
2. Set hypotheses
3. Find proofs or rebuttals
4. Draw final conclusion

## Rules

1. Lack of proof is also knowledge
2. Human-made knowledge is 1000x more valuable than your own or created by the other LLM
3. Opinions are valid, but real numbers and university research are stronger proofs
4. Nothing wrong with asking questions - ASK, don't assume
5. Exploration is just as important as being correct
6. Context for analysis is just as important as other parts: don't make a hypothesis assuming a personal project is an enterprise application, and vice versa
7. Take into account conflict of interest - research sponsored by a company X will say that technology used by company X is safe.
