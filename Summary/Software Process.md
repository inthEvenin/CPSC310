# Software process

- The core role fo software process is to **increase transparency** about the software development process so all stakeholders know **what is required** of them and **what they can expect** from others.
  - In this way, processes can help **ameliorate** risk by explictly **capturing** stakeholder expectations and constraints.

### Traditional approaches

- **Waterfall** is the 'classic' software development model. 
  - In Waterfall, each project phase **flows** into the next with explicit stakeholder **sign-off before the next phase begins**.
  - Shortcoming of waterfall-based processes: 
    - There is extreme pushback against **revisiting a prior phase**; once requirements are **complete**, the requirements are **fixed**. 
    - It is also **not flexible** in the face of **organizational change**.
    - The overall value of the system **cannot be validated** until the process has run to completion; this can be problematic for long-running projects.
- The **Spiral** model was introduced to increase the responsiveness of waterfall-based process.
  - In contrast to Waterfall, the Spiral model **revisits each system phase** on **each iteration**. It can be split into four main phases:
    - Planning
    - Risk analysis
    - Engineering
    - Evaluation
  - Compared to Waterfall, the spiral model enables much **greater sensitivity** to **changes** to requirements than waterfall.
  - Unfortunately, the overhead of performing effective risk analysis and review can be **overwhelming**, and the **duration** between spirals (often over one year) result in **large delays** between customer feedback.

### Agile approaches

- XP
  - XP mandated that systems should always be **buildable** and that developers should be willing to start **small**, **adapt** and **refactor** their systems as the need arose, rather than investing in huge up-front engineering efforts.
  - 5 key principles:
    - Communication
    - Simplicity
    - Feedback
    - Courage
    - Respect
- TDD
  - Test-driven development (TDD) emerged from the agile movement as an approach to ensure that automated testing was always a key part of the development process.
  - Set of steps for TDD:
    - Add a test.
    - Run the tests to ensure they fail.
    - Write the code/run the tests.
    - Refactor the code.
- Scrum
  - Scrum is an incremental iteration-based methodology that breaks work into fixed-length *sprints*.
  - Code after every sprint should be shippable, and propertested, but likely not complete.
  - A product has a global set of requirements left to be implemented known as the **product backlog**. The work items being worked on in each sprint are called the **sprint backlog**. 
  - Process-specific roles:
    - **Product owner**: This person defines product features and helps to prioritize features according to their value to the team.
    - **Scrum master**: This is a single person that facilitates the scrum process; often these people have attended workshops to learn techniques for keeping teams on track.
    - **Team**: Scrum-based teams are typically diverse and cross-functional containing designers, managers, engineers, clients, and test specialists. 
  - Three broad ceremonies:
    - **Sprint planning**: This takes place **before** the sprint and is an opportunity for the product owner to **describe** and **motivate** the **highest priority user stories** from the **product backlog** for the upcoming sprint. During this process, teams take the opportunities to **probe for additional information** so they can be sure they **adequately undestand the work that will be required**. Although the product owner sets the priorities, it is up to **technical teams** to build an estimate of how long each task will take.
    - **Standup meeting**: Also known as *daily scrum meeting*, this is when the team members talk about the **challenges they are facing** and **anything that is blocking their progress for that day**. **Only** the team members that are involved are allowed to speak, but attending is allowed for **everyone**.
    - **Sprint review**: After each sprint, review meetings are held for the teams to **demonstrate** their features to the product owner or other stakeholders (ex. doing demo, etc.). They also take this opportunity to **evaluate** how much **progress** has been made on the sprint backlog.
    - **Retrospective**: Since every product and team is unique, they take time to **reflect** on how the sprint worked out for them. During this time, they identify which activities the teams should **start doing, stop doing, or continue doing**. This is a good opportunity to make sure the process is **providing value for the team** and **find opportunities to improve** and **refine the activities the team is performing**.
