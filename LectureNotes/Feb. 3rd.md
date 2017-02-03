# Abstraction & Decomposition

### What is abstraction?

- Forcusing on essential details while supressing extraneous information for a given task
  - Information hiding
  - Encapsulation

### Data abstraction

```typescript
// Creates a new team.
// Requires: name is non-empty and unused
// Modifies: team database
// Effects: returns whether team was created
public createTeam(name: string):boolean {...}
```

### Top-down design

- Also known as functional decomposition;
  - Split a problem into independent parts.
  - Describe the responsibilities of each part.
- Splitting can be done according to:
  - Development teams
  - Application domains
  - Physical infrastructure
- Might be necessitate revisiting prior decisions.

### Bottom-up design

- Start with componenets and synthesize design.
- Higher emphasis placed on reusability as decisions about components are made with respect to future use.
- Flexible means of incorporating feedback.
  - Early prototyping easier when you can test components and subsystems concretely.
- Blended approcahes more common that either on its own:
  - using some …?

### Constant change

- Parameters change over time
  - Often by many orders of magnitude
- Right design at X might be wrong at 10X or 100X
  - … design for ~10X growth, but plan to rewrite before ~100X
- Continuous evolution
  - 7 significant revisions in the last 10 years
  - often rolled out without users noticing the change

### Architectural & design representations

- Abstractions are fundamentally about facilitating technical communication between project stakeholders
- An opaque abstraction or one abstracting the wrong detail has no value as it will not be adequately understood
- 3 properties of representation (Ambiguity, accuracy, ?)

### Static structure vs. dynamic behaviour

- Necessary to complile & deploy
  - Is it sufficient?
- Behaviour matters. Static relationships are only a subset of a complete system.
- Behaviour is inherently dynamic.
  - The code alone may not be sufficient.
  - Debugging only gives glimpses in time.
- Increased abstraction == decreased control