> **Core Idea:** A module should be responsible to one, and only one, **actor**.

- **The Common Misconception:** SRP does _not_ mean "a function should do only one thing." That is a low-level refactoring rule for functions, not an architectural principle.
    
- **Actor Defined:** An "actor" is the group—users, stakeholders, or business roles (e.g., CFO, COO, CTO)—that requests a specific change in the system.
    
- **Architectural Risk:** When a single module serves multiple actors, changes requested by one actor can break functionality required by another.
    
- **Example Violation:** An `Employee` class containing `calculatePay()` (for Accounting), `reportHours()` (for HR), and `save()` (for DBAs). A fix for HR's hours reporting could inadvertently alter accounting's pay logic.