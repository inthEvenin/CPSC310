# Specification

### Writing specs is hard (follow-up from class activity)

- Was it complete?
- Was it consistent?
- Was it precise?
- Was it concise?

### Measuring Requirements

- "To measure is to know. If you can not measure it, you can not improve it."
- We must explicitly quantify requirements.
- -> and verify that they are met.
- In practice, it turns out that measureable objectives are usually achieved.
- Having explicit measures provides explicit goals.
- Explicit goals arise from concrete discussions about values.

### Performance

### Reliability

- Trying to maximize availability
- Mean Time Between Failures (MTBF)
- Minimum uptime
- How do failures influence the rest of the system
- Operational availability
  - Availability - error downtime - admin downtime
- Mean Time To Resume (MTTR) [from failure]

### Complexity

- Lines of code
- Cyclomatic complexity
  - Independent closed loops on minimal graph
- Number of branches
- CallGraph statistics (e.g., node order)
  - Number of direct/indirect in edges
  - Number of direct/indirect out edges
- Bug reintroduction rate

### Security

- Number of vulnerabilities
- Number of security process violations
- % of system tested security tested
- % of threats with contingency plans
- Explicit monitoring
  - Intrusion / incident / dashboards
- Risk / benefit in explicit $ terms



