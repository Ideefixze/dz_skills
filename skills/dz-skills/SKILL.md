---
name: dz-skills
description: A general introduction to Dominik's (aka "dz-*") skillset for AI personal coding. Always use as a good starting point for any task related to programming, implementation or analytical work.
---

# dz_skills

This skill briefly describes all skills that should be used together for creating personal projects efficently.
Projects created by this skillset will be well designed, maintanable, expandable, easy to read and play around with.
Skills are related, meaning they are best used together in a single task, where they can shine.

This skill also describes common usage paths and definitions that are used in particular skills.

## Skillset usage

### Glossary

Small feature - 1-3 files need to be modified, low scope.
Medium feature - 3-8 files need to be modifed. Needs extra attention.
Big feature - 8+ files need to be modified. All code that is produced in this feature needs to be strictly controlled.

Question - a single query to the user that describes the problem shortly, straight to the point and a question/decision user has to make.
Interview - a series of questions from AI agent to the user.
Decision - a choice between A or B. A free text describing a selected solution.

### Common usage patterns

1. New project? -> dz-interview + dz-boilerplate + dz-unslop to cleanup README.md
2. Feature? -> dz-interview + dz-new-feature
3. Writing content? -> dz-unslop
4. Creating a new non-trivial feature -> dz-interview + dz-analyze + dz-new-feature
5. Research topic -> dz-analyze + dz-unslop

Use skills freely and don't forget the rules defined in this main dz-skills skill.
This is the most important **CORE** skill to follow in all cases, because it describes a communication protocol and a general usage od other dz-* skills.

### General rules

1. NARUTO - Never Apply Rules Unquestioningly; Think & Observe
2. DRY - Every piece of knowledge must have a single, unambiguous, authoritative representation within a system
3. MOIST - Maximum Optimization Implies the Simplest Thing
4. KISS - don't overcomplicate, Keep It Simple Stupid!
5. APO - Avoid Premature Optimization, do not optimize too early unless task specifies you to do it!

6. LoD - Law of Demeter, don't talk to strangers, do not make method chains!
7. Orthogonality - things that are not related conceptually should not be related in the system
8. Maximise Cohesion - maximise the degree to which its responsibilities form a meaningful unit.
9. Liskov Substitution Principle - objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program.
10. Open/Closed - software entities (e.g. classes) should be open for extension, but closed for modification. Such an entity can allow its behavior to be modified, without altering its source code.
11. Curly's Law - single goal for a single piece of code.

Apply those rules to EACH code you write down. After making even the smallest change, like fixing a tiny bug or making a one line method, CHECK if those rules won't be broken by your change.

Example:

```
from abc import ABC, abstractmethod
from dataclasses import dataclass


@dataclass(frozen=True)
class Product:
    name: str
    price: float


class PricedItem(ABC):
    @abstractmethod
    def total_price(self) -> float:
        pass


@dataclass(frozen=True)
class RegularItem(PricedItem):
    product: Product
    quantity: int

    def total_price(self) -> float:
        return self.product.price * self.quantity


@dataclass(frozen=True)
class DiscountedItem(PricedItem):
    product: Product
    quantity: int
    discount: float

    def total_price(self) -> float:
        subtotal = self.product.price * self.quantity
        return subtotal * (1 - self.discount)


def calculate_cart_total(items: list[PricedItem]) -> float:
    return sum(item.total_price() for item in items)


if __name__ == "__main__":
    book = Product("Book", 20.0)
    pen = Product("Pen", 5.0)

    cart = [
        RegularItem(book, quantity=2),
        DiscountedItem(pen, quantity=3, discount=0.20),
    ]

    print(f"Cart total: ${calculate_cart_total(cart):.2f}")
```

For code above the fulfilment of rules are:

1. NARUTO --- Think and Observe: The design uses only abstractions
   that help meet the stated requirements and avoids unnecessary
   infrastructure. Agent asked few questions to confirm the user need.
2. DRY --- Don't Repeat Yourself: Product details and cart
   aggregation each have a single authoritative representation,
   although the simple subtotal formula appears in both item classes.
3. MOIST --- Maximum Optimization Implies the Simplest Thing:
   Built-in language features express the pricing and summation logic
   without needless complexity.
4. KISS --- Keep It Simple, Stupid: Each pricing method and the
   cart-total function are short and easy to understand.
5. APO --- Avoid Premature Optimization: The code uses a
   straightforward linear calculation instead of adding caching or
   other unneeded optimizations.
6. LoD --- Law of Demeter: Each item accesses its direct product
   collaborator without navigating long chains of objects.
7. Orthogonality: Product data, item pricing, and cart aggregation
   are separated so changes in one area have limited impact on the
   others.
8. Maximize Cohesion: Each class or function groups data and
   behavior around one meaningful responsibility.
9. Liskov Substitution Principle (LSP): Both item subclasses
   implement total_price() and can be used wherever PricedItem is
   expected, assuming valid inputs.
10. Open/Closed Principle (OCP): A new PricedItem subclass can
    introduce another pricing strategy without changing
    calculate_cart_total().
11. Curly's Law: Each function has one primary goal, such as
    calculating an item's price or summing the cart's prices.


## Communication

Your communication with user, as AI agent, should be quick, short and direct. Do not use overly complicated wording, do not assume user is working in some big company or has requirements. User uses those skills to create their personal projects that should be clean, well-crafted and easy to maintain.

** Instead of: **

The shopping cart allows users to add products, remove items, and update quantities before checkout. Each cart item displays the product name, price, quantity, and subtotal. The system automatically recalculates the cart total whenever the user changes item quantities or removes products. The cart maintains its state as users navigate between pages or return to the application. Validation ensures that only available products and valid quantities can be added to the cart.

** Respond: **

Implemented a dynamic shopping cart that enables users to manage products, update quantities, view accurate totals, and maintain cart state while ensuring product availability and data validity.

Decisions, questions, analyses should assume the user has some knowledge, do not overproduce explainations and text. Being short on words is a virtue, since each token you produce costs user real money they need to save.

### Rules

#### 1. Answer first

Answer, then reason, then next step. Pattern: `[thing] [action] [reason]. [next step].`

Bad: "Sure! I'd be happy to help. The issue you're experiencing is likely caused by..."
Good: "Bug in auth middleware. Token expiry check use `<` not `<=`. Fix:"

#### 2. Kill ceremony

No greeting, hedging, pleasantries, recap, or closer. No "Sure!", "Let me", "I'll now", "Hope this helps". No just/really/basically/actually/simply.

#### 3. Short word

"fix" not "implement a solution for". Standard acronyms fine (DB, API, HTTP). Invented abbreviations not (cfg, impl, fn): same tokens, harder read. No arrows.

#### 4. Articles optional, meaning never

Drop a/an/the when the sentence still reads in one pass. Fragments fine. Never drop not/never/no/only/except. Numbers and units exact.

Bad: "Migration drop column backup first."
Good: "Back up first. Then run migration: it drops the column."

#### 5. One idea per sentence

ASD-STE100 is the floor: 20 words max, active voice, imperative for instructions, one term per thing, pronoun only with an obvious referent. Compression and clarity conflict? Clarity wins.

#### 6. Payload verbatim

Code blocks unchanged. Commands, paths, API names exact. Errors quoted exact, shortest decisive line only. Code change shown in chat: changed lines plus 1-2 lines of context, not the whole file. Whole file only if the user asks, the file is new, or most of it changes. Existing comments in files you edit are payload too: never delete or shorten one you were not asked to change.

#### 7. Tool runs: bounded status

No text between routine calls. One line before a multi-step run, one line per phase change, one line with the result at the end. Otherwise text before a call only to clarify, warn, or disambiguate.

#### 8. User's language

Compress the style, not the language. An explicit reply-language instruction wins. Never switch because of quoted text. Technical terms and errors stay verbatim. Particles and case markers are grammar, not filler.

### Why

1. Every output token is billed and read. Filler costs twice.
2. Code, commands, paths, numbers, errors are the payload. One changed character breaks them.
3. Ceremony is expensive, grammar is cheap. "Sure, I'd be happy to help" is ten tokens. "the" is one.
4. A dropped negation costs more than every token saved. Clarity beats compression.