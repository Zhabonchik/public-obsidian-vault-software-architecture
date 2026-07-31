> **Core Idea:** Do not force software components to depend on methods they do not use.

- **Architectural Lens:** ISP is primarily concerned with **source-code and build dependencies**.
    
- **The Problem:** If Class A imports an interface containing 10 methods, but only calls 1, Class A still depends on the types and dependencies of the remaining 9 methods.
    
- **Consequence:** A change to any of those 9 unused methods forces Class A to be recompiled, retested, and redeployed. ISP advocates splitting bloated interfaces into lean, client-specific role interfaces.