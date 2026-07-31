> **Core Idea:** Subtypes must be substitutable for their base types without altering system behavior.

- **Architectural Lens:** Originally a mathematical definition for object subtyping (Barbara Liskov, 1988), Uncle Bob applies LSP to **interfaces, REST APIs, and microservices**.
    
- **Architectural Violation:** If a system interacts with a set of payment services, but one specific service requires a special `if/else` check or a unique payload structure, the architecture is contaminated with leaky abstractions.
    
- **Consequence:** Violating LSP forces complex conditional logic and extra deployment steps all the way up the architecture stack.