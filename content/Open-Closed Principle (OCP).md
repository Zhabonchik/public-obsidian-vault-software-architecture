> **Core Idea:** A software artifact should be open for extension, but closed for modification.

- **Architectural Lens:** OCP is the fundamental goal of system architecture. If adding a new feature requires modifying existing, working source code across multiple files, the architecture has failed.
    
- **How It Works:** Divide the system into components, and order their dependencies in a directional hierarchy.
    
- **Protection Direction:** Lower-level details (like UI, databases, and reporting components) must depend on higher-level business policy—never the other way around. Changing the UI or database should require zero changes to core business rules.