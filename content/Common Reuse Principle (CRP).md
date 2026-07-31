> **Core Idea:** Don't force users of a component to depend on things they don't need.

- **Architectural Lens:** CRP is the **Interface Segregation Principle (ISP) applied at the component level**.
    
- **Key Takeaway:** Classes that are reused together should be packaged together. If Component A uses Component B, A should ideally use _all_ classes in B, not just one. Otherwise, changes to irrelevant classes in B will force unnecessary re-compilations and re-deployments of A.