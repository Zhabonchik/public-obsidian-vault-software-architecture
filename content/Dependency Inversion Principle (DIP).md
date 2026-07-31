> **Core Idea:** High-level policies should not depend on low-level details. Both should depend on abstractions.

- **Architectural Lens:** DIP is the mechanism that draws the actual **architectural boundaries** in a application.
    
- **Volatile vs. Stable:** Stable abstractions (interfaces, abstract classes) change far less often than concrete implementations (database drivers, UI frameworks, third-party libraries).
    
- **The Rule of Thumb:**
    
    - Do not refer to volatile concrete classes in source code declarations.
        
    - Do not derive from volatile concrete classes.
        
    - Do not override concrete functions.