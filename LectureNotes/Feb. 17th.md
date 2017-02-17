# Information Security

### Threat modelling

- Who is attacking the system?
  - Accident
  - Disgruntled employee
  - Automated malware
  - Curious attacker
  - Script kiddies
  - Motivated attacker
  - Hacktivitsts
  - Organized crime
  - Cyber terrorists
  - State actors
- What are they trying to do?
  - Steal end-user data.
  - Direct financial gain.
  - Acquire/delete corporate data.
  - Damage reputation
  - Steal intellectual property.
  - Decrease productivity.
- Which vulnerabilities are they using?

### STRIDE

- **S**poofing: Pretend to be someone else.
- **T**ampering: Modifying data.
- **R**epudiation: Denying performing a task.
- **I**nformation Disclosure: Access private information.
- **D**enial of Service: Halt service.
- **E**levation of Privilege: Gaining unauthorized privileges.

### Attack tree

- Attacker: Who is doing it?
- Goal: What are they trying to do?
- Attack: How are they going to do it?
  - Break login:
    - Guess user/pass.
    - Use known vulnerability.
    - Phishing a password change.

### DREAD

- **risk** = damage(1…10) + reproducibility(1…10) + usersNumber(1...10) + discoverability(1…10)

### Minimize attack surface

- Attack surface is the 'size' of your input/output mechanisms.
  - The fewer ways in, the easier it is to secure them.
- OWASP definition:
  - The numer of i/o mechanisms.
  - The code securing those mechanisms.
  - The data being transmitted.
  - The code & mechanisms securing the data.
- Often conflicts with functional goals.

### Defence in depth

- A small breach shouldn't become a big one.
  - Need to minimize access within the system.
- Action:
  - Don't rely on border security alone.
  - Vary mechanism.
  - Avoid failure propagation.
- Downside:
  - Adds complexity, redundancy.

### Least privilege

- Coarse-grained privileges allow:
  - Malicious access
  - Accidental access
- Action:
  - Finer-grained privileges, roles, access control lists
  - Microservices
- Downside:
  - More complicated (in code and in usage)

### Separation of duties

- A single bad actor can cause great harm in secure system.
  - High-impact tasks should be validated.
  - Also good for protecting against accidents.
- Action:
  - Introduce internal process for impactful tasks.
  - Usually manual, but could also be automated.
- Downside:
  - Decreased velocity.

### Strong authentication

- If it is 'easy' for an adversary to gain access to your system, they will.
- Action:
  - Multi-factor authentication (commonly) :
    - Know something
    - Have something
- Downside:
  - Velocity, complexity

### Non-repudiation

- System users must be held accountable.
  - Not just for misbehaving users, also for tracking attackers.
- Action:
  - Atomic, write-only, auditing.
- Downside:
  - Audit logs are also sensitive information that could be compromised.

### Security mitigation in practice

- After a system has been modelled and its threats understood, we can start to design mitigation strategies.
- Google is a pretty lucrative adversarial groups.
- They have deployed a wide range of mitigation strategies.
- These range from custom hardware all the way through secure development practices.

### Google security infrastructure

- High-level goals:
  - Secure deployment of services.
  - Secure storage of data with end user privacy safeguards.
  - Secure communications between services.
  - Secure and private communication with customers.
  - Safe operation by administrators.
- All Google services are built on this infrastructure.

### Low level infrastructure

- Hardware infrastructure
  - Secure boot stack & machine identity
  - Hardware design and prevenance
  - Physical device security
- Service deployment
  - Access data management
  - Inter-service encryption
  - Inter-service access management
  - Service isolation

### Mid level infrastructure

- User identity
  - Authentication
  - Abuse detection
- Secure data storage
  - Encryption at rest
  - Deletion of data
- Internet communication
  - Google front end
  - DoS protection

### High level infrastructure

- Operational security
  - Intrusion detection
  - Reducing insider risk
  - Employee device & credentials
  - Safe software development:
    - Anti-XSS libraries
    - Tools: static analysis, fuzzers, security scanners
    - Security reviews
    - Vulnerability rewards program