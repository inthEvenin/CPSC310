# Automation

### Intro

- Gone are the days where delivering once every 3-5 years was considered acceptable. Being able to deliver changes on a weekly, daily, or minute-by-minute basis allows software teams to more quickly deliver new products to market or provide more timely bug fixes.
- Software systems are increasingly large, distributed, and heterogeneous. Successfully building, testing, and deploying them requires coordinating a huge stack of tools, environments, and systems.
- The goal of automation is to transform this unsustainable way of building software into a process that is:
  - **Repeatable**: the process of building a product should not vary between different versions of the software.
    - A unified building process provides a mechanism for building the system the same way, every time with minial human intervention required.
  - **Reliable**: If the build process was repeatable but was subject to many non-deterministic failures it would not have value
    - Being able to trust that the repeatable process will run to its successful completion is crucial, although naturally test failures are sometimes to be expected and are not considered a build automation reliability failure.
  - **Revertible**: The build process should make it possible to quickly and transparently revert out of any change.
    - If a build is deployed and is found t o have an error in prodution, it should be possible to automatically rever to a prior build in a quick and transparent way.

### Automateable units

1. **Source** **control**: Every software team uses version control to track their source code resources (and other assets including any automation tools themselves).
2. **Dependency** **management**: Code is not developed in isolation; all systems are built upon a host of existing libraries and frameworks. Dependency management solutions provide a means to reliably procure software required for the build process.
3. **Build** **tools**: Compiling the code into shippable units (be they libraries or actual executables) is the next step. While these tasks are sometimes easy, they often involve many independent steps that are joined toegther by build tools.
4. **Test tools**: Tests are code too, so enabiling them to be written with as little boilerplate code as possible is important for reducing the costs of automated testing. Many unit test tools in particular have been developed to help software engineers write tests and form them into coherent test suits quickly.
5. **Test runners**: Once test suites have been developed they must be run in a repeatable way. While this can take place on the engineer's development machine, tests are often run on a common infrastructure to increase the consistency between test runs for all developers.
6. **Deployment**: In the online realm, software must be deployed once it is built.