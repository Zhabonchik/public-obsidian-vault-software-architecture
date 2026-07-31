- **Core Premise:** Isolate core business logic from external frameworks, databases, user interfaces, and third-party services.
    
- **Structural Layers:**
    
    - **Core Domain (Inside):** Pure business logic, domain models, and use cases. Has zero dependencies on external frameworks or databases.
        
    - **Ports (Boundaries):** Interfaces defining how the core communicates with the outside world.
        
        - **Driver (Primary) Ports:** Entry points to the application (e.g., Use Case interfaces invoked by API controllers).
            
        - **Driven (Secondary) Ports:** Exit points required by the core (e.g., Repository or Mailer interfaces).
            
    - **Adapters (Outside):** Concrete implementations of ports (e.g., PostgreSQL adapter, REST controller, CLI runner).
        
- **Key Takeaway:** Treat infrastructure as a plugin. Core business rules should function identically whether triggered by a web endpoint, a background worker, or a CLI command.