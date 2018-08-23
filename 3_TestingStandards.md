# itgroove Testing Standards

Objective: This document has been written to create itgroove standards surrounding testing of code.

<!-- START doctoc generated TOC please keep comment here to allow auto update -->
<!-- DON'T EDIT THIS SECTION, INSTEAD RE-RUN doctoc TO UPDATE -->
**Table of Contents**  

- [1. General Testing Principles](#1-general-testing-principles)
- [2. The Various Testing Layers Analogy](#2-the-various-testing-layers-analogy)
- [3. Unit Testing](#3-unit-testing)
  - [3.1 Unit Test Names](#31-unit-test-names)
  - [3.2 Unit Testing Guidlines](#32-unit-testing-guidlines)
- [4. Integration Testing](#4-integration-testing)
  - [4.1 Integration Teting Guidlines](#41-integration-teting-guidlines)
- [5. System Testing](#5-system-testing)
  - [6. End-To-End Testing](#6-end-to-end-testing)
- [7. Load Testing](#7-load-testing)
- [8. Acceptance Testing](#8-acceptance-testing)
- [9. Regression Testing](#9-regression-testing)

<!-- END doctoc generated TOC please keep comment here to allow auto update -->

## 1. General Testing Principles 

* itGroove adheres to the principles outlined in "Foundations of Software Testing" by Rex Black, Erick Van Veenendaal, Dorothy Graham. Below is a summary by Vineeta Gakhare at https://www.utest.com/articles/seven-testing-principles.  

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

**Unit tests:** After manufacturing each seperate module, the module is tested in isolation as to whether it is working reliably the way it was designed to work.

**Integration tests:** When each individual module is combined with another, that assembled combination is tested to ensure assembling has not produced any side effects to the functionality of each component and whether both components are working together as expected.

**System tests:** Once all the parts are assembled and the car is ready to drive, the manufacturer needs to check different aspects of the car as a whole in a controlled environment and confirm the requirements have been met. Can the car can be driven smoothly, break quickly, shifts gears fluidly? Is system functionality working properly - does the car accelerate quickly and corneer efficiently? Does the car pass basic saftey requirements like crashing and not hurting the occupants?

**End-to-end tests:** The car is then driven in real-world scenarios - traffic, city streets, evasive maneovers, getting rear-ended, smooth roads vs bumpy roads, freezing / wet / hot weather. End-to-end testing involves testing the unit in real-world environmental conditions that are occuring around the car under test.

**Load tests:** The engineers want to know where the point of failure is for the car. They drive it faster then it was designed to drive and let the engine run hotter then it is supposed to. The purpose of these tests is to find the products breaking point so they understand exactly how far a given car can be pushed and explore the outer limits of performance capacity. 

**Acceptance Tests:** The car then needs to be driven by real-world users in a focus group to find out how consumers feel about the capabilities of the product and get feedback. Do they feel like it's smooth? Do they like the color and look? Would they buy it? Would they reccomend it to their friends?    

**Regression Tests:** The car has been approved and is in production. In the future, the manufacturer finds out about an issue within the motor. They go back to their design and correct the issue. They now want to ensure that they have not created any side effects by fixing the motor. They procede to run all the tests again to ensure the new changes have not negatively effected any other aspects of the car. 



## 3. Unit Testing 

* Unit tests are short, quick and automated tests that ensure a specific part of your program works. They test specific functionality of a method or class that have a clear pass/fail condition. By writing unit tests, developers can make sure their code works, before passing it to QA for further testing.
* The test only fails when a new bug is introduced into the system or requirements change. 
* When the test fails, it should be easy to understand the reason for the failure. 

### 3.1 Unit Test Names
* Use the scenario tested and expected result as part of of the test method name. State name of method being tested, inputs then outputs expected in the name. ex. Multiply_PassOnePositiveAndOneNegative_ReturnCorrectAnswer(); 

### 3.2 Unit Testing Guidlines 
1. Test only one thing per test to create a readable, reliable test. Do not create long, fragile and complex unit tests that test everything in a single method. 
2. Unit tests should be self-sufficient. Great unit tests should be isolated and avoid dependencies (databases,environment settings etc.). A single test should not depend on other tests before it or the execution order of tests in general. Running the test 1000 times should return the same same result every time. Initialize and clean the test suite after every test run.   
3. Test should be deterministic. It is unacceptable to have a test that passes only some of the time. A test should either pass all the time or fail until fixed! Having a unit test that only works some of the time is comperable to not having a test at all. Never use randomized data in a unit test as it creates uncertainty and makes it impossible to recreate the test.  
4. Naming conventions. To know why the test failed, you need to be able to understand it at a glance. 
5. Do repeat yourself. In writing tests, readability is of high importance. If tests are similarily structured, it makes it very easy to read through a suite of tests and know exactly what each piece is testing. 
6. Test results, not implementation. Having the inner workings of code change should not fail a unit test if the code produces the same output result. The unit test is not meant to test the inner workings of a method, just it's output. Implementaion naturally will grow and change as the project evolves. Private methods are part of the internal mechanics of a class and should only be tested if there is a very good reason to do so. Otherewise trivial refactoring can cause complication errors and failures in the tests. 
7. Avoid overspecification. While it seems logical to create well-defined, controlled, strict tests that observe exact process flow, it can "lock" the scenario under test and prevent it from changing in ways that do not affect the result. 
8. Use an isolation framework. Dependencies hinder the ability to write unit tests. When dependencies need a complex setup for the automated test to run, the result is fragile tests. A mocking framework has a set of API's for creating and using fake objects without the user needing to maintain details of the specific test.  


## 4. Integration Testing

* If a test is an integration test if it is using a database, network, external system (a queue or a mail server) or reads/writes file or performs other I/O. 

* Integration testing is a testing approach to test the integration among two or more objects that should work and interact together. 

### 4.1 Integration Teting Guidlines

Best practices for continuous integration testing. https://techbeacon.com/6-best-practices-integration-testing-ci-environment
1. Run unit tests before integration tests. Unit tests indicate whether the inner workings of a code base are operating properly which is a pre-req to ensuring that the various modules will function properly together. 
2. Don't test business logic with integration testing. Unit tests are for business logic and should be fast and not hinder a developers time. Intgeration testing takes longer and shouldn't be run as often as unit tests.
3. Be clear about how integration is different than unit testing. 
* Encapsulation - Unit tests are encapsulated while integration rely on external resources. 
* Complexity - Unit tests target small and distinct parts of code while integration are mero complex and often require setup/teardown. 
* Test failure - When a unit test fails, there is clearly a bug in the business logic. When integration fails, it's likely environmental issues that need to be addressed.  
4. Keep your testing suites separate. Integration tests should not be run together with unit tests. Unit tests need to be run frequently and should not be inconvenient to run. By keeping test suites separate, developers feel free to run quick unit tests. Long and tedious integration tests holud be reserved for the build server in a seperate suite to be run less frequently. 
5. Log extensively. Since unit tests have specific scope and test small pieces of code, if they fail it is clear why. Integration tests can span several modules, devices and components. If these tests fails, it's more complex to understand why. Exhaustive logging is the only way to analyze a failure ad discover where the problem lies. Use a logging framework that can be controlled via flags that allow for minimal logging during passing tests and more when a test fails. 
6. Don't stop at integration tests. Integration is simply how specific modules work together. The actual usage of your application goes beyond this involving virtualization tools, databases, mail servers, DNS servers, proxy servers etc.. The end users experience depends on both your application and how it's deployed in a production environment and works with all the other peripheral components. So once you have validated your high-level architecture with integration testing, make sure you run systems tests that accurately simulate your production environment. 

## 5. System Testing 

* Validates the software system but doesn't look outside of it.
* Looks at system features (viewing each feature as a subsystem).
* Follows integration testing. 
* Is easier to automate thought manual system testing is still a widespread practice.

* System testing means testing the system as a whole. All the modules/components are intergrated in order to verify if the system works as expected or not. 

* If an app has three modules - A, B, C then testing done on any two modules, either A + B, B + C, C + A would be integration testing. Integrating all three modules and testing it as a complete system is termed as system testing. 

* System testing precedes end-to-end testing. It checks whether the functionality of the system meets the requirments and it looks at how separate features interoperates as parts of a product. 

* During the process of manufacturing a ballpoint pen, the cap, the body, the tail, the ink cartridge and the ballpoint are produced separately and unit tested separately. When two or more units are ready, they are assembled and Integration Testing is performed. When the complete pen is integrated, System Testing is performed.

### 6. End-To-End Testing


End-to-End testing is typically performed by a technical QA team, whereas User Acceptance Testing is typically performed by a business user.

* End-to-end testing checks if an application performs as designed on all levels across all subsystems. The scope encompasses the application in its entirety, as well as its integration with external interfaces and outside applications. 

* Validates both the software system, all interconnected systems and external interfaces.
* Looks at backend and hardware to cover all functionality that the user experiences when using an application.
* Follows system testing.
* Manual end-to-end testing is more common due to the need of dealing with external interfaces. 

* End-to-end testing is the verification of a fully functional system's ability to respond to its user interface with appropriate activity at all the extremities of its connections.

* Software systems are composed of a multitude of functional modules that must communicate command and data information to each other. Even if the interfaces into and out of a code module have been verified to meet their specifications, they may encounter content and timing issues in real world usage. 

* End-to-end tests verify the use of the system controls to retrieve, manipulate and store data results in the intended activities at the database and API points of the system. They test message content integrity (did the the correct info get transferred throughout the chain) and operational timing (did content pieces/control get where they needed to be in the proper order). 

* The downside is cost. With its extreme setup and overall control and monitoring requirements, this is easily the most expensive and time-consuming software quality test method. 

* End-to-end testing can be automated but the effort to do this is both extensive and transitory. Writing test scripts to perform a thorough test is typically as expensive as simply spending the hours to manually perform it and system changes (bug fixes, new features) require script re-writes to match.


* Here is the first general guideline
* Here is the second general guideline

## 7. Load Testing

Load testing is the process of putting simulated demand on software, an application or website in a way that tests or demonstrates it's behaviour under various conditions. 

Load testing involves applying ordinary stress to a software application or IT system to see if it can perform as intended under normal conditions. It is related to stress testing, but load testing ensures that a given function, program, or system can handle what it's designed to handle while stress testing is about overloading / applying unlikely load scenarios upon the software until it breaks. 

Load testing best practices:
1- Clear browser cache and cookies before recording traffic. 
2- Start recording a new scenario from the 

## 8. Acceptance Testing

End-to-End testing is typically performed by a technical QA team, whereas User Acceptance Testing is typically performed by a business user.

* Project is submitted to a 3rd party company for testing purposes. They may conduct a wide range of tests depending on the what they have been requested to do.

User Acceptance Test is a phase in a typical software development process.

From the other side, End-To-End test is one of the approaches to testing the complex applications which involves all layers of the application to interact with each other during test execution.

It means that you can execute End-to-End test in User Acceptance Test phase, and you can't consider those two terms as one, that has the same meaning.
 The perspectives are different, and while some duplication of effort could happen, the defects identified may vary.

## 9. Regression Testing 

* Regression : "when you fix one bug, you introduce several new bugs". 

* Regression testing is testing that is done to verify that code change in the software does not impact the existing functionality of the product. Ensures the product works fine as previous with the newly added functionality or any change in the existing feature or once the bug fix is done. Previously executed test cases are re-executed in order to verify the impact of change. 

* Regression testing is like a verification method. Test cases are generally automated as test cases are required to execute again and again and running the same test cases again and again manually is time consuming and tedious one too.

* Regression means retesting the unchanged parts of the application. 

* Regression tests methodology - Re-run the previous tests. Compare the current results with previously executed test results. 

* Various types of regression tests: 
  1- Unit regression - done during the unit testing phase and a code is tested in isolation. Any dependencies on teh unit to be tested are blocked so that the unit can be tested individually without any discrepency.

  2- Partual Regression - done to verify that thet code works fine even when the changes have been done in the code and that the unit is integrated with the unchanged or already existing code. 

  3- Complete regression - done when a change in code is done on a number of modules and also if the change impact of a change in any other module is uncertain. Product as a whole is regressed to check any changes because of the changed code. 

* Process as outlined in https://www.softwaretestinghelp.com/regression-testing-tools-and-methods/
  1- Prepare a Test suite for Regression considering the points mentioned in “How to select Regression Test suite”?
  2- Automate all the test cases of the test suite.
  3- Update the Regression suite whenever it is required like if any new defect which is not covered in the test case is found, and a test case for the same should be updated in the test suite so that the testing is not missed for the same next time. Regression test suite should be managed properly by continuously updating the test cases.
  4- Execute the Regression test cases whenever there is any change in the code, the bug is fixed, new functionality is added, an enhancement to the existing functionality is done etc.
  5- Create a test execution Report which includes Pass/Fail status of the executed test cases.

* Understand what kind of changes have been made to the software
* Analyze and determine what modules/parts of the software might be impacted – the development and BA teams can be instrumental in providing this information
* Take a look at your test cases and determine if you will have to do a full, partial or unit regression. Identify the ones that will fit your situation
* Schedule the time and test away!
