- **Dependency Injection (DI):**
    
    - **Definition:** Passing an object's dependencies in from the outside (typically via constructor parameters) instead of creating them internally via `new`.
        
    - **Inversion of Control (IoC):** Handing off dependency management to the caller or a DI framework container.
        
- **Mocking:**
    
    - **Definition:** Creating lightweight, fake implementations of dependencies (ports/interfaces) to test code in isolation without calling real databases or external APIs.
        
    - **Common Test Doubles:**
        
        - **Stubs:** Provide canned responses for tests.
            
        - **Mocks:** Verify specific interactions (e.g., ensuring `sendEmail()` was called exactly once).
            
        - **Fakes:** Working lightweight implementations (e.g., an in-memory repository).
            
- **The Connection:** DI provides the hook required for testing. Without DI, replacing real network or database calls with test doubles during unit testing is nearly impossible.