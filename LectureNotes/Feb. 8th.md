# Technical Abstraction

### Sequence diagram

- Codify how elements communicate with each other.
  - Dynamic view; how do static structures interact?
  - Good for showing protocols & interactions.
  - Enables concrete reasoning about data flow.
    - Often uncovers missing information or missing links from the static class diagrams
- Almost always captures a specific task
- Particularly useful for async and distributed flows.

### State machine diagram

- Used to model complex behaviours and protocols.
- Extremely useful for event based modelling.
  - Essentially every UI
  - From an app-perspective states can often be thought of as screens/pages. Often used for reasoning about user flows.
- Can be used to reduce the complexity of event systems/
  - e.g., reason about when events are applicable.
  - Transitions run to completion (like JavaScript methods).