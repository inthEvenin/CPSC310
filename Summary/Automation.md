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