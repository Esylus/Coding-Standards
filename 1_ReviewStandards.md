# itgroove Code Review Standards

Objective: The purpose of this style guide is to create standards to adhere to while conducting code base reviews. 

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  *generated with [DocToc](https://github.com/thlorenz/doctoc)*

- [0. Terms](#0-terms)
- [1. General code review concepts](#1-general-code-review-concepts)
- [2. Code review procedure](#2-code-review-procedure)
- [3 Reviewer Responsibilities](#3-reviewer-responsibilities)
- [4 Author Responsibilities](#4-author-responsibilities)
- [5 Conflict resolution](#5-conflict-resolution)
- [Use the style guide!](#use-the-style-guide)
- [5 Key points for Reviewer to consider](#5-key-points-for-reviewer-to-consider)
- [5 Key points for Author to consider](#5-key-points-for-author-to-consider)
- [Author checklist](#author-checklist)
- [Reviewer Checklist](#reviewer-checklist)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->


<!-- Table of contents -->

## 0. Review Terms  
* Author - Developer who writes the changelist.
* Reviewer - Developer who reviews the authors changelist.
* Changelist - A set of recommended changes to source code that the author wants to merge into a repository.
* LGTM - Shorthand for "Looks good to me".

## 1. Overview of the Code Review 

*Code Reviews are both a technical and social process. The seasoned reviewer will not only seek out bugs / issues but will also recognize opporutunities to praise the work and offer conscientious feedback to help teamates improve*

* Code reviews are an opportunity to share knowledge and make informed engineering decisions.
* The wise code reviewer will pick their battles and not try to attack all aspects of an authors code in a single review. 
* Each review, the reviewer should strive to raise the level of the authors code a single grade level. ex. from a D grade to a C grade. 
* Raising the level from a D to an A+ will happen incrementally over several reviews and relies on rapport and trust between co-workers.  
* The reviewer should prioritize creating a positive, beneficial code review experience for the author.
* The author should approach the review as an opportunity to learn something and always keep an open mind. 
* A good code reviewer not only finds bugs but provides conscientious feedback to help fellow teammates improve. 
* Code reviews shares knowledge across the team and allows other developers to become familiar with your work. 

## 2. Code Review Procedure

1. An author believes a specific changelist is finished, has gone through the author checklist and they are ready to move it forwards to the repository. 
2. The author initiates a code review request and selects / is assigned a reviewer (or two reviewers? - managements call). 
3. Reviewer reviews the submitted changelist according to the established Reviewer Checklist.
4. If reviewer finds issue that needs addressing, he writes a note about it, then rereads the note to ensure it is worded in a clear, non-accusatory way.  
4. Author reads the note, modifies the change list and resubmits to the reviewer who ensures changes were implemented correctly.
5. Reviewer verifies that the author has addressed the note properly and when satisfied, signs off on the changelist (LGTM) and code is pulled into codebase.  

## 3. itGroove Style Guide / Coding Standards

* It is non-productive to argue about different style preferences as there is no ultimate correct way to write code. 
* An itGroove style guide has been created to maximize code readability and maintainability.
* If there is a style conflict, refer to the itGroove style guide. If the guide doesn't cover the issue, it's not worth arguing over. 
* In order to modify the style guide, a submission has to be sent to the GitHub which will be reviewed by management. 

## 4. Reviewers Responsibilities

1. Focus on high-level / conceptual improvements in the code - leave minor syntax errors for a linter. 
2. Don't argue about personal style preferences, use the established company style guide.
3. Start reviewing the submission immediately - treat code reviews as high priority.
4. If you need to note something that is out of scope of the current review, do so but don't let it obstruct the review that is in scope. 
4. Maximum turnaround time on a review should be one business day. If you can't do this, decline the review. 
5. Do not drown the author in a sea of notes! Keep all points short and sweet. 
6. Verify that the defects are actually fixed. 

## 5. Authors Responsibilities

1. Ensure the code has conformed to itGroove standards - style guide, linter, unit tests and/or other tests.
2. Make each commit contain an isolated chunk of work. This makes it clearer for the reviewer what your intention was per commit.   
3. Break large code into smaller, sensible chunks for review so as not to overwhelm the reviewer.  
4. The reviewer can return the first small chunk allowing you to make modifications while they review the second chunk. 
5. Remember that reviewers are reviewing your code, not you as a person. Try not to take offence to the review. 
6. Follow up on feedback. Make sure you revise what was discussed in your code review.
7. If you don't agree with a given comment, don't be afraid to challenge it. Productive discussions are beneficial for all parties.  

## 6. Conflict resolution & stalemates

* Beware of unconstructive stalemates. If the tone of the conversation is getting tense or hostile, take action! 
* Are requested changes and notes per review round not trending downwards? 
* Is there lots of pushback or an unusually high number of notes? 
* Make sure to communicate. Meet in person or a video chat.. Keep the lines of communication open!
* Is there a larger problem around application design? Should you open it up to the team for discussion? 
* Eventually you must concede or escalate as the longer the conflict goes on the more damaging it is to the relationship.
* Concede - Is this point really so bad you need to fight about it? 
* Escalate - Do you need to look to a higher power in the company to solve the stalemate? 
* After a stalemate - take some space and have a break. Discuss with a manager. Study conflict resolution. Do better next time. 

## 7. Author checklist

* Have I ensured the code conforms to the itGroove style guide? 
* Does my code compile without errors and run without exceptions in happy path conditions?
* Have I checked this code to see if it triggers compiler or static analysis warnings?
* Have I covered this code with appropriate tests, and are those tests currently green?
* Have I run our performance/load/smoke tests to make sure nothing I've introduced is a performance killer?
* Have I run our suite of security tests/checks to make sure I'm not opening vulnerabilities?

## 8. Reviewer Checklist

* Does this changelist solve the problem it was supposed to solve? 
* Does this change-set make sense in the current architecture?
* Can any of the code be written more efficiently?
* Is the code easy to understand?
* Does this code read like prose?
* Does the understanding of the desired behavior match the requirements/stories for this work?
* Do the methods do what the name of the method claims that they'll do? Same for classes?
* Can I get an understanding of the desired behavior just by doing quick scans through unit and acceptance tests?
* Is this code introducing any new dependencies between classes/components/modules and, if so, is it necessary to do that?
* Is this code idiomatic, taking full advantage of the language, frameworks, and tools that we use?
* Is anything here a re-implementation of existing functionality the developer may not be aware of?

## 9. Helpful tools in code review

1. Unit Tests / Integration tests - to ensure code behaves as expected and hasn't broken anything.
2. Continuous Integration - to ensure the code builds.
3. Code Formatter - To verify whitespace matches the teams chosen styles.
4. Code Linters - To idenitfy unused imports or vars.  