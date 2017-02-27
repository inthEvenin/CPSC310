# Specifications

### Intro

- Specifications are documents used to **describe** a software system.
  - Specs connect customers and engineers and help to ensure that different parts of the implementation work together. 
  - A spec with define both what the system does and how the behaviour can be tested for correctness. 
  - Different specs are useful for different stakeholders.
- All software specifications are abstractions that abstract away some kinds of details so stakeholders can focus on other details.

### Requirements

- There are two broad categories of requirements:
  - **Functional requirements**: These describe what the system must do.
    - Ex) "They system shall let the user logout with a single click" provides a specific feature the system must have.
  - **Non-functional requirements**: These describe properties the system must have.
    - Ex) "The system should be usable" describes a property the system should exhibit.
- It is important to remember that requirements **describe** what system is to do, but **not how** it is to be done.
  - Ex) "A list should be sortable in O(nlogn) time" **vs** "A list will be used using quicksort"
- Non-functioanl properties play important roles in most systems. 
  - These include the 'ilities' like reliability, security, usability, complexity, evolvability, performance, etc.
  - By engaging stakeholders in discussions about requirements, we can help them to understand which are **most important for the successful operation** of the system.
- There are four important properties stakeholders should keep in mind when recording software specs:
  - ```Complete```: A spec that does not completely describe the requirements provide opportunities for **misunderstanding** between stakeholders
  - ```Consistent```: Conflicting requirements also generate **misunderstanding** that can make knowing the right behaviour **impossible** to understand.
  - ```Precise```: Natural language is inherently **imprecise** while source code must be **precise** for the computer to be able to interpret it. 
    - This disconnect, and the fact that specs cannot be automatically validated, means imprecise language can further complicate understanding intended behaviour.
  - ```Concise```: While the above points seems to say that *"more is better"* when it comes to specifications, having *"more"* also provides more space for imprecision and inconsistency to become problems.
- During the requirements elicitation process, several different types of requirements can be gathered in addition to the functional and non-functional properties; these include:
  - Design constraints
  - Environment constraints (new system should work with existing systems)
  - Preferences (not all requirements are equal)

### Validating requirements

- Being able to validate a requirement is clearly advantageous for the customer.
  - It is also good for the technical team as it makes their *"definition of done"* extremely clear.
  - If the objective was unrealistic, it should have been caught during requirements elicitation rather than during project accpetnace.
  - Being concrete also ensures that stakeholders have consistent expectations about the final product.

### User stories

- User stories are lightweight descriptors of features that are often used by engineers to specify software development tasks.
- Stories provide a concrete description that can be used by various project stake holders to **discuss features**, **their value**, **how they can be validated**, and **their cost**.
- Format: (Role - Goal - Benefit)
  - "As a ```<stakeholder>``` I want ```<function>``` so that ```<value>```"
  - One crucial aspect of user stories is their *definition of done*.
    - It provides a **specific description** of how the story can be **validated** by both the developer and the product owner to **ensure** it is completed correctly (helps developers avoid working unnecessarily on extra functionality the stakeholder might not need).
  - Any specific engineering notes required can be added to the story.
  - An effort estimate is typically attached.
- Set of guidelines called INVEST is often used to evaluate user stories:
  - **I**ndependent: Stories need to be **independent** and **self-containe**d so they can be **reordered and implemented as needed**. 
  - **N**egotiable: Choosing which stories are performed in the next iteration needs to be a **negotiable** activity. This also allows the product owner and technical team to ask more questions that **flesh out the story** and **provide greater detail** as needed.
  - **V**aluable: Being **clear** about the value of a story is important; most stories are not valuable to all stakeholders, but being able to have this conversation explicitly makes negotiating the relative benefits of various stories possible.
  - **E**stimable: If a story lacks sufficient detail to evaluate its **feasibility** (and how long it will take) more specification work is needed. One of the cornerstones of user stories is they make reasoning about tasks and maintaining schedules tractable; **if a story cannot be estimated it will not work in practice**.
  - **S**mall: User stories tend to describe features that take between half a day and half an iteration in length. Longer stories should be **split up to reduce** the chance of a story not making it in an iteration and so that future work on the story can be negotiated in the subsequent work period.
  - **T**estable: The definition of done is fundamentally important so all stakeholders **understand** the ways in which the story will be evaluated. This brings quality concerns to the forefront before development even starts and encourages that features be built in a verifiable manner.