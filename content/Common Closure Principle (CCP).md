> **Core Idea:** Gather into the same component those classes that change for the same reasons and at the same times.

- **Architectural Lens:** CCP is the **Single Responsibility Principle (SRP) applied at the component level**.
    
- **Key Takeaway:** Minimize the blast radius of change. If a business requirement changes, you want that change to affect as few deployed components as possible. Classes tied to the same business policy should live in the same component.