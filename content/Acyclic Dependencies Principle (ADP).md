> **Core Idea:** Allow no cycles in the component dependency graph.

- **Architectural Lens:** System build/dependency graphs must be a Directed Acyclic Graph (DAG).
    
- **The Cycle Problem:** If Component A depends on B, B depends on C, and C depends back on A, all three effectively merge into one giant monolithic component. You lose independent releases.
    
- **How to Break Cycles:**
    
    1. Apply the **Dependency Inversion Principle (DIP)**: Insert an interface inside Component A so Component C depends on the interface instead of A directly.
        
    2. Create a **New Component**: Move the shared classes that both C and A depend on into a separate 4th component.