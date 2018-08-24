# itgroove Testing Standards

Objective: This document has been written to create itgroove standards surrounding testing of code.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  

- [1. General Testing Principles](#1-general-testing-principles)
- [2. The Various Testing Layers Analogy](#2-the-various-testing-layers-analogy)
- [3. Unit Testing](#3-unit-testing)
  - [3.1 Unit Testing Guidelines](#31-unit-testing-guidelines)
- [4. Integration Testing](#4-integration-testing)
  - [4.1 Integration Testing Guidelines](#41-integration-testing-guidelines)
- [5. System Testing](#5-system-testing)
  - [5.1 System Test Guidelines](#51-system-test-guidelines)
- [6. End-To-End Testing](#6-end-to-end-testing)
  - [6.1 End-To-End Testing Guidelines](#61-end-to-end-testing-guidelines)
- [7. User Acceptance Testing](#7-user-acceptance-testing)
  - [8.1 User Acceptance Testing Guidlines](#81-user-acceptance-testing-guidlines)
  - [8.2 User Acceptance Testing Deliverables](#82-user-acceptance-testing-deliverables)
- [9. Regression Testing](#9-regression-testing)
  - [9.1 Regression Testing Guidelines](#91-regression-testing-guidelines)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 1. General Testing Principles 

* itgroove adheres to the principles outlined in "Foundations of Software Testing" by Rex Black, Erick Van Veenendaal, Dorothy Graham. Below is a summary by Vineeta Gakhare at https://www.utest.com/articles/seven-testing-principles.  

1. Testing finds defects. While testing can show that defects are present, it cannot prove that there are no defects at all. One can never assume that there are no defects or the application is 100 percent bug free even if thorough testing is done.

2. Exhaustive testing is impossible. Testing everything (all combinations of inputs and preconditions) is not feasible except for trivial cases. Instead of exhaustive testing, risk analysis and priorities should be used to focus testing efforts.

3. Test early. To find defects early, testing activities shall be started as early as possible in the software life cycle and shall be focused on defined objectives. The cost of testing will be much less if the defects are found as early as possible rather than later in the development life cycle.

4. Defect clustering. Testing efforts shall be focused proportionally to the expected and later observed defect density of modules. A small number of modules usually contains most of the defects discovered during pre-release testing. Use the Pareto principle of 80:20, that is 80%  of defects are due to 20% of code. If we find one defect in a particular module/area there is pretty high chance of finding more there.

5. Pesticide Paradox. If the same kinds of tests are repeated over and over again, eventually these tests will no longer be able to find any new bugs. To overcome this “Pesticide Paradox”, test cases need to be regularly reviewed, revised and enhanced to exercise different parts of the software to find potentially more defects.

6. Testing is context dependent. Testing is conducted differently for different application types. For example, safety critical software is tested differently from an e-commerce site. Testing efforts should be based on what is to be tested while testing focus will depend on what is most important for that type of application.

7. Absence-of-errors fallacy. If the system built is unusable and does not fulfil the user’s needs and expectations then finding and fixing defects does not help. If the product does not meet user requirements that may be explicitly mentioned and implicitly implied, that is if it is not fit for use, there is no point in testing it. 

## 2. The Various Testing Layers Analogy 

*There are many different types of testing that get employed on a piece of software. Let's first get an overview of the various software testing practices by comparing with the building of a vehicle in a factory.*

A car manufacturer does not produce a car as a whole car all at once. Each component of the car is manufactured separately, like seats, steering, mirrors, breaks, cables, the engine, car frame, wheels etc. The manufacturer performs many types of tests along the way to quickly find and address any issues that present during the build. 

**Unit tests:** After manufacturing each seperate module, it is tested in isolation as to whether it is working reliably the way it was designed to work.

**Integration tests:** When each individual module is combined with another, that assembled combination is tested to ensure assembling has not produced any side effects to the functionality of either component and whether both components are working together as expected.

**System tests:** Once all the parts are assembled and the car is ready to drive, the manufacturer needs to check different aspects of the car as a whole in a controlled environment and confirm the requirements have been met. Can the car can be driven smoothly, break quickly, shifts gears fluidly? Is system functionality working properly - does the car accelerate quickly and corner efficiently? Does the car pass basic saftey requirements like crashing and not hurting the occupants?

**End-to-end tests:** The car is then driven in real-world scenarios - traffic, city streets, evasive maneovers, getting rear-ended, smooth roads vs bumpy roads, freezing / wet / hot weather. End-to-end testing involves testing the unit in real-world environmental conditions that are occuring around the car under test.

**Load tests:** The engineers want to know where the point of failure is for the car. They drive it faster then it was designed to drive and let the engine run hotter then it is supposed to. The purpose of these tests is to find the products breaking point so they understand exactly how far a given design can be pushed and explore the outer limits of performance capacity. 

**Acceptance Tests:** The car then needs to be driven by real-world users in a focus group to find out how consumers feel about the capabilities of the product and get feedback. Do they feel like it's smooth? Do they like the color and look? Would they buy it? Would they reccomend it to their friends?    

**Regression Tests:** The car has been approved and is in production. In the future, the manufacturer finds out about an issue within the motor. They go back to their design and correct the issue. They now want to ensure that they have not created any side effects by fixing the motor. They procede to run all the tests again to ensure the new changes have not negatively effected any other aspects of the car. 

## 3. Unit Testing 

* Unit tests are short, quick and automated tests that ensure a specific module in your program works. 
* They will test specific functionality of a method or class and have a clear pass / fail condition. 
* With unit tests, developers ensure their code works and continues to work as they make changes to it in the future.
* The test only fails when a new bug is introduced or requirements change. If it fails, it should be easy to understand why.
* Unit testing is typically performed by the development team.

### 3.1 Unit Testing Guidelines 

*  State the name of the method being tested, inputs used and outputs expected.
```
 Multiply_PassOnePositiveAndOneNegative_ReturnCorrectAnswer(); 
 FindMatchingNumber_PassUserInteger_ReturnMatchingInteger();
```

* Test only one thing per test to create a readable, reliable test. Do not create long and complex tests that test everything in a single method. 
* Unit tests should be self-sufficient, isolated and avoid dependencies (databases, environment settings). A single test should not depend on other tests before it or the execution order of tests in general. Initialize and clean the test suite after every test run.   
* Test should be deterministic. It's unacceptable to have a test that passes unreliably - a test should either pass all the time or fail until fixed. Running the test 1000 times should return the same same result every time. Never use randomized data in a unit test as it creates uncertainty and impossible to recreate the test.  
* Use naming conventions. To know why the test failed, you need to be able to understand it at a glance.   
* Do repeat yourself. In writing tests, readability is of high importance. If tests are similarily structured, it makes it very easy to read through a suite of tests and know exactly what each piece is testing. 
* Test results and not implementation. Changing the inner workings of a method should not fail a unit test if the code produces the same output result. Implementaion will naturally grow and change as the project evolves. Private methods are part of the internal mechanics of a class and should only be tested if there is a very good reason to do so. Otherewise trivial refactoring can cause complication errors and failures in the tests. 
* Avoid overspecification. While it seems logical to create well-defined, controlled, strict tests that observe exact process flow, it can "lock" the scenario under test and prevent it from changing in ways that do not affect the result. 
* Use an isolation framework. Dependencies hinder the ability to write unit tests. When dependencies need a complex setup for the automated test to run, the result is fragile tests. A mocking framework has a set of API's for creating and using fake objects without the user needing to maintain details of the specific test.  

## 4. Integration Testing

* Integration tests should be written when combining two or more key modules together to ensure the modules all work fluidly together as a system. For example, an integration test could call a REST endpoint which calls a service which calls a test database to insert, then retrieve some information. If all the parts are working correctly, the integration test will pass. If any one of the modules is not configured properly, the test will fail and the developer will have to determine why.  
* Be clear about how integration is different than unit testing. 
* Encapsulation - Unit tests are encapsulated while integration tests rely on external resources. 
* Complexity - Unit tests target small and distinct parts of code while integration tests are more complex and often require a global setup / teardown. 
* Test failure - When a unit test fails, there is clearly a bug in the business logic. When integration fails, it's likely environmental issues that need to be addressed.  
* Integration testing is typically performed by the development team or a closely related QA team. 

### 4.1 Integration Testing Guidelines

1. Run unit tests before integration tests. Unit tests indicate whether the inner workings of a code base are operating properly which is a pre-req to ensuring that the various modules will function properly together. 
2. Don't test business logic with integration testing. Unit tests are for business logic and should be fast and not hinder a developers time. Intgeration testing takes longer and shouldn't be run as often as unit tests.
3. Keep your testing suites separate. Integration tests should not be run together with unit tests. Unit tests need to be run frequently and should not be inconvenient to run. By keeping test suites separate, developers feel free to run quick unit tests. Long and tedious integration tests should be reserved for the build server in a seperate suite to be run less frequently. 
4. Log extensively. Since unit tests have specific scope and test small pieces of code, it is clear why they fail. Integration tests can span several modules, devices and components. If these tests fails it's more complex to understand why. Exhaustive logging is the only way to analyze a failure and discover where the problem lies. Use a logging framework that can be controlled via flags that allow for minimal logging during passing tests and more when a test fails.  

## 5. System Testing 

* Once the application has been completed by having all its modules/components integrated, system tests are run which attempt to accurately reproduce your production environment while remaining in a safe, predictable development environment. The purpose of these tests are to validate functionality as a whole. They will test the various features as subsystems of an application and ensure user requirements have been met. It also tests how separte features interoperate as parts of a product.
* System testing testers are concentrated on finding bugs/defects based on software application behaviour, software design and expectations of the end user.
* System testing is typically performed by the development team or a closely related QA team.

**With over 50 different types of System Testing, what factors should be considered in choosing tests?**

* Who the tester works for - Methods used by large companies are different than those used by smaller ones.
* Time available for testing - Time is often what limits us to using only the types that are most relevant for the project.
* Resources available - Testers may not have resources to conduct a testing type, like expensive automated testing suites. 
* Software Tester's Education - There is a certain learning curve for each type of software testing available.
* Testing budget - Money is driving factor for all levels  of companies. 

**Common types of System Tests**

* Usability Testing - Focuses on the user's ease to use the application, flexibility in handling controls and ability of system to meet its objectives.
* Load Testing - The process of putting simulated demand on software, an application or website in a way that tests or demonstrates it's behaviour under various conditions.
* Recovery Testing - Done to demonstrate a software solution is reliable, trustworthy and can successfully recoup from possible crashes.
* Migration Testing - Ensures that the software can be moved from older system infrastructures to current system infrastructures without any issues.
* Functional Testing - Also known as functional completeness testing, Functional Testing involves trying to think of any possible missing functions.
* Hardware/Software Testing - Focuses attention on the interactions between the hardware and software during system testing.

### 5.1 System Test Guidelines

**FIGURE OUT ITGROOVES SYSTEM TESTING GOALS AND PUT HERE ONCE UNDERSTOOD**

## 6. End-To-End Testing

* The actual usage of an application goes beyond system testing by involving virtualization tools, databases, mail servers, DNS servers, proxy servers etc.. Software systems are composed of a multitude of functional modules that must communicate command and data information to each other. Even if the interfaces into and out of a code module have been verified to meet their specifications, they may encounter content and timing issues in real world usage.  
* Thus once the high-level architecture is validated through integration and system testing, End-to-End tests are used to test the application within its final production environment.
* End-to-end tests verify the use of the system controls to retrieve, manipulate and store data results in the intended activities at the database and API points of the system. They test message content integrity (did the the correct info get transferred throughout the chain) and operational timing (did content pieces/control get where they needed to be in the proper order). 
* End-to-end testing checks if an application performs as designed on all levels across all subsystems. The scope encompasses the application in its entirety, as well as its integration with external interfaces and outside applications. 
* End-to-End testing is typically performed by a technical QA team. 

### 6.1 End-To-End Testing Guidelines

* End-To-End tests should validate both the software system, all interconnected systems and external interfaces. They should look at backend and hardware to cover all functionality that the user experiences when using an application. 
* Manual end-to-end testing is more common due to the need of dealing with external interfaces.  
* End-to-end testing can be automated but the effort to do this is both extensive and transitory. Writing test scripts to perform a thorough test is typically as expensive as simply spending the hours to manually perform it and system changes (bug fixes, new features) require script re-writes to match.

**MORE ON END-TO-END TESTING ONCE WE START USING CYPRUS FOR LODGELINK2.0**  

## 7. User Acceptance Testing

* User acceptance testing is a process where an application is tested for business requirement acceptability and validates the end-to-end business flow.
* Acceptance tests are created by business customers and articulated in business domanin languages. Ideally it is a collaboration between business customers, business analysts, testers and developers.
* It consists of test suites which involve multiple test cases and each test case contains input data as well as expected output. 
* User Acceptance Testing is typically performed by the client, other business user or 3rd party testing company.

### 8.1 User Acceptance Testing Guidlines

* The official business requirements should be available and used to develop the the test cases around. 
* Test cases should also be developed around real world scenarios of end users.
* The actual testing should be carried out in a replica of the production environment using all external factors that the production environment will encounter. 

### 8.2 User Acceptance Testing Deliverables

* Test plan - To outline the testing strategy.
* Test cases - The test cases help the team to effectively test the application in the acceptance test environment.
* Results & Error Reports - This is a log of all the test cases executed and the actual results.
* Installation Instructions - This is a document which helps to install the sysetm in production environments.
* Documentation Materials - Tested and updated user documentation and training materials are finalized. 
* User Acceptance Signoff - This is the final signoff that system, documentation and training materials have passed all tests.

## 9. Regression Testing 

**Because when you fix one bug, you could introduce several new bugs** 

* Regression testing is testing that is done to verify that code change in the software does not impact the existing functionality of the product. It ensures the product works fine as previous with the newly added functionality or any change in the existing feature or once the bug fix is done. Previously executed test cases are re-executed in order to verify the impact of change.
* Regression testing is like a verification method. Test cases are generally automated as test cases are required to execute again and again and running the same test cases again and again manually is time consuming and tedious.
* Regression means retesting the unchanged parts of the application as well as the modified parts.
* Take a look at your test cases and determine if you will have to do a full, partial or unit regression.
* Unit regression - Done during the unit testing phase where code is tested in isolation. Any dependencies on the unit to be tested are blocked so that the unit can be tested individually without any discrepency.
* Partial Regression - done to verify that the code works fine even when the changes have been done in the code and that the unit is integrated with the unchanged or already existing code.
* Complete regression - done when a change in code is done on a number of modules and also if the change impact of a change in any other module is uncertain. Product as a whole is regressed to check any changes because of the changed code.

### 9.1 Regression Testing Guidelines 

* Analyze and determine what modules/parts of the software might be impacted – the development and BA teams can be instrumental in providing this information
* Prepare a Test suite for Regression testing considering what kind of changes have been made to the software.
* Automate all the test cases of the test suite.
* Run the regression tests which should include all previous tests. Compare the current results with previously executed test results.
* Update the Regression suite whenever it is required like if any new defect which is not covered in the test case is found, and a test case for the same should be updatedin the test suite so that the testing is not missed for the same next time. Regression test suite should be managed properly by continuously updating the test cases.
* Execute the Regression test cases whenever there is any change in the code, a bug is fixed, new functionality is added or any enhancement is done to the existing functionality.
* Create a test execution Report which includes Pass/Fail status of the executed test cases.
