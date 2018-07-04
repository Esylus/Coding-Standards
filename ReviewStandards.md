# itgroove Code Review Standards

The purpose of this style guide is to create standards to adhere to while conducting code base reviews. 



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

## 0. Terms 
* Author - Developer who writes the changelist.
* Reviewer - Developer who reviews the authors changelist.
* Changelist - A set of recommended changes to source code that the author wants to merge into a repository.
* LGTM - Shorthand for "Looks good to me".

## 1. General code review concepts

*Code Reviews are both a technical and social process. The seasoned reviewer will not only seek out bugs / issues but will also recognize opporutunities to praise the work and offer conscientious feedback to help teamates improve*

* Code reviews are an opportunity to share knowledge and make informed engineering decisions.
* The wise code reviewer will pick their battles and not try to attack all aspects of code in a single review. 
* Each review, the reviewer should strive to raise the level of the authors code a single grade level. ex. from a D grade to a C grade. 
* Raising the level from a D to an A+ will happen incrementally over several reviews and relies on rapport and trust between co-workers.  
* The reviewer should prioritize creating a positive, beneficial code review experience for the author.
* The author should approach the review as an opportunity to learn something and keep an open-mind. 
* A good code reviewer not only finds bugs but provides conscientious feedback to help teammates improve. 
* Code reviews shares knowledge across the team and allows other developers to become familiar with your work. 

## 2. Code review procedure

*In principle :*

1. Author believes a specific changelist is finished and they are ready to move it forwards to the repository. 
1. Author initiates code review request and selects / is assigned a reviewer (two reviewers?). 
1. Reviewer reviews submitted changelist according to Reviewer Checklist and returns to the author for modification if required.
1. Author modifies the change list and resubmits to the reviewer who ensures changes were implemented correctly.
1. Reviewer signs off on the changelist (LGTM) and code is pulled into codebase.  

## 3 Reviewer Responsibilities

*In principle :*

1. Focus on high-level / conceptual improvements in the code - leave minor syntax errors for a linter. 
1. Refer to a style guide for all style issues - don't argue about personal preferences.
1. Start reviewing immediately - treat code reviews as high priority.
1. Maximum turnaround time on a review should be one business day. If you can't do this, decline review. 
1. Do not drown the author in a sea of notes! Keep all points short and sweet. 
1. 
1. 


## 4 Author Responsibilities

1. Break code into smaller, digestable chunks for review. 
1. The reviewer can return the first small chunk allowing you to make modifications while they review the second chunk. 
1. Do not submit in large projects and have to wait for it to be sent back.
1. Point 1

## 5 Conflict resolution 

1. Beware of unconstructive stalemates. If the tone of the conversation is getting tense or hostile, take action! 
1. Point 1
1. Point 1

## Use the style guide!
* It is a waste of time to argue about different styles as their is no right answer. 
* If there is a conflict, refer to the style guide. If the guide doesn't cover it, it's not worth arguing over. 
* In order to modify the style guide, a submission has to be sent to the GitHub which will be reviewed. 

## 5 Key points for Reviewer to consider 

1. Point 1
1. Point 1
1. Point 1

## 5 Key points for Author to consider 

1. Point 1
1. Point 1
1. Point 1

## Author checklist
*Don't waste time in the review with style issues and errors* 

* Have I ensured the code conforms to the style guide with working unit tests? 

* Does my code compile without errors and run without exceptions in happy path conditions?
* Have I checked this code to see if it triggers compiler or static analysis warnings?
* Have I covered this code with appropriate tests, and are those tests currently green?
* Have I run our performance/load/smoke tests to make sure nothing I've introduced is a performance killer?
* Have I run our suite of security tests/checks to make sure I'm not opening vulnerabilities?

## Reviewer Checklist
* Does this changelist solve the problem it was supposed to solve? 
* Does this change-set make sense in the current architecture?
* Can any of the code be written more efficiently?
* Is the code easy to understand?
* Does it increase or decrease technical debt?

* Does this code read like prose?
* Does the understanding of the desired behavior match the requirements/stories for this work?
* Do the methods do what the name of the method claims that they'll do? Same for classes?
* Can I get an understanding of the desired behavior just by doing quick scans through unit and acceptance tests?
* Is this code introducing any new dependencies between classes/components/modules and, if so, is it necessary to do that?
* Is this code idiomatic, taking full advantage of the language, frameworks, and tools that we use?
* Is anything here a re-implementation of existing functionality the developer may not be aware of?
