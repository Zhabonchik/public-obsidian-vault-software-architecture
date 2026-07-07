
* **Critical Business Rules:** Rules that generate or save money for the business *even if they were performed manually* without a computer (e.g., a bank calculating loan interest).
* **Critical Business Data:** The exact data required for those critical business rules to function (e.g., loan balance, interest rate).

#### Entities (The Highest Level)
* **Definition:** An object that encapsulates **Critical Business Rules** and **Critical Business Data** together.
* **Core Concept:** An Entity *is the business itself*. It is pure domain logic.
* **Independence:** It knows absolutely nothing about the database, the UI, or the application frameworks. It is built for maximum stability and multiple reuse across different applications.

#### Use Cases (Application-Specific Level)
* **Definition:** Descriptions of automated system usage. They orchestrate the flow of data to and from the entities.
* **Core Concept:** Use Cases define *how* the automated system behaves (User Input ➡️ Actions ➡️ System Output).
* **Relative Level:** Use Cases are a **lower level** than Entities because Use Cases depend on Entities, but Entities have no knowledge of Use Cases.

#### Crossing the Boundary (Data Flow)
* **Request/Response Models:** Data entering or leaving a Use Case must use simple, isolated data structures (DTOs). 
* *Rule:* Never pass raw Entity objects across the boundary to the UI or Web layer, as this violates the isolation of your highest-level policies.