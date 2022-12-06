# Testing React App With Jest

### [1] OverView
* How to install Jest.
* Running tests with Jest.
* Scaffold tests using mocks.
* Test fully-featured React Components.

### [2] Version Check  (Not appliciable for React 17.0 or latest)
* React 16.0.0 [v16.0.0 to v16.4.0]
* Jest 26.6.3 

### [3] Objectives
* General understanding of testing and realted architecture (How, Why).
* Jest Installation, test-running and detailed API Analysis.
* Moking - How and Why and Implementation.
* Unit, Component and Snapshot testing in practice.

### [4] Why Testing
* Prevent regression.
* Provides objective success criteria.
* Facilitates complex modular applications.

### [4] What are Tests
* A suite of tests is an application which checks your application.
* Composed of assertions about how your code will execute.
* Test files are comitted to the repo with application code.
* Suite is run quickly and routinely by CI tools.

### [5] Different Kinds of Tests
* Unit Test
    * Tools: Jest / Mocha
* Component Test
    * Tools: Jest / Enzyme
* Snapshot Test
    * Tools: Jest
* End-to-End Test
    * Tools: Protractor / Cypress

### [6] Introduction to Jest
* A library installed via NPM or Yarn and run via command line.
* Similar to popular test-runner but with handy extra features.

### [7] The Jest Tesing Ecosystem
* Jasmine/Mocha
    * Test-runner that organizes tests into "describe" and "it" blocks (or "suite" and "test").
    * All assertions inside tests are verified whenever the test-runner is invoked.
    * Doesn't include mocking or snapshots
 
 * Jest
    * Bulit on top of Jasmine/Mocha.
    * Adds snapshot testing, mocking and many other useful features.
    * Includes superior assertion library, CLI
    * Works with or without React

* Enzyme
    * Not a test runner like Jest, but provides tools to test React apps specifically.
    * Expresses component output as HTML (Like React Test Renderer).
    * Potentially useful but not for every project.

* Jest vs. Mocha
    *                     Jest        Mocha
    *        Runs Tests    Yes         Yes
    *        Async         Yes         Yes
    *        Spies         Yes         No
    *        Snapshot      Yes         No
    *        Mocking       Yes         No

* Jest
    * The actual test-runner library which you use to execute your tests

* Jest CLI
    * A tool that you use from the command line to provide configuration options to Jest

# Test Running with Jest

### [8] Jest Installation
Step 1: Install dependencies
~~~bash  
npm install && npm run postinstall
~~~  

Step 2: Install Jest CLI
~~~bash  
  npm install -g jest-cli
~~~  

Step 3: Run Cmd jest
~~~bash  
  folderPath> jest
~~~  

If you expect below erroe message:
~~~bash 
jest.ps1 is not digitally signed. You cannot run this script on the         
current system. For more information about running scripts
and setting execution policy, see about_Execution_Policies
at https:/go.microsoft.com/fwlink/?LinkID=135170.
~~~  

Execute this cmd:
~~~bash 
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
~~~

Step 4: Add Jest test script in package.json 
~~~bash
"test": "jest"
~~~

### [9] How are test files identified
* Any files inside a folder named __tests__ are considered tests.
* Any Files with .spec or .test in their filename are considered tests.

### [10] Jest Globals
* IT (Test)
    * Method which you pass a function to that function is executed as block of tests by the test runner
* DESCRIBE (SUITE)
    * An optional method for grouping any number of IT or test statements

### [11] Create a test folder src/components
* Create a __test__ folder
* Create a test file named "QuestionDetail.js"
* Create a test file named "QuestionList.spec.js"

### [12] Jest Watching for Changes

Watch for Changes - Terminal
~~~bash
folderpath> jest --watch
~~~

### [13] BeforeEach and BeforeAll
* BeforeEach runs a block of code before each test
* Usefull for setting up databases, mock instances, etc.
* BeforeAll runs code just once, before the first test
