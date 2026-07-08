
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

### 🌐 Universal Application

This pattern applies to _any_ boundary where an inner policy meets an outer detail:

- **Database Gateways:** Interactor uses a pure repository interface (Smart); the concrete Gateway handles the raw SQL/ORM mechanics (Humble).
- **Service Wrappers:** Application uses a generic communication boundary (Smart); the adapter deals with third-party SDK quirks (Humble).