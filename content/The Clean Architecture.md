
* **The Core Principle of Screaming architecture:** The architecture of a software system should loudly proclaim its *intent* and *business domain*, not the tools or frameworks used to build it.
* **Self-Descriptive Structure:** Looking at the top-level packages and classes should make it instantly clear what the application *does* (e.g., a healthcare app, an e-commerce platform) rather than what tech stack it uses.
* **Frameworks as Details:** Architecture must remain platform- and instrument-agnostic. Frameworks, databases, and web servers are merely delivery mechanisms; they are options to be deferred, not the foundation of the system.
* **The Benefit:** Unit tests can be run without the web server, database, or framework being active, making testing incredibly fast and the core business logic highly maintainable.

#### The Core Concentric Circles

The application is structured into concentric layers, moving from the most abstract/stable (center) to the most concrete/volatile (edge).

1. **Entities (Innermost):** Enterprise-wide business rules. Encapsulates the most general and high-level rules. Least likely to change when something external changes.
    
2. **Use Cases:** Application-specific business rules. Orchestrates the flow of data to and from entities.
    
3. **Interface Adapters:** Translates data from the format most convenient for use cases and entities, to the format most convenient for external agencies (e.g., Presenters, Controllers, Gateways/Repositories).
    
4. **Frameworks & Drivers (Outermost):** The "details"—Web, Database, UI, Devices. Generally consists of glue code that connects to the inner circles.

#### The Dependency Rule

> Source code dependencies must point **only inward**, toward higher-level policies.

- Nothing in an inner circle can know anything at all about something in an outer circle (functions, classes, variables, or data formats).
    
- **Crossing Boundaries:** When the control flow needs to go from an inner circle to an outer circle (e.g., a Use Case needs to call the Database), use the **Dependency Inversion Principle (DIP)**. The Use Case defines an interface, and the outer layer implements it.
    
- **Data Across Boundaries:** Data passed across boundaries must be in simple data structures (Plain Old Java/JavaScript/C# Objects, DTOs, or simple maps). _Never_ pass raw database rows or Entity objects across a boundary; doing so forces an inner layer to know about an outer layer's data format.

![[concentric-layers-and-the-dependency-rule.png]]

Clean architecture should not depend on hardware. Otherwise it will turn from Software into micro services that will be strictly bound to a particular hardware, which leads to problems with support and reuse.