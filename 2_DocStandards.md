# itgroove Documentation Standards

Objective: The purpose of this style guide is to create standards to adhere to while creating support documentation for itgroove apps. 

<!-- Table of contents -->

## 1. General 

* itGroove has selected Documentation.js (https://documentation.js.org/) as its code documentation generator. 
* It's used to generate documentation from comments within your code. Documentation.js processes JavaScript comments
in the JSDoc format. JSDoc is not code however. It's a simple and standard syntax for writing documentation.

We want code documentation to have some rules without being too suffocating. This means:
- Files should have a comment block at the top with a quick description and anything a reader might need to know. This is not necessary for files like schemas and tests.
- Functions that aren't self-explained will need a comment block on them.
- Please verify that GraphQL requests are self-documented on GraphQL Playground, and that the REST endpoints have swagger documentation attached to them.

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

## Commitizen + Semantic Versioning 

On the [LodgeLink-Components](/Repositories/LodgeLink-Components) project, we utilize [Semantic Versioning](http://www.semver.org) to version and publish releases of the component library. We've integrated [Semantic Release](https://github.com/semantic-release) to take the manual work out of creating releases. **Semantic Release** is meant to be executed on the CI environment after every successful build on the release branch. This way no human is directly involved in the release process and the releases are guaranteed to be unromantic and unsentimental.

## How does it work?

### Semantic Versioning Summary
Given a version number MAJOR.MINOR.PATCH, increment the:

* MAJOR version when you make incompatible API changes **BREAKING CHANGES**,
* MINOR version when you add functionality in a **backwards-compatible** manner, and
* PATCH version when you make **backwards-compatible** bug fixes.

Check the [Relevant, Real-world Example](#semver-example) to get a better, applicable look at this concept.

**semantic-release** uses the commit messages to determine the type of changes in the codebase. Following formalized conventions for commit messages, **semantic-release** automatically determines the next [semantic version](https://semver.org) number, generates a changelog and publishes the release.

By default **semantic-release** uses [Angular Commit Message Conventions](https://github.com/angular/angular.js/blob/master/DEVELOPERS.md#-git-commit-guidelines). This is the one that is used on the component library but can be changed to match your needs.

We use [commitizen](https://github.com/commitizen/cz-cli) to ensure proper formatting of the commit messages. Commitzen is entirely opt-in based and not required but does make it easier to learn the formatting of the messages and ensure compliance. Commitzen's convention adapter can be modified to match the conventions used on semantic-release if you don't opt into use Angular's Commit Message Conventions.

### What if I don't want to use Commitizen?
As the developer, you're free to use a regular commit flow but commit messages **not** adhering to the conventions will be ignored by semantic-release. The work still gets merged and ultimately published, but, if you commit a breaking change and fail to specify it as such, semantic-release will not pick it up and a breaking change may sneak into a minor/path release (which may upset some fellow developers).

Please check out the [Commit Guide from our component library for a guide to formatting commits and using Commitizen.](/Repositories/LodgeLink-Components/Commiting-Guide)
Here is an example of the release type that will be done based on a commit messages:

| Commit message                                                                                                                                                                                   | Release type               |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|
| `fix(component): fix rendering of text on Button component`                                                                                                                             | Patch Release              |
| `feat(component): add 'Adaptive' component`                                                                                                                                                       | ~~Minor~~ Feature Release  |
| `perf(css): remove cssKit`<br><br>`BREAKING CHANGE: cssKit removed for redundancy. Please use graceful migration path. Closes #32` | ~~Major~~ Breaking Release |


# Setting up Semantic-Release
While semantic-release claims to be CI agnostic, the default implementation is *very* geared toward GitHub. With a few overwrites, you can get it running on VSTS (though it doesn't believe that VSTS is a real CI and thus you have to override CI mode–more on that soon).

## Semantic-Release Setup
`npm i -D semantic-release` will install the latest version as a devDependency. **Do not try to use the semantic-release-cli setup as it does not work with non-GitHub projects.**

Before we add semantic-release as a build step in the VSTS pipeline, you'll want to make a few modifications to your `package.json`:

1. Add the following script: `"semantic-release": "semantic-release --ci false"`
2. Ensure your repository entry points to the `https://` repo and not `ssh`: `"url": "https://lodgelink.visualstudio.com/LodgeLink/_git/LodgeLink-Components"`
3. If you're using Commitizen, follow the install instructions from [the Commitizen repo.](https://github.com/commitizen/cz-cli)

Once you're setup on that end, you're close getting ready to add it to your build pipeline. We'll need a few things.

1. If you're using an NPM token on the registry URL inside `.npmrc`, **you need to ensure that this one has read/write access.** Semantic-release will favor this token over any other one (env variable or not) so it needs to be read/write.
2. If you're NOT using a token in your `.npmrc`, you need to add a read/write NPM token to your variables in your build pipeline. The variable should have the key `NPM_TOKEN` and the value should be the token string. 
3. You need to setup Git Credentials for VSTS. VSTS doesn't seem to play nice with SSH auth between the build pipeline and the repo itself. Semantic-release needs Git creds so it can write tags to your repo. **Note:** These credentials are an alias for your _own_ credentials and therefore you can set any username and password you like. **The username/password cannot contain any special characters as this will throw off the HTTP basic authentication.** You can setup Git Credentials in VSTS in two ways:
  1. Through your account settings by clicking on your name icon in the top-right of the screen and then clicking on Security, and then Alternate Credentials.
  2. Navigate to the relevant repo, ie, https://lodgelink.visualstudio.com/LodgeLink/_git/LodgeLink-Components, click on CLONE in the top-right, ensure that HTTPS is selected. You'll see an area for Setting Git Credentials there. 
4. Once you have your Git Credentials, you need to add them as a build variable like you did with your NPM token. The key should be `GIT_CREDENTIALS` and the value should be your `<username>:<password>` separated with a colon. Ensure that your username and password do NOT contain any special characters as it will not be able to properly authorize if it does.
5. After this is all setup, add a `npm` step to your build pipeline with the following custom command: `run semantic-release`
6. After this is setup, you're ready to trigger a build.

Before triggering a build, it's a good idea to run a dry-run. You can do this by first adding your GIT_CREDENTIALS into your own environment `export GIT_CREDENTIALS=<username>:<password>`. If you're not using `.npmrc` to hold your token, you'll need to add it to your local environment as well. You can then run `npx semantic-release --dry-run`. 

> **Don't run `npm run semantic-release` here as npm-run-scripts notoriously ignores flags so it WON'T be a dry run.**

Once you've verified your dry run, feel free to run it through your build pipeline and trigger an actual publish. If you're having difficulty with this, [Lee Mulvey](mailto:leem@criticalmass.com) @ CM set this all up and may be able to give you a hand!

<br /><br/>

 

## 4.0 Basic Requirements of Application Documentation 

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


