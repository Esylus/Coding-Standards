# itgroove Coding Style Guide

The purpose of this style guide is to create a collaboration baseline. 

This guide will follow the below format to address both generalities and details:

*In principle :* General guiding principles around the topic. 

*In practice :* Specific implementation details required by itgroove of it's developers.

<!-- Table of contents -->

## 1. General 

*Why have coding standards?* 

* To maximize code readability and maintainability by making a development teams code base look like a single person has written it.
* To speed up writing code. Simple rules to follow means you won't have to make continuous judgements about how code looks / presents.
* To read each others code faster and discern patterns visually without having to read each token.
* To encapsulate the shared experience of many developers so we can learn from each others mistakes. 
* To free us to think in higher abstractions and come up with new patterns instead of enforcing what we have always seen or done. 

Note - Being that there is no right or wrong coding standard, a team has to "just pick something" for each category and stick with it. Thus this guide is a collection of "just pick something"'s developed by the itgroove team in July, 2018.  

## 2. Comments

*In principle :*

1. Point 1
1. Point 1
1. Point 1

## 3. Naming Schemes

### 3.1 Variables
### 3.2 Functions
### 3.3 Classes

## 4. Readability

### 4.1 Spacing
### 4.2 Braces
### 4.3 Lines

## 5. Cluster Sizes

## 6. Classes

## 7. Errors

## 8. Portability

## 9. Testing

## 10. Repository

## 10. Best Practices

### 10.1 DRY Principle: Don't repeat yourself
* This principle summarizes the essense of what it means to write good code, in all languages, at all levels.
* Every piece of knowledge should have a single, unambiguous, authoritative representation within a system 
* If you see the same code twice, wrap it in a function and maximize reusability. 
* DRY matters much less in testing code then it does in production code. 

### 10.2 YAGNI - You ain't gonna need it
* Don’t write code that you think you might need in the future but don't need yet - this is coding for imaginary future use cases. 
* YAGNI code can easily become dead code or will need rewriting because the future case will always turn out different then you imagined it

### 10.3 KISS - Keep it simple silly
* Less is more! The simplest solution is more then sufficient.
* Write as little code as possible, less to read, less to understand, less bugs to show up and have to fix.
* Either code belongs in the app or doesn't - Don't leave commented out code, it will confuse people. Place it in the Git log.
* Refactor whenever you see the need and have the chance. 

### 10.4 Fail fast, fail often
*
*
*

### 10.5 Do not hinder your fellow developer
*
*
*

### 10.6 POLA - Principle of least astonishment
* Choose a solution that everyone can understand
* A component of a system should behave in a way a user expects it to behave, users should not be astonished by it's behavior. 
*

### 10.7 Should I use cool new feature "X"?
* Will everyone on my team understand the code? 
* Does it replace another less readable feature?
* Does it reduce redundancy/repetition?
* Does it add information for the reader?
* Does it reduce the likelihood of errors?



