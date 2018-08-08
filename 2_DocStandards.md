# itgroove Documentation Standards

The purpose of this style guide is to create standards to adhere to while creating support documentation for itgroove apps. 


<!-- Table of contents -->

## 1. General 

* itGroove has selected Documentation.js (https://documentation.js.org/) as its code documentation generator. 
* It's used to generate documentation from comments within your code. Documentation.js processes JavaScript comments
in the JSDoc format. JSDoc is not code however. It's a simple and standard syntax for writing documentation.

JSDoc lets you specify absolutely everything about your code: use @name to say what something is called, @kind for whether it's a function or a class, @param for its parameters, and so on. But writing all of that explicitly is tedious, so where it can, `documentation` automatically populates @name, @kind, and @memberof tags based on its reading of the code.

## 2. Basic Documentation.js syntax

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

### 2.1 Common tags

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

### 2.2 Installation

Globally install `documentation` using the [npm](https://www.npmjs.com/) package manager:

```sh
$ npm install -g documentation
```

### 2.3 Usage Examples

Below are several ways to run the documentation generator to achieve different output formats:

generate markdown docs for index.js and files it references
documentation build index.js -f md

**generate html docs for all files in src**
documentation build src/** -f html -o docs

**document index.js, ignoring any files it requires or imports**
documentation build index.js -f md --shallow

**build and serve HTML docs for app.js**
documentation serve app.js

**build, serve, and live-update HTML docs for app.js**
documentation serve --watch app.js

Commands:
  serve [input..]   generate, update, and display HTML documentation
  build [input..]   build documentation
  lint [input..]    check for common style and uniformity mistakes
  readme [input..]  inject documentation into your README.md

## 3.0 Semantic Versioning + Commitizen

* Should details about this go in here? 

## 4.0 Basic Application Documentation Requirements 

* All projects should cover the below points in their documentation. 

**Project Title**

One Paragraph of project description goes here

**Getting Started**

These instructions will get you a copy of the project up and running on your local machine for development and testing purposes. See deployment for notes on how to deploy the project on a live system.

**Prerequisites**

What things you need to install the software and how to install them

```
Give examples
```

**Installing**

A step by step series of examples that tell you how to get a development env running

Say what the step will be

```
Give the example
```

And repeat

```
until finished
```

End with an example of getting some data out of the system or using it for a little demo

**Running the tests**

Explain how to run the automated tests for this system

**Break down into end to end tests**

Explain what these tests test and why

```
Give an example
```

**And coding style tests**

Explain what these tests test and why

```
Give an example
```

**Deployment**

Add additional notes about how to deploy this on a live system

**Built With**

* [Dropwizard](http://www.dropwizard.io/1.0.2/docs/) - The web framework used
* [Maven](https://maven.apache.org/) - Dependency Management
* [ROME](https://rometools.github.io/rome/) - Used to generate RSS Feeds

**Contributing**

Please read [CONTRIBUTING.md](https://gist.github.com/PurpleBooth/b24679402957c63ec426) for details on our code of conduct, and the process for submitting pull requests to us.

**Versioning**

We use [SemVer](http://semver.org/) for versioning. For the versions available, see the [tags on this repository](https://github.com/your/project/tags). 

**Authors**

* **Billie Thompson** - *Initial work* - [PurpleBooth](https://github.com/PurpleBooth)

See also the list of [contributors](https://github.com/your/project/contributors) who participated in this project.

**License**

This project is licensed under the MIT License - see the [LICENSE.md](LICENSE.md) file for details

**Acknowledgments**

* Hat tip to anyone whose code was used
* Inspiration
* etc