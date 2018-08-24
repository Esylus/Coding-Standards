# itgroove Code Review Standards

Objective: This document has been written to create standards to adhere to while conducting code base reviews. 

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  

- [0. Code Review Terms](#0-code-review-terms)
- [1. Code Review Overview](#1-code-review-overview)
- [2. Code Review Procedure](#2-code-review-procedure)
- [3. Style Guide](#3-style-guide)
- [4. Authors Responsibilities](#4-authors-responsibilities)
- [5. Author Checklist](#5-author-checklist)
- [6. Reviewers Responsibilities](#6-reviewers-responsibilities)
- [7. Reviewer Checklist](#7-reviewer-checklist)
- [8. Conflict Resolution & Stalemates](#8-conflict-resolution--stalemates)
- [9. Helpful Tools](#9-helpful-tools)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


<!-- Table of contents -->

## 0. Code Review Terms  

* Author - Developer who writes the changelist.
* Reviewer - Developer who reviews the authors changelist.
* Changelist - A set of recommended changes to source code that the author wants to merge into a repository.

## 1. Code Review Overview

*Code reviews are a process that is both technical and social. The seasoned reviewer will not only seek out bugs / issues but will also recognize opportunities to praise the work and offer conscientious feedback to help teamates improve.*

* Code reviews are an opportunity to share knowledge and make informed engineering decisions.
* The wise code reviewer will pick their battles and not try to attack all aspects of an authors code in a single review. 
* Each review, the reviewer should strive to raise the authors code a single grade. ex. from a D grade to a C grade. 
* Raising the level from a D to an A+ happens incrementally over many reviews and relies on trust between co-workers.  
* The reviewer should prioritize creating a positive, beneficial code review experience for the author.
* The author should approach the review as an opportunity to learn something and always keep an open mind.  
* Code reviews shares knowledge across the team and allows other developers to become familiar with your work. 

## 2. Code Review Procedure

1. An author believes a specific changelist is finished, has gone through the author checklist and is ready to review. 
2. The author initiates a code review request and is assigned a reviewer. 
3. Reviewer reviews the submitted changelist according to the established Reviewer Checklist.
4. If reviewer finds an issue, he writes a note, then rereads the note to ensure it is worded in a clear, non-accusatory way.  
5. Author reads the note, modifies the change list and resubmits. The reviewer ensures changes were done correctly.
6. Reviewer verifies that the author has addressed the note properly then signs off on the changelist.  
7. Code is pulled into codebase.

## 3. Style Guide

* It is non-productive to argue about different style preferences as there is no ultimate correct way to write code. 
* An itGroove style guide has been implemented to maximize code readability and maintainability.
* If there is a style conflict, refer to the style guide. If the guide doesn't cover the issue, it's not worth arguing over. 
* In order to modify the style guide, a submission has to be sent to the GitHub which will be reviewed by management. 

## 4. Authors Responsibilities

* Ensure the code has conformed to itGroove standards, style guide, linter, unit tests and/or other tests.
* Make each commit contain an isolated chunk of work to makes it clear what your intention was per commit.  
* Break large code sections into smaller, sensible chunks for review so as not to overwhelm the reviewer.  
* The reviewer can return the first small chunk allowing you to make modifications while they review the second chunk. 
* Remember that reviewers are reviewing your code, not you as a person. Try not to take offence to the review. 
* Follow up on feedback. Make sure you revise what was discussed in your code review.
* If you don't agree with a given comment, respectfully challenge it. Productive discussions are beneficial for all.  

## 5. Author Checklist

1. Have I ensured the code conforms to the itGroove style guide? 
2. Does my code compile without errors and run without exceptions?
3. Have I checked this code to see if it triggers compiler, linter or static analysis warnings?
4. Have I covered this code with appropriate tests and are those tests currently green?
5. Have I run our performance/load/smoke tests to make sure nothing I've introduced is a performance killer?
6. Have I run our suite of security tests/checks to make sure I'm not opening vulnerabilities?

## 6. Reviewers Responsibilities

* Focus on high-level and conceptual improvements in the code leaving minor syntax errors for a linter. 
* Don't argue about personal style preferences, use the established company style guide.
* Start reviewing the submission immediately. Treat code reviews as a high priority.
* If noting something out of scope of the current review, do so but don't hinder the current scoped review. 
* Maximum turnaround time on a review should be one business day. If you can't do this, decline the review. 
* Do not drown the author in a sea of notes! Keep all points short and sweet. 
* Verify that the defects are actually fixed. 

## 7. Reviewer Checklist

1. Does this changelist solve the problem it was supposed to? 
2. Does this changelist make sense in the current architecture?
3. Can any of the code be written more efficiently?
4. Is the code easy to understand?
6. Does the understanding of the desired behavior match the requirements/stories for this work?
7. Do the names of the methods and classes clearly explain their purpose?
8. Can I get an understanding of the desired behavior just by doing quick scans through unit and acceptance tests?
9. Is this code introducing any new dependencies between components and modules and, if so, is it necessary?
10. Is this code idiomatic, taking full advantage of the language, frameworks, and tools that we use?
11. Is anything here a re-implementation of existing functionality the developer may not be aware of?

## 8. Conflict Resolution & Stalemates

* Are requested changes and notes per review round not trending downwards? 
* Is there lots of pushback or an unusually high number of notes?
* Is the tone of the conversation is getting tense or hostile?
* Beware of unconstructive stalemates - take action!  
* Always be sure to communicate. Meet in person or a video chat.. Keep the lines of communication open!
* Is there a larger problem around application design? Should you open it up to the team for discussion? 
* The longer the conflict goes on the more damaging it is to the relationship. The issue must be condeced or escalated.
* Concede - Is this point really so bad you need to fight about it? 
* Escalate - Do you need to look to a higher power in the company to solve the stalemate? 
* After a stalemate - take some space and have a break. Discuss with a manager. Study conflict resolution. Reconnect, talk through what happened, reconcile.  

## 9. Helpful Tools

1. Unit Tests / Integration tests - to ensure code behaves as expected and hasn't broken anything.
2. Continuous Integration - to ensure code builds.
3. Code Formatter - To verify whitespace matches the teams chosen styles.
4. Code Linters - To idenitfy unused imports, vars, style choices etc.  