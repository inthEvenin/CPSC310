# API

### Intro

- **Application Programming Interface** (API) describe the programmatic interfaces used for interacting with a software system.
- The primary purposes of APIS are to **provide** a **predictable means of programmatic interaction** and to **hide implemenetation details** from the API client.
  - By hiding the internal implementation, APIs enable the API owner to change their underlying implementation **without** affecting any clients that may depend upon it.

### Design principles

- At high-level, the principles behind good API design mirror that of good design in general. The first two questions to consider when designing the API are:

  - What is the **goal** of the API?
  - Who is the API's **intended customers**?

- Some high-level API design advice includes:

  - APIs should do **one thing**, and do it **well** (aka single responsibility principle)

  - APIs should be kept as **small** and **simple** as possible; once an API is released, it is **hard** to remove.

  - APIs should **never** expose internal implementation details; these make it **difficult** for the **consumer** to **use** and for the **maintainer** when they want to **change** an internal implementation detail.

  - The *'usuability'* of a system to another engineer is dictated by the **quality** of the API. This means **names** should be **well considered** and **consistent** and the APIs, their **constraints**, and their **pre-** and **post-conditions** should be **documented**.

    ​