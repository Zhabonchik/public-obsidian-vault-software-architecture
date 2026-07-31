---
tags: [moc, software-architecture, system-design]
---
S# 🏛️ Software Architecture Map of Content

> "The goal of software architecture is to minimize the human resources required to build and maintain the required system." — Robert C. Martin

This is the central hub for all concepts regarding how software is designed, structured, and scaled. It moves from the microscopic (lines of code) to the macroscopic (entire distributed systems).

---

## 🧱 1. Foundational Paradigms (The Rules of Code)
*How we constrain our code and manage basic control flow.*
* [[Structured Programming]] - Imposing discipline on direct transfer of control (No GOTO).
* [[Object-Oriented Programming]] - Imposing discipline on indirect transfer of control (Polymorphism).
* [[Functional Programming]] - Imposing discipline on variable assignment (Immutability).

## 📐 2. Class-Level Principles (SOLID)
*How we design individual classes and their immediate relationships.*
* [[Single Responsibility Principle (SRP)]] - A module should be responsible to one, and only one, actor.
* [[Open-Closed Principle (OCP)]] - Open for extension, closed for modification.
* [[Liskov Substitution Principle (LSP)]] - Subtypes must be mutually substitutable.
* [[Interface Segregation Principle (ISP)]] - Prevent classes from depending on things they don't need.
* [[Dependency Inversion Principle (DIP)]] - Depend in the direction of abstraction.

## 📦 3. Component & Module Design
*How we group classes together into packages/binaries and manage their dependencies.*
**Component Cohesion (What goes in):**
* [[Reuse-Release Equivalence Principle (REP)]]
* [[Common Closure Principle (CCP)]]
* [[Common Reuse Principle (CRP)]]

**Component Coupling (How they interact):**
* [[Acyclic Dependencies Principle (ADP)]]
* [[Stable Dependencies Principle (SDP)]]
* [[Stable Abstractions Principle (SAP)]]

## 🏰 4. System-Level Architecture & Boundaries
*The macro-blueprints. How the system protects its core business rules from external changes.*
* [[Architectural Boundaries]] - Drawing lines between policy and details.
* [[Entities vs Use Cases]] - Defining pure business logic.
* [[The Clean Architecture]] - The concentric circles dependency rule.
* [[Hexagonal Architecture]] - Ports and Adapters pattern.
* [[Microservices vs Monoliths]] - Deployment and scaling boundaries.

## ⚙️ 5. Infrastructure, Delivery, and "Details"
*The external tools that interact with our core system. (These should be kept at arm's length).*
* [[The Database is a Detail]] - Abstraction of persistence.
* [[The Web is a Detail]] - Abstraction of delivery mechanisms.
* [[Frameworks are Details]] - Why you shouldn't marry your framework.

## 🧪 6. Testing Strategy
*Testing is an architectural component, not just a QA phase.*
* [[Testing as a System Boundary]]
* [[The Test Pyramid]]
* [[Mocking and Dependency Injection]]

---
### 📚 Master Reference Library
*Notes specific to the authors, books, and courses that feed this MoC.*
* [[Book - Clean Architecture by Robert C. Martin]]