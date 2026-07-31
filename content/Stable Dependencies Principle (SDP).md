> **Core Idea:** Depend in the direction of stability.

- **Architectural Lens:** A component should only depend on components that are _more stable_ than itself.
    
- **Defining Stability:** Stability is not about frequent code changes; it is about the **amount of work required to make a change**. A component with many incoming dependencies is _stable_ because modifying it breaks many callers.
    
- **Instability Metric ($I$):**
    
    $$I = \frac{C_{out}}{C_{in} + C_{out}}$$
    
    - $C_{in}$ (Fan-in): Incoming dependencies (classes outside this component depending on classes inside).
        
    - $C_{out}$ (Fan-out): Outgoing dependencies (classes inside depending on classes outside).
        
    - $I = 0$: Maximally stable (hard to change, widely depended upon).
        
    - $I = 1$: Maximally unstable (easy to change, depends on many external things).