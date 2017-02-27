# REST

### Intro

- **REST** is an architectural style heavily used in web-based systems for providing services between different systems (and interfaces).
- **REST** defines a mean of connecting systems together that focuses on their interfaces rather than their implementations using self-descriptive messages. 
- In this way, **REST** provides a *language* to define a specific kind of APIs for communicating across a network.
- **REST** services are transported over the network using **HTTP protocol**.

### Verbs

- **REST** describes how HTTP verbs should be used when communicating with **REST** services. **REST** services respond with payloads (typically JSON or XML) and an integer-based response code. Each **REST** requrest uses only one verb and recieves only one response.
  - ```GET```: Used to read a resource. 
    - GET requests should **never** modify data on a server, meaning that calling them repeatedly should have **no visible effects** on the server. 
    - GET requests can have a body but this is not idiomatic; requested resources are defined by the URI alone. 
    - Common response codes are **200** (ok) and **404** (not found).
  - ```PUT```: Used to update a resouce at a known URI.
    - PUT can also be used to **create** a resource if the client is allowed to define a new URI that **does** **not already exist**.
    - Reponse bodies are not typically returned for these requests. 
    - PUT **modifies** server resources but in the same way for every request and can be considered idempotent.
    - Common response codes are **200** (ok), **204** (no content), **404** (not found).
  - ```POST```: Used to create a new resource. 
    - The response body should contain a URI to the newly-created resource.
    - POST modifies server resources and is not idempotent.
    - Common response codes are **201** (created), **404** (not found), **409** (conflict).
  - ```PATCH```: Used to modify (not completely replace or delete) a resource.
    - **Not** idempotent
    - This is the **least-frequently** used verb.
    - Common response codes are **200** (ok), **204** (no content), **404** (not found).

### Statelessness

- **REST** services are often viewed as highly scaleable. 

  - The main reason for this is that there is an expectation that the client maintains state instead of server.
  - This means that a client can interact with several different servers for a single set of requests.
  - For example, if a client is trying to undertake a complex multi-step operation, it is the **client's reponsibility** to keep track of where they are, **not** the server's responsibility.
  - Servers are responsible for **sending back detailed information** about the **resources they are returning** so that clients have the ability to **make further requests of server** with the correct URIs.

### Design goals

- There are several orthogonal ideas to keep in mind when designing **REST** APIs
  - API must provide a **valuable** service.
  - APIs should also be **sufficiently flexible** to work in a wide variety of circumstances.
  - **Effectively measing your APIs** is also important for undersanding how your customers are using your system.
  - **Effective API documentation** is key for helping developers understand how to use any API.