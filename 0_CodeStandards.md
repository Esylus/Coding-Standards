# itgroove Coding Style Guide

Objective: This document has been written to create coding style standards to adhere to while developing itgroove projects.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents** 

- [1. itgroove Style Guide Overview](#1-itgroove-style-guide-overview)
- [2. Comments](#2-comments)
- [3. General Naming Choices](#3-general-naming-choices)
  - [3.1 Variable Names](#31-variable-names)
  - [3.2 Function and Method Names](#32-function-and-method-names)
  - [3.3 Class Names](#33-class-names)
- [4. General Style Choices](#4-general-style-choices)
  - [4.1 Spacing](#41-spacing)
  - [4.2 Braces](#42-braces)
  - [4.3 Lines](#43-lines)
  - [4.4 Code Cluster Sizes](#44-code-cluster-sizes)
  - [4.5 Types](#45-types)
  - [4.6 Class Order](#46-class-order)
  - [4.7 Null and Undefined](#47-null-and-undefined)
  - [4.8 Errors](#48-errors)
- [5. Maintainability](#5-maintainability)
- [6. Portability](#6-portability)
- [7. Best Practices To Strive For](#7-best-practices-to-strive-for)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 1. itgroove Style Guide Overview 

**Why have a style guide / coding standards at all?** 

* To maximize code readability and maintainability by making a teams code base look like a single person has written it.
* To speed up writing code. Simple rules to follow means developers won't have to make continuous judgements about how code looks and presents.
* To discern patterns visually without having to read each individual token.
* To encapsulate the shared experience of many developers so we learn from each others wisdoms and mistakes. 
* To free us to think in higher abstractions and come up with new patterns instead of enforcing what we have always seen or done. 

Note - Being that there is no right or wrong coding standard, a team has to "just pick something" for each category and stick with it. Thus this guide is a collection of "just pick somethings" developed by the itgroove team in August, 2018.  

## 2. Comments

**We want code documentation to have some rules without being too suffocating. This means:**
* Files should have a comment block at the top with a quick description and anything a reader might need to know. This is not necessary for files like schemas and tests.
* All functions should be documented using JSDoc syntax for automatic documentation generation using [Documentation.js](https://documentation.js.org/). See the itgroove Documentation Standards for details.
* Functions that aren't self-evident will need a comment block describing the INTENT of the code. However, avoid obvious and unnecessary comments. Never state the obvious!
* Please verify that [GraphQL](https://graphql.org/) requests are self-documented on [GraphQL Playground](https://github.com/prisma/graphql-playground), and that the REST endpoints have [Swagger](https://swagger.io/solutions/api-documentation/) documentation attached to them.
* Multi-line comments should use // rather then /* */ to make commenting out large sections of code easier when debugging.
* Since future developers can't be relied on to always accurately update comments, over time, code comments become inaccurate and misleading. Thus before commenting, strive to make code readable and self-documenting through effective naming practices and known programming styles.

## 3. General Naming Choices

* Use PascalCase for type and enum names.
* Use camelCase for variable, function, method and property names. 
* Do not use "_" as a prefix private properties. 
* Do not use "I" as a prefix for interface names.
* Names should tell you why it's there, what it does, how to use it.
* Use whole, pronounceable English words and never use ambiguous abbreviations. 
* Ensure names are always sufficiently different so you don't mistake a name for another similar one. 
* Disallowed words: anything to general or to vague ex. Manager, Processor, Data, Info.
* A name should be an obvious, logical name to search. ex. A button to restore all is named 'restoreAllButton'.

### 3.1 Variable Names

* When you can, use customary opposite pairs in variable names such as min/max, begin/end, open/close.
* Boolean vars should contain 'is / has / can / use' which implies yes/no or true/false ex. fileIsFound, isValidEmail.
* Use single letter var names for short loop indexes or array index ex. For(x = 0; x > 10, x++) or a[i].
* Even for a trivial, limited scope variable, always use meaningful names.
* Groups of enumerated types should share same prefix Ex. FONT_ARIAL and FONT_ROMAN

### 3.2 Function and Method Names

* Use verb-noun method - name routines that perform an operation-on-a-given-object ex. calulateTotalAmount()
* Mention if there is heavy processing or side effects ex.. shutdown(), removeListener(), getWidth(), generateHistogram()
* Append computational qualifiers (Avg, Sm, Min, Max etc..) to end of name where appropriate.


## 4. General Style Choices

* The indenting style of code conveys logical structure and flow.
* Consider arrays as immutable by default after creation.
* Do not use for..in statements; instead, use ts.forEach, ts.forEachKey and ts.forEachValue. Be aware of their slightly different semantics.
* Try to use ts.forEach, ts.map, and ts.filter instead of loops when it is not strongly inconvenient.
* Use arrow functions over anonymous function expressions.
* Only surround arrow function parameters when necessary. 
* For example, (x) => x + x is wrong but the following are correct:
    x => x + x
    (x,y) => x + y
    <T>(x: T, y: T) => x === y

### 4.1 Spacing

* Do not mix spaces with the tab key - the number of spaces represented by a tab is different in different IDE's.
* Use 2 spaces per indentation.
* Use space after every comma in a list.
* Use space before and after every "=" of assignment, after every binary operators (+, -, /, *).
* Parenthesized constructs should have no surrounding whitespace. 
* A single space follows commas, colons, and semicolons in those constructs. For example:
    for (var i = 0, n = str.length; i < 10; i++) { }
    if (x < 10) { }
    function f(x: number, y: string): void { }

### 4.2 Braces

* Always surround loop and conditional bodies with curly braces.
* Open curly braces always go on the same line as whatever necessitates them.
* else goes on a separate line from the closing curly brace.

### 4.3 Lines

* Try to keep lines short and clear as general rule - don't want to use horizontal scroll bar.
* Write one statement per line, not multiple statements per line .
* However if  breaking up a longer line creates confusing looking code, a longer line is more readable and acceptable. 
* In long lines of similar code with minor variations, stacking vertically will emphasize patterns and make vertical similarities jump out. 
* Use a single declaration per variable statement 
    (i.e. use var x = 1; var y = 2; over var x = 1, y = 2;).

### 4.4 Code Cluster Sizes

* Functions should be under 10 lines of code.
* Classes shouldn't be bigger then 5 member variables and a few hundred lines of code.
* Files shouldn't be longer then 500 lines of code so you can navigate effectively.

### 4.5 Types

* Do not export types/functions unless you need to share it across multiple components.
* Do not introduce new types/values to the global namespace.
* Shared types should be defined in 'types.ts'.
* Within a file, type definitions should come first.

### 4.6 Class Order

* Classes are a story that you read from top to bottom. The most relevant, important parts go at the top.
* Public members first, protected second, private last - public members are most relevent to extension. 
* Try to minimize scrolling either vertically or horizontally.
* For consistency, do not use classes in the core compiler pipeline. Use function closures instead.

### 4.7 Null and Undefined

* Use "undefined". DO NOT use "null".

### 4.8 Errors

* Always recover or fail gracefully - Report an error message and optimally attempt to continue.
* Provide useful error messages while also logging a programmer friendly message with enough user info so a support team can investigate the error.
* Use a period at the end of a sentence.
* Use indefinite articles for indefinite entities.
* Definite entities should be named (this is for a variable name, type name, etc..).
* When stating a rule, the subject should be in the singular (e.g. "An external module cannot..." instead of "External modules cannot...").
* Use present tense.

## 5. Maintainability

* Software is a living work, the initial development is just the beginning - expect it to change and evolve.
* Keep scope of variables as small as possible to avoid confusion and ensure maintainability.
* Use vars and routines for one purpose only, avoid multipurpose routines that perform a variety of unrelated tasks.
* Avoid deep nesting, it makes code harder to read and follow.
* Try to keep a return point from a function as the last statement in the function.
* Don't put numbers directly in code, put in variables or constants that can be changed later.

## 6. Portability

* Program code should not contain "hard-coded" or literal values referring to environmental parameters such as file paths, user names, host names etc..
* Parametrize such variables and configure them for the hosting environment outside of the application such as on the application server or in database. 
* Code should run on different environments and not fail on systems with a different design then anticipated.

## 7. Best Practices To Strive For

**Work out loud**
* Information should be shared in a timely manner with other team members, regardless of whether that information is deemed relevent. 

**DRY - Don't repeat yourself**
* This principle summarizes the essense of what it means to write good code, in all languages, at all levels.
* Every piece of knowledge should have a single, unambiguous, authoritative representation within a system 
* If you see the same code twice, wrap it in a function and maximize reusability. 
* DRY matters much less in testing code then it does in production code. 

**YAGNI - You ain't gonna need it**
* Don’t write code that you think you might need in the future but don't need yet - this is coding for imaginary future use cases. 
* YAGNI code can easily become dead code or will need rewriting because the future case will always turn out different then you imagined it

**KISS - Keep it simple silly**
* Less is more! The simplest solution is more then sufficient.
* Write as little code as possible, less to read, less to understand, less bugs to show up and have to fix.
* Either code belongs in the app or doesn't - Don't leave commented out code, it will confuse people. 
* Refactor whenever you see the need and have the chance. 

**Fail fast, fail often**
* Write defensively - always think about what can go wrong, what will happen on invalid input, what might fail, what will help you catch many bugs before they happen
* Check input on nonsensical input or invalid states as early as possible.
* Use error response's or message's that will make the exact problem clear to your caller.

**POLA - Principle of least astonishment**
* A component of a system should behave in a way a user expects it to, users should not be astonished by it's behavior.
* Choose a solution that everyone can understand.
 
**Should I use cool new feature "X"?**
* Will everyone on my team understand the code? 
* Does it replace another less readable feature?
* Does it reduce redundancy/repetition?
* Does it add information for the reader?
* Does it reduce the likelihood of errors?