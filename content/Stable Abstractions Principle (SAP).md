> **Core Idea:** A component should be as abstract as it is stable.

- **Architectural Lens:** High-level business rules must sit in stable components ($I \approx 0$). To ensure stable components remain flexible and easy to extend, they must be composed primarily of **abstract classes and interfaces**.
    
- **Abstractness Metric ($A$):**
    
    $$A = \frac{N_a}{N_c}$$
    
    - $N_a$: Number of abstract classes/interfaces in the component.
        
    - $N_c$: Total number of classes in the component.
        
    - $A = 0$: Fully concrete component.
        
    - $A = 1$: Fully abstract component.