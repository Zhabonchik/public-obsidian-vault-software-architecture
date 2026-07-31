- **Core Premise:** A balanced testing strategy designed to optimize execution speed, maintenance cost, and system reliability.
    
- **Layers (Bottom to Top):**
    
    1. **Unit Tests (Foundation ~70–80%):**
        
        - Fast, deterministic tests focused on single functions, classes, or modules in complete isolation.
            
        - High coverage, cheap to write and maintain.
            
    2. **Integration Tests (Middle ~15–20%):**
        
        - Verify communication between components (e.g., ORM interacting with an actual database, API client talking to a mock server).
            
        - Slower and more expensive than unit tests.
            
    3. **End-to-End / UI Tests (Top ~5–10%):**
        
        - Validate critical complete user flows through the full system (UI or public API to database).
            
        - Slowest, highest maintenance cost, prone to flakiness.
            
- **Anti-Pattern:** The **Ice Cream Cone** (inverted pyramid), where most test coverage relies on fragile E2E tests, leading to long build pipelines and frequent false failures.