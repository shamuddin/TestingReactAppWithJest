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
* BeforeEach runs a block of code before each test.
* Usefull for setting up databases, mock instances, etc.
* BeforeAll runs code just once, before the first test.

### [14] AfterEach and AfterAll
* Inverse version of BeforeEach and BeforeAll
* Runs a block of code after each test (or after the last test).
* useful for closing open connections, terminating sub-processes.

### [15] What are Asynchoronous Tests?
* Contains assertions (like a regular test).
* Does not complete instantaneously.
* Can take varying amount of time, even an unknown amount of time.
* Jest must be notified that test is complete.

### [16] Defining Asynchoronous Tests
* Invoke the done() callback that is passed to the test.
* Return a promise from a test.
* Pass an async function to describe.

### Examples
~~~bash
it("async test 1", done => {
    setTimeout(done,100)
});
~~~

~~~bash
it("async test 2", () => {
    return new Promise(
        resolve => setTimeout(resolve, 100)
    )
});
~~~

~~~bash
it("async test 3", async () => await delay(100)
);
~~~

### [17] Understanding Jest Mocks
* Why Mocking
    * Reduce dependencies required by tests (Faster execution).
    * Prevent side-effects during testing.
    * Build custom mock to facilitate desired testing procedures.

### [18] What is a Mock
* Convincing duplicate of an object with no internal workings.
* Can be automatically or manually created.
* Has same API as original side-effects.
* Spies and other mock features simplify testing.

### [19] The Mocking Processes
* Scan the original object for methods, give the new object spy methods with same names.
* Ensure that any methods which returned a promise still return a promise in the mock.
* Create mocks for any complex values that are returned from the methods which are required for tests.

### [20] Mock Functions
* Also known as "Spies".
* No side-effects.
* Counts function calls.
* Records arguments passed when they called.
* Can be "Loaded" with return values.
* Return value must approximate original.

### [21] Creating Mock Files
* Appropriately named NPM mock are loaded automatically.
* Mocks must reside in a __mocks__ folder next to mocked modules.
* NPM modules and local modules can both be mocked.

### [22] What is a Snapshot
* JSON-based record of a component's output.
* Compared to component's actual output during testing process.
* Committed along with other modules and tests to the application repo.

### [23] The Snapshot testing process
* Developer A authors a new component.
* Snapshot of that component's output is generated automatically.
* Developer A commits changes, moves on.
* Developer B makes a breaking change to a dependency of the new component.
* A new snapshot is automatically generated.
* Since the snapshots don't match, the test suite will fail until updated.

### [24] What does testing React Component Mean
* Verify output has not regressed.
* Ensure that rarely occuring corner cases produces the correct output.
* If component generates side effects, verify they occur but do not execute them.
* Verify user interactions are handled as expected.

### [25] Constructing Testable React Components
* Components may or may not have lifecycle handlers.
* Components may or may not have internal state.
* Components may or may not generate side effects.
* Component may get state from arguments, or from external dependencies.
* No internal state
    * Output is an idepotent product of the props that are provided.
* No side-effects
    * Any AJAX calls, UI changes or other side effects are handled by sagas, thunks, etc., but not by components.
* No lifecycle hooks
    * Fetching data is handled on the application level, not the component level.

### [26] React Redux and Jest
* Components don't generate side effects.
* Component consists of logical display and container components.
* Components do not have internal state.

### [27] Testing React Redux Components
* Test Container and Display elements separately.
* Use unit tests to verify methods and properties passed by container are accurate.
* Use snapshot tests to verify the output of the display component, passing props in directly.

### [28] Testing Statefull React Components
* Mock dependencies, then test them.
* Use spies to verify side-effects.
* Move logic from lifecycle to services.
* Prevent regression with snapshot.
* Inject values by writing mocks for services.
* Make stateless components, where possible.

### [29] What is a Matcher
* Also known as an assertion or expectation.
* Represents a claim that a value will be equal (or not) to something.
* Throws an error (test fails) if matcher's claim is not validated.

* HandWritten test
~~~bash
function test(){
    const value = getValue42();
    if(value !== 42){
        throw new Error("/**/")
    }
}
~~~
* If statement (condition).
* Throw an error.
* In test runner, the error result in test .failing, not in the application failing.

* Matchers
~~~bash
function test2(){
    const value = getValue42();
    expect(value).toEqual(42);
}
~~~
* Equivalent test using a mathcer.
* Matcher is equivalent to if statement above.

### [30] Exploring Matcher
* Guide URL : https://jestjs.io/docs/getting-started

* "Not" Matcher
    * Reverses an assertion.
    * If assertion without not would pass, asertion with not will fail.

* "To Be" and "To Equal" Matcher
    * Verify that two values are equivalent.
    * Two arrays with matching elements are equal, but not identical.
    * Very general - use more specific matcher when possible.

* "To Be Close To" Matcher
    * Like toEqual for numbers, but assertion still passes if number are close but not equal.
    * For assertions involving floating point numbers.

* "To Contain" & "To Have Length"
    * Array matcher which verify the contents and size of a collection.
    * More succinct than combining toEqual with array operators includes, length, etc.