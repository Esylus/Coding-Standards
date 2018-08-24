
# itgroove Change Control and Deployment Standards

Objective: This document has been written to create standards to adhere to while changeing code bases and deploying projects. 

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents** 

- [1. General Deployment Strategy](#1-general-deployment-strategy)
- [2. VSTS Continuous Integration](#2-vsts-continuous-integration)
- [3. VSTS Continuous Delivery](#3-vsts-continuous-delivery)
- [4. VSTS Branching](#4-vsts-branching)
- [5. Database Changes](#5-database-changes)
- [6. Semantic Versioning + Commitizen](#6-semantic-versioning--commitizen)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 1. General Deployment Strategy

* Test
* Test
* Test

* itgroove is committed to utilizing the latest technology embodied in Visual Studio Team Services in all aspects of product planning, production, testing and deployment.
* Using VSTS, itgroove can practice Continuous Integration and Continuous Delivery which not only automates the build, testing and deployment of the app, it gives complete traceability to see everything in the bulid including changes to the the code, reviews and test results.  
* A specific branching strategy has been implemented across all projects to enforce uniform project management that has high readability.
* Node Package Management versioning has been automated using Semantic Versioning and Commitizen.
* Database changes follow a strict procedure and utilize the migration capablities of TypeORM. 

## 2. VSTS Continuous Integration

* Continuous Integration (CI) is a software best practice where code is automatically built and tested everytime a team member commits changes to version control.
* itgroove has fully embraced the ideas of continuous integration within the software development lifecycle by utilizing it to it's fullest extent in Visual Studio Team Services. All code must undergo successful Continuous Integration before being pulled into a code base.

* Different types of coding repositories will require different actions within the CI build process. Examples include..

```
- Install the lastest version of Node.js
- Run NPM install
- Run NPM build
- Run NPM tests
- Publish test data
- Run NPM start
- Publish to Node Package Manager
- Publish Documentation.js
```

* On completion of a succesful integration, the code is added to the code base or is possibly moved on into Continuous Deployment. Continuous Integration processes can be applied to different branches for different reasons to achieve different outcomes. 
* See VSTS Branching Strategy below for more detail as to how Continuous Integration is being applied within itgroove. 

## 3. VSTS Continuous Delivery

* Continous Delivery (CD) is the process to build, test, configure and deploy from a build to a production environment. Multiple testing or staging environments create a release pipeline to automate the creation of infrastructure and deployment of applications. Successive environments support progressively longer-running activities of integration, load and user acceptance testing. * itGroove fully utilizes the power of Continuous Delivery within the software devlivery cycle within Visual Studio Team Services. 

* Within any given project, different types of coding repositories will be deployed to different types of resources. Some examples include Continuous Delivery from Visual Studio Team Serivces to..

```
- Azure resource groups
- Azure docking registry (for Docker)
- Staging for testing by 3rd parties
- Virtual Machines
- And more..
```

* On completion of a succesful deployment, the code has been safely delivered to a testing or staging slot. From there, if approved, is moved forward to a production slot for consumption by the public. Continuous Deployment processes are very flexible and can be configured so that a single push from a developer into a pipeline will test the code and deploy to an Azure resource. 
* The pipeline can be setup to deliver any code project to any internet resource either automatically or with required approvals along the way.   

## 4. VSTS Branching

* There is a naming scheme for branching, and a defined process all the way to deployment.
* `next` serves as our stable branch, while `master` reflects what is currently on the production site.
* `test` is deployed to a test resource where it will undergo various forms of testing.  

* Development branching procedure: 

1. Branch off the `integration` branch (or an existing branch) with the following name:
-- `feature/{UserStory}`
-- `bugfix/{BugToFix}`
-- `cleanup/{CleanupItem}`
2. Do a Pull Request back to `integration` when you've finished developing your branch. A build will run with automated testing to verify that the PR is valid.
3. When it's ready to be QA'd, create a PR from `integration` to `deployment/test`. Another build will kick off when this is accepted, and it will deploy automatically to the test site.
4. When it's ready to be pushed to production, create a PR from `deployment/test` or from a tag of `deployment/test` to `deployment/staging`.
5. After some testing to ensure that everything works in staging, create a PR from `deployment/staging` to `deployment/prod`.
6. Merge changes from `deployment/prod` to `master`.
7. Merge changes `master` to `next` to have a branch that can be safely developed further then `master`.

* Before approving Pull Requests, please make sure to:

1. Run the app and do a quick test of some of the code
2. Run an `npm run test` to verify the tests.

## 5. Database Changes 

* Please make sure that the database you are changing has the current changes by running `typeorm migration: run`.

* To make changes to the data schema, simple change or add the entities required under entity. As much as it makes sense, use partial classes for fields that are common among multiple classes.

* From there, it's for now a multiple step process to migrate the changes:

```
npm run build
typeorm migration:generate -n MigrationName
npm run build
typeorm migration:run
```

* First, build so your changes are reflected in the `lib`. You then generate the migration to generate a `.ts` under `src/migration`. Please verify this migration to make sure that these are the changes you expect, and if not, change the queries as needed. 
* Next, build again to pull the new migration files as `.js`, and finally migrate those changes to the database.

## 6. Semantic Versioning + Commitizen

On itgroove software development projects, we utilize [Semantic Versioning](http://www.semver.org) to version and publish releases of the component library. We've integrated [Semantic Release](https://github.com/semantic-release) to take the manual work out of creating releases. **Semantic Release** is meant to be executed on the CI environment after every successful build on the release branch. This way no human is directly involved in the release process and the releases are guaranteed to be unromantic and unsentimental.

Given a version number MAJOR.MINOR.PATCH, increment the:

* MAJOR version when you make incompatible API changes **BREAKING CHANGES**,
* MINOR version when you add functionality in a **backwards-compatible** manner, and
* PATCH version when you make **backwards-compatible** bug fixes.

**semantic-release** uses the commit messages to determine the type of changes in the codebase. Following formalized conventions for commit messages, **semantic-release** automatically determines the next [semantic version](https://semver.org) number, generates a changelog and publishes the release.

By default **semantic-release** uses [Angular Commit Message Conventions](https://github.com/angular/angular.js/blob/master/DEVELOPERS.md#-git-commit-guidelines). This is the one that is used on the component library but can be changed to match your needs.

itgroove uses [commitizen](https://github.com/commitizen/cz-cli) to ensure proper formatting of the commit messages. Commitzen is entirely opt-in based and not required but does make it easier to learn the formatting of the messages and ensure compliance. Commitzen's convention adapter can be modified to match the conventions used on semantic-release if you don't opt into use Angular's Commit Message Conventions.

Here is an example of the release type that will be done based on a commit messages:

| Commit message                                                                                                                                                                                   | Release type               |
|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|----------------------------|
| `fix(component): fix rendering of text on Button component`                                                                                                                             | Patch Release              |
| `feat(component): add 'Adaptive' component`                                                                                                                                                       | ~~Minor~~ Feature Release  |
| `perf(css): remove cssKit`<br><br>`BREAKING CHANGE: cssKit removed for redundancy. Please use graceful migration path. Closes #32` | ~~Major~~ Breaking Release |

