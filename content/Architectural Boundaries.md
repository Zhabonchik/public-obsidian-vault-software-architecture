
* **Software as Policy:** A computer program is a detailed description of policies that transform input data into output data.
    * Policies that change together at the same time/for the same reasons must be grouped together (same package).
    * Policies that change independently should be isolated from each other (different packages).
* **Defining "Level":** "Level" is defined as the *remoteness from input and output*.
    * **High-Level Policies:** The furthest away from I/O. They handle core business rules. They change less frequently and only for critical, foundational reasons.
    * **Low-Level Policies:** The closest to I/O. They handle formatting, delivery, and data inputs. They change frequently and for trivial reasons.
* **The Direction of Dependencies:** Source code dependencies must always point in the direction of higher-level policies. Low-level policies must depend on high-level ones, never vice-versa.