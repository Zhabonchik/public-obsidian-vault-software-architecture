
* **Software as Policy:** A computer program is a detailed description of policies that transform input data into output data.
    * Policies that change together at the same time/for the same reasons must be grouped together (same package).
    * Policies that change independently should be isolated from each other (different packages).
* **Defining "Level":** "Level" is defined as the *remoteness from input and output*.
    * **High-Level Policies:** The furthest away from I/O. They handle core business rules. They change less frequently and only for critical, foundational reasons.
    * **Low-Level Policies:** The closest to I/O. They handle formatting, delivery, and data inputs. They change frequently and for trivial reasons.
* **The Direction of Dependencies:** Source code dependencies must always point in the direction of higher-level policies. Low-level policies must depend on high-level ones, never vice-versa.

#### Presenters and Humble Objects
Architectural boundaries are hard to test because they look outward at volatile infrastructure (UI, Databases, Web). The **Humble Object Pattern** solves this by splitting a boundary's behavior into two distinct modules.

- **The Smart Module (Logic):** Contains all the testable logic. High-level policy, completely independent of external mechanisms.
- **The Humble Module (Mechanics):** Contains all the un-testable, framework-dependent glue code. Kept so dead-simple that it contains zero logic and requires no testing.
#### The UI Boundary Example
To keep the UI testable without running an actual browser or device emulator, the boundary is decoupled using a **Presenter** and a **View Model**.

```
[ Interactor ] ──> ( Output Boundary Interface )
                           ▲
                           │ (Implements)
                     [ Presenter ] ──> [ View Model ] ──> [ View (Humble) ]
```

1. **Interactor (Use Case):** Outputs raw application data.
2. **Presenter (Smart Module):** Implements the Interactor's output interface. It takes raw data and translates it entirely into user-ready primitives (e.g., formats dates, turns booleans into `"Enabled"`/`"Disabled"` strings).
3. **View Model (Simple Data):** A flat structure of plain strings, numbers, and flags. It holds data, but no behavior.
4. **View (Humble Module):** The actual UI framework component. It simply maps the `ViewModel` onto the screen. It is completely "humble" because it contains no business or formatting logic.
####  🌐 Universal Application

This pattern applies to _any_ boundary where an inner policy meets an outer detail:

- **Database Gateways:** Interactor uses a pure repository interface (Smart); the concrete Gateway handles the raw SQL/ORM mechanics (Humble).
- **Service Wrappers:** Application uses a generic communication boundary (Smart); the adapter deals with third-party SDK quirks (Humble).

### Partial boundaries

Full-fledged architectural boundaries are expensive to design, implement, and maintain (requiring reciprocal interfaces, DTO mapping, and separate deployment units). A good architect implements a **Partial Boundary** as a lightweight placeholder when a full boundary is too expensive today, but likely needed tomorrow.
##### 1. Skip the Last Step
- **How it works:** You do all the work of a full boundary—create reciprocal interfaces, isolate data structures—but you **don't** separate them into different binaries. You compile and deploy them together in the same monolithic component.
- **Compromise:** Saves deployment/versioning overhead, but risks developers accidentally cross-linking code over time.
##### 2. One-Dimensional Boundaries (Strategy Pattern)
- **How it works:** A simple Client-Interface-Service setup. Uses Dependency Inversion in one direction.
- **Compromise:** Protects the high-level client from the low-level service. However, because it lacks reciprocal interfaces, it is highly vulnerable to "backchannels" where low-level code accidentally takes dependencies on high-level data structures.
##### 3. Facades
- **How it works:** A single `Facade` class encapsulates a group of services. The client interacts only with the Facade.
- **Compromise:** Sacrifices Dependency Inversion completely. It creates an organizational boundary, but the client still transitively depends on all underlying services at compile-time.

> **The Architect's Warning:** Partial boundaries require massive developer discipline. Because the compiler isn't physically preventing boundary violations (via separate modules), these boundaries can degrade rapidly into spaghetti code if ignored.

🔑 **The Golden Rule of Interfaces:** Whichever module **defines** the interface owns the relationship. Any module that **implements** that interface automatically points its compile-time dependency arrow _toward_ the defining module.