# itgroove Documentation Standards

Objective: This document has been written to create standards for itGroove support documentation.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  

- [1. Documentation Types Overview](#1-documentation-types-overview)
- [2. Project ReadMe Requirements](#2-project-readme-requirements)
- [3. Documentation.js](#3-documentationjs)
  - [3.1 Common tags](#31-common-tags)
  - [3.2 Usage Examples](#32-usage-examples)
- [4.0 Swagger Documents](#40-swagger-documents)
- [5.0 GraphQL Documents](#50-graphql-documents)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 1. Documentation Types Overview  

**Project ReadMe:** 
* All projects require a readMe file to explain the basics of getting up and running with the app. 
* An itGroove readMe template is supplied in this document as a starting point for any project.  

**Code Documentation:** 
* itGroove has selected Documentation.js (https://documentation.js.org/) as its primary code documentation generator. 
* It's used to generate documentation from comments within your code. 
* Documentation.js processes JavaScript comments in the JSDoc format, a simple and standard syntax for writing documentation.

**Rest Endpoint Documentation:** 
* itGroove has selected Swagger Documentation (https://swagger.io/solutions/api-documentation/) as its REST endpoint documentation generator.
* The usage of Swagger within itGroove projects is currently being investigated and will be detailed in this document at a later date.   

**GraphQL Documentation:**
* itGroove has selected GraphQL (https://graphql.org/) as query language for it's API's.
* GraphQL is self-documenting in that you describe the data types, fields and interaction points between them. 
* Playground then lets you interactively explore the schema of a GraphQL server and run queries against it at the same time.
* Dynamically generated documentation can be generated from the GraphQL schema's to be used in a webpage. 

**File Comment Documentation:** 
* Files should have a comment block at the top with a quick description and anything a reader might need to know. 
* This is not necessary for files such as schemas and tests.
* Functions that aren't self-explained will need a comment block on them beyond the Documentation.js syntax.

## 2. Project ReadMe Requirements

*All projects should cover the below points in their documentation.* 

**Project Title**  
One Paragraph of project description goes here.

**Getting Started**  
These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. 
See deployment for notes on how to deploy the project on a live system.

**Prerequisites**  
What things you need to install the software and how to install them.

```
Give examples
```

**Installing**    
A step by step series of examples that tell you how to get a development environment running
with an example of getting some data out of the system or using it for a little demo.

```
Give the example
```

And repeat

```
until finished
```

**Running the tests**  
Explain how to run the automated tests for this system.

**Break down into end to end tests**  
Explain what these tests test and why.

```
Give an example
```

**Deployment**  
Add additional notes about how to deploy this on a live system.

**Built With**  
List major components of the system and where to find more info about them.  
* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

**Contributing**  
Details about how to contribute to the project if possible.
Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

**Versioning**    
List what is used for versioning control.
We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

**Authors**     
List of the developers on the project and a public contact for them. 
*Sally Developer* - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)
*Billie Developer* - *Database Schemas* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

**License**     
State the license that the project is defined under.
This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

**Acknowledgments**    
Any special acknowledgemnets that could include:
* Hat tip to anyone whose code was used
* Inspiration
* etc

## 3. Documentation.js

* For complete instructions on installation and usage, please visit (https://documentation.js.org/). 
* Documentation.js, using the syntax of JSDoc, lets you specify absolutely everything about your code: use @name to say what something is called, @kind for whether it's a function or a class, @param for its parameters, and so on. But writing all of that explicitly is tedious, so where it can, `documentation` automatically populates @name, @kind, and @memberof tags based on its reading of the code.
* Syntax for comments in code begin with /** and end with a */. This is required syntax for documentation.js to identify the comments and gather them for the documentation output. 

```js
/**
 * This function adds one to its input.
 * @param {number} age any number
 * @returns {number} that number, plus one.
 */
function addOne(age) {
  return input + 1;
}
```

* The first line of the comment is a description of the code unit. It should say what the code is or does.
* @param is a tag. It indicates that we'll be documenting a function's parameter. 
* {number} is a type. It defines this input type as a number, string, object, date etc.. It could also be a custom class.
* Age is the name of the input variable. It should match what the codes input parameter says. 
* Any number is a description of the input.
* Returns is a return value. These won't have a name, just a description.

### 3.1 Common tags

[usejsdoc.com](http://usejsdoc.org/index.html) covers all available tags in the
JSDoc syntax, and is a great reference.

The most common tags are listed below. 

* @param - input given to a function as an argument
* @returns - output value of a function
* @name - explicitly set the documented name of a function, class, or variable
* @private - you can use @private to document
  code and not have it included in the generated documentation,
  maybe it's not part of the public API. There's also @public and @protected 
* @example - you can use the @example tag to add inline code examples with your
  documentation

### 3.2 Usage Examples

* After applying the JSDoc syntax, there are different ways to run the documentation generator to achieve different output formats.
* Below are two examples, many other types of output formats can be found on the Documentation.js webpage. 

```
**generate markdown docs for index.js and files it references**  
documentation build index.js -f md

**build and serve HTML docs for app.js**  
documentation serve app.js
```

## 4.0 Swagger Documents

* The role of documentation with a REST API is to explain the individual endpoints, what function they perform, and the parameters a developer can pass to them.  
* The usage of Swagger within itGroove projects is currently being investigated with usage details forthcoming. 

**CREATE SOME SWAGGER GUIDELINES AND PUT HERE ONCE UNDERSTOOD**

## 5.0 GraphQL Documents

* With a GraphQL API, you describe the data types, fields, and the interaction points between them, and a developer can assemble an appropriate query to get the information they need.
* Playground then lets you interactively explore the schema of a GraphQL server and run queries against it at the same time.
* This autogenerates explanatory text based on the three main entry types into a GraphQL schema: Query, Mutation, and Subscription.
* GraphQL offers a lot of positives on the documentation front for simple APIs. For example, keeping documentation in sync with API changes is easy, as once a field, type, or query changes in code, so do the docs.

**CREATE SOME GRAPHQL GUIDELINES AND PUT HERE ONCE UNDERSTOOD**




