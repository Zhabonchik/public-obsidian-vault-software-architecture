- **Monolith:**
    
    - A single application unit containing all domain modules and deployed as one process.
        
    - **Pros:** Simple deployment, easy cross-cutting concerns (logging, auth), straight-forward local debugging.
        
    - **Cons:** Tight coupling risk, scaling bottlenecks (must scale whole app, not just hot spots), deployment friction across large teams.
        
- **Microservices:**
    
    - A distributed system where features are broken into autonomous services structured around business domains (Bounded Contexts) that communicate over networks (HTTP/gRPC/Messaging).
        
    - **Pros:** Independent deployments, tech-stack flexibility, granular scaling per service.
        
    - **Cons:** High operational overhead, network latency, distributed transaction complexity, eventual consistency trade-offs.
        
- **Rule of Thumb:** Start with a well-structured **Modular Monolith**. Enforce clear internal domain boundaries first. Splitting messy monolithic code yields a distributed mess.