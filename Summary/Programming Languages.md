# Programming Languages

### Definition

- It defines the vocab used to encode our ideas about what a computer should do in a format that a computer can understand. 

### Two main goals of programming languages

1. To provide a format that is understandable to humans as they encode their intent for the desired behaviour of a program.
2. To provide a format that can be unambiguously understood by automated tools enabling the language to be transformed into more compact executable representations.

- Tension between making a programming language easy to read and understand by developers and making it imprecise for machine analysis and transformation.

### Learning new languages

- Being able to quickly self-learn new languages is a fundamental skill for all software engineers.
- Language choices are infrequently made; vast majority of teams will already be using a set language that you will not have control over choosing (it could also be an unreleased internal language).
- Java (strongly typed language), JavaScript (untyped), Typescript (augments JavaScript with type checking).

### Language properties

- **Syntax** and **semantics** defines the form and meaning of programming languages.
- **Syntax** defines the **grammar (tokens)** and the **legal order** that these tokens can be used in valid programs.
- **EBNF** is often used to define the legal syntax of a language precisely.
- The **semantics** of the language **capture the actual meaning of the ordered tokens**.
- Some statements can be syntactically valid while being semantically meaningless.
  - if(foo === foo) will always be true and has **no semantic value**, while **syntactiaclly correct**.
- Developers frequently use **small patterns**, or **idioms**, that are common to language.
- Following **common idioms**, along with **code style**, and **code conventions** make it **easier** for people to **understand** and **read** your code.
- There is an **important distiction** to be made between **static representation** (source code) and the **dynamic representation** of a system (runtime state and behaviour).
- The distinction is important because it is **often not obvious from the source code how the code will execute at runtime** (ex: different code paths being invoked due to polymorphism).
  - Think of debugging; while you can pause execution on a single breakpoint and get a view of the program **at that instant in time**, the **true dynamic behaviour** of a program is an aggregation of ***all*** program states across ***all*** executions. (which makes understanding bug reports difficult).

### Language features

- Syntax is **not the most important differentiator** between languages.

- Every language designer makes **higher-level design decisions** that provide more **coarse-grained differences** between them and their syntax.

- **Interpreted** vs. **compiled**

  - An interpreted language executes the code by starting at the top of the code listing and executive successive lines. 
  - A complied language are first analyzed and transformed by a complier before they can be excuted.
    - It enables:
      - The code to be anaylzed for syntax problems before runtime.
      - Type checking (if the language is statically typed).
      - The emitted code to be optimized for runtime performance improvements.
      - The code to reference elements that have not yet been defined (as the whole code can be analyzed in multiple passes by the complier)
  - Java is **not** an interpreted language (we explicitly compile it with javac).
    - Also, we can reference fields and methods before they are declared.
  - JavaScript is **not** an interpreted langauge as well.
    - While JavaScript started as an interpreted language, all modern JavaScript use **Just-in-time (JIT)** compliation to transform the JavaScript code into bytecode which can then be evaluated.

- **Static** vs. **dynamic** **types**

  - In languages that uses static types, variables are **given types** and a complier checks that **assignments to** and **usages** of these variables **do not violate** the type declaration.


  - However, in languages that use dynamic types, values rather than variables have types.
    - Dynamically typed languages do not perform type checking which can cause problems at runtime.
    - TypeScript extends JavaScript by adding static type declarations that are checked by a compiler.
    - TypeScript uses type inference to figure out the types in your code from how they are used, rather than forcing you to explicitly define them.
    - TypeScript also gives you the ability to turn off type checking for specific variables with the *any* type. This tells the complier not to emit type errors for that variable so that you can change the type of a variable dynamically.

Examples for type declarations:

**Java**:

```java
int age; // age is declared to be an int

age = 10; // ok, 10 is an int

age = 100; // ok, 100 is an int

age = false; // !ok, false is not an int

age = '10'; // !ok, '10' is a string, not an int

```

**JavaScript**:

```javascript
var age; // age does not have a type
age = 10; // ok, 10 is a number, so age is now a number
age = 100; // ok, age is still a number
age = false; // ok, false is a boolean so age is now a boolean
age = '10'; // ok, '10' is a string so age is now a string
```

**TypeScript**:

```typescript
var age: number; // age is a number
age = 10; // ok, 10 is a number
age = 100; // ok, 100 is a number
age = false; // !ok, false is a boolean, not a number
age = '10'; // !ok, '10' is a string, not a number
```

```typescript
var age; // age does not have a type
age = 10; // ok, 10 is a number so age is now a number
// age has now been given the type number, this cannot be changed
age = 100; // ok, 100 is a number
age = false; // !ok, false is a boolean, not a number
age = '10'; // !ok, '10' is a string, not a number
```

```typescript
var age: any; // age can take any type
age = 10; // ok
age = 100; // ok
age = false; // ok
age = '10'; // ok
```