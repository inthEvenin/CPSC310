# Software testing

### Intro

- Software systems are only useful if they do what they are supposed to do.
  - This is increasingly important given the vital safety-critical roles modern software systems play.
  - Unfortunately, proving that a system is correct is exceedingly **difficult** and **expensive** for large software systems.
- In **Test-Driven Development** (**TDD**), the first develop step would be to write test for features that haven't been written yet to guide future development.

### Terminology

- A number of different terms are commonly used in the testing space:
  - ```SUT/CUT```: System / code under test. This is the thing that you are actually trying to validate.
  - ```White box testing```: When testing in a white box manner, one typically carefully **examines** the **program source code** in order to identify potentially problematic **set of inputs** or **control flow paths**.
  - ```Black box testing```: Black box testing validates program **without** any knowledge of how the the system is implemented. This form of testing relies heavily on **predicting problematic inputs** by **examining public API signitures** and **any** **available documentation for the CUT**.
  - ```Effectiveness```: The simplest way to reason about the effectiveness of a test or test suite is to **measure the probability the test will find a real fault** (per unit of effort, which can be something like developer creating / maintenance time or number of test executions)
  - ```Higher/lower testability```: Some systems are significantly easier to test than others due to the way they are constructed. A highly testable system will enable more effective tests for the same cost than a system whose tests are largely ineffective (or require an outsized amount of creation and maintenance effort).
  - ```Repeatability```: The likelihood that running the same test twice under the **same conditions** will yield the **same result**.
- There are a number of different ***levels*** of test; these range in *size*, *complexity*, *execution duration*, *repeatability*, along with how *easy* they are to *write*, *maintain*, and *debug*.
  - ```Unit```: Unit tests exercise **individual components**, usually **methods** or **functions**, in **isolation**. This kind of testing is **usually quick to write** and the tests **incur low maintenance effor**t since they touch such **small parts** of the system. They typically ensure that the unit fulfills its contract making test failures **more straightforward** to **understand**.
  - ```Integration```: Integration tests exercise **groups of components** to ensure that their contained units interact correctly together. Integration tests touch much **larger pieces of the system** and are more prone to spurious failure. Since these test validate many different units **together**, identifying the root-cause of a specific failure can be **difficult**. 
  - ```End-to-End```: Also referred to as ***acceptance*** testing, these tests typically validate **entire customer flows**. They are especially useful for **validating quality attributes** (such as *performance* and *usuability*) that **cannot** be captured in isolation. These tests are great for **ensuring** that the system behaves correctly but provide **little guidance** for understanding **why** a failure arose or **how** it could be fixed.
  - ```A|B```: A special subset of testing that is typically employed in production environments. In A|B testing, two different versions are compared at **runtime** to validate which one performs *'best'*. A|B testing is often used to **validate business decisions**, rather than evaluate functional correctness.
  - ```Smoke/Canary```: This is a subset of a test suite that typically executes quickly, is high reliable, and has high effectiveness. Smoke tests try to expose a fault as quickly as possible, making it possible to **defer** running large swaths of **unnecessary** tests for a system that is know to be broken (for example, if you have an error in your data model that touches your whole system, there is no need to run slow integration and end-to-end tests).

### Testability

To write a successful test, it needs to be able to execute the code you wish to test, in a way that can **trigger** a defect that will propagate an incorrect result (which it can be checked against the expected behaviour). These are four high-level properties required for effective test writing and execution:

- Controllability
  - Tests dynamically execute the system. If the CUT **cannot** be **programmatically controlled**, an automated test **cannot** be **written** for it.
  - There is often a controllability tradeoff between what code it is **possible** to write a test for and what code it is **efficient** to write a test for. 
- Observability
  - Sometimes the CUT can be invoked by a test but its outcome **cannot** be **observed**. 
  - For example, if a defective method mutates some external inaccessible object but does not return a value.
    - Often these can be resolved by returning data to the callee that might otherwise just been passed further down a call chain.
  - One surprising challenge when considering observability is determining what values are correct and what values are erroneous.
- Isolateability
  - Being able to isolate the CUT under test is crucial to be able to **quickly determine** what has caused a failure so it can be resolved. 
  - This is challenging in large modern system due to the number of dependies (often third party) software systems have (its huge).
  - In simulation-based environments, code dependencies are **mocked** or **stubbed** whereby they are replaced with **developer-create fake components** that take **known** inputs and return **known** values.
    - In addition to isolation, mocking also greatly increases performance and make components less prone to non-determinism as the result being returned.
    - Mocking can also make it possible to test program states that would otherwise be hard to trigger in practice.
- Automatability
  - The above properties all aim to support making it possible to automate the execution of the test suite. 
  - The automated test suits are more likely to be run after a system has been released in the form of a regression suite to ensure that a system continues to execute as expected.
  - All systems exist within organizations, even if the software does not change, external dependencies, libraries, frameworks, and computing infrastructure will which will require continous validation of even deployed systems
  - Automated tests are also economically beneficial.
  - Automated tests also can be run online as changes are made to a system.
  - Automated tests also provide global visibility of the state of the system.

It is often necessary to **restructure** the software that has not been written in a testable way to make it possible to validate a system effectively. One of the biggest advantages of Test-Driven Development (TDD) is that by writing your tests first, you are able to ensure that your system is structured in a **testable way**.

### Why not test?

- Ultimately, testing does have a cost; since tests are **also programs**, they take time to **write**, **debug**, and **execute** and must also be **evolved along with the system**.
- It is not the case that the only bug-catching tests have values. Passing tests do give us the warm feeling that we have not introduced unexpected regression bugs into our systems.

### Assertions

- A key skill when creating automated unit tests is evaluating the **correctness** of the code under test. 
- While a compiler can **validate** the **syntax** of a program, a test suite is required to **ensure** its **runtime behaviour** matches its specificiation.
- **Assertions** are the primary piece of machinery used to evaluate correctness within automated unit test suites.
  - jUnit was one of the early (and still most popular) unit testing frameworks, and it is not surprising that many modern frameworks provide features similar to jUnit's assertion features for evaluating program outputs.
- There are several high-level models to consider when structuring tests; two of the most widely used are:
  - ```Four-Phase Tests```: This model is supported by default by jUnit and its variants.
    - The four phase correspond to:
      - 1) **setting up** the testing environment
      - 2) **executing** the code under test (CUT)
      - 3) **evaluating** the output of the CUT
      - 4) **tearing down** the testing environment.
  - ```Give-When-Then```: This model was developed by the **behavioural driven programming (BDD)** community which strives to create 'executable specifications' throught unit tests that use **descriptive strategies** for **nesting** and **naming**.
    - Tests are structured from some **given** state, where the system's configuration is understood.
    - The key action of the test is the **when**; this is often described in the test name using plain language (e.g., ```it('should be able to parse a document that has UTF-16 characters')```).
    - The **then** step involves observing the output to ensure its correctness. 
- It is often best to have each behaviour tested independently as possible.
  - This eases debugging because a change that breaks a behaviour will be easy to isolate as it will only have broken one tests and not a handful.
  - It also eases program evolution because changing a behaviour will not require modifications to lots of different tests.
- When creating our tests we can break down the behaviours we are testing three ways:
  - Normal conditions: The normal conditions represent the way we expect to be used.
  - Unexpected conditions: The unexpected conditions arise when the code is used in unexpected ways.
  - Boundary conditions: All programs consume input; by testing boundray values, we can ensure our program will successfully operate with the breadth of inputs the program might encounter.

### Coverage

- When evaluating the quality of the system, we really want insight into how well the system performs its expected tasks and how robustly it responds to unexpected inputs and situations. 
- Since the system code is supposed to both perform the expected operations and handle unexpected ones, coverage can make sure we are testing both of these aspects of the system.
- Coverage has two properties in particular that make it appealing:
  - It is relatively **cheap** to compute. In contrast to reasoning about expected and unexpected behaviours, a veroage tool simply needs to track which parts of a program have executed when the test suite is executing.
  - It is **actionable**. Developers can look at the output of a coverage report, find the parts that are not currently covered by the test suite, and decide how to act upon this information in a straightforward way.
- There are many flavours of coverage that areused in practice, here are three of them:
  - ```Statement```: This measures the **fraction** of the statements of the code that are executed. **Statement** and **line coverage** are both the **simplest** forms of coverage. Statement coverage considers **every statement within the system**.
  - ```Decision```: Decision (and branch) coverage checks to make sure that **all branching options** within the system are executed. Decision coverage only measures those program points where execution can take divergent paths within the system.
    - For example, decision coverage checks whether both true and false branches of ```if``` statements are executed by the test suite.
  - ```Modified Condition (MCC)```: MCC coverage checks **all program entry** and **exit points** along with the **every combination of decisions** within the program.
  - Strength: MCC > Decision > Statement
    - The stronger the coverage criteria, the more strigently we can say the code was covered by the test suite.
- The greatest shorting coming of coverage is that while it clearly shows that the suite **executes** the code under test, it does not show that the code under test is **correct**.

Sample code and its test:

```typescript
1: eval(x: number, c1: boolean, c2: boolean): number {
2:  if (c1)
3:    x++;
4:  if (c2) 
5:    x--;
6:  return x;
7: }
```
```typescript
// 60% statement coverage, 50% decision coverage, 25% MCC coverage
1:	eval(0, false, false);
```

```typescript
// 100% statement coverage
eval(0, true, true);

// 100% decision coverage
eval(0, true, true);
eval(0, false, false);

// 100% MCC coverage
eval(0, true, true);
eval(0, false, false);
eval(0, true, false);
eval(0, false, true);
```