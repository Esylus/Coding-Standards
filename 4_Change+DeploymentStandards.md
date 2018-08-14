# itgroove Change Control and Deployment Standards

Objective: The purpose of this style guide is to create standards to adhere to while changeing code bases and deploying. 

<!-- This guide will cover Continuous Integration, Contiuous Deployment details -->
<!-- This guide will also cover how to handle database changes for apps with relational databases -->

<!-- Table of contents -->

## 1. General Deployment Strategy

* Deployment standards 

## VSTS Continuous Integration Strategy

Continuous Integration (CI) is a software best practice where code is automatically built and tested everytime a team member commits changes to version control.

itGroove has fully embraced the ideas of continuous integration within the software development lifecycle by utilizing it to it's fullest extent in Visual Studio Team Services. 

Different types of coding repositories will have different steps implemented in the CI build process. Several steps can be common to many types of builds. Examples include..

- Install the lastest version of Node.js
- Run NPM install
- Run NPM build
- Run NPM tests
- Publish test data
- Run NPM start
- Publish to Node Package Manager
- Publish Documentation.js

On completion of a succesful integration, the code is added to the code base or is possibly picked up into the Continuous Deployment lifecycle. Continuous Integration processes can be applied to different branches for different reasons to achieve different outcomes. See VSTS Branching Strategy below for more detail as to how Continuous Integration is being applied within itGroove. 

## VSTS Continuous Delivery Strategy 

Continous Delivery (CD) is the process to build, test, configure and deploy from a build to a production environment. Multiple testing or staging environments create a release pipeline to automate the creation of infrastructure and deployment of applications. Successive environments support progressively longer-running activities of integration, load and user acceptance testing. 

itGroove fully utilizes the power of Continuous Delivery within the software devlivery cycle within Visual Studio Team Services. 

Different types of coding repositories will be deployed to different types of resources. Some examples include deployment to..

- Azure resource groups
- Azure docking registry (for Docker)
- Staging for testing by 3rd parties
- And more..

## VSTS Branching strategy
There is a naming scheme for branching, and a defined process all the way to deployment. `next` serves as our stable branch, while `master` reflects what is currently on the production site.
1. Branch off the `integration` branch (or an existing branch) with the following name:
-- `feature/{UserStory}`
-- `bugfix/{BugToFix}`
-- `cleanup/{CleanupItem}`
2. Do a Pull Request back to `integration` when you've finished developing your branch. A build will run with automated testing to verify that the PR is valid.
3. When it's ready to be QA'd, create a PR from `integration` to `deployment/test`. Another build will kick off when this is accepted, and it will deploy automatically to the test site.
4. When it's ready to be pushed to production, create a PR from `deployment/test` or from a tag of `deployment/test` to `deployment/staging`.
5. After some testing to ensure that everything works in staging, create a PR from `deployment/staging` to `deployment/prod`.
6. Merge changes (TODO: Is this another PR?) from `deployment/prod` to `master`.
7. TODO: Add bit for `next`.

Before approving Pull Requests, please make sure to:
1. Run the app and do a quick test of some of the code
2. Run an `npm run test` to verify the tests.

### 7. Database Changes 

### Making Database Changes
Please make sure that the database you are changing has the current changes by running `typeorm migration: run`.

To make changes to the data schema, simple change or add the entities required under entity. As much as it makes sense, use partial classes for fields that are common among multiple classes.

From there, it's for now a multiple step process to migrate the changes:
```
npm run build
typeorm migration:generate -n MigrationName
npm run build
typeorm migration:run
```

First, build so your changes are reflected in the `lib`. You then generate the migration to generate a `.ts` under `src/migration`. Please verify this migration to make sure that these are the changes you expect, and if not, change the queries as needed. You then build again to pull the new migration files as `.js`, and finally migrate those changes to the database.

