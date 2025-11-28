# The Art of Software Design

> The ultimate goal of software architecture is not to shatter everything into fragments, but to establish a healthy, unidirectional, and stable power structure.

This repository explores the fundamental principles that transform code from a collection of fragments into a well-architected system. At its core, **software design is the art of controlling change**—and mastering dependency relationships is the foundation of that art.

## 🎯 What is Software Design?

Software design is not about writing code that works—it's about creating systems that **evolve gracefully** under change. The difference between good and great software lies in how we answer one critical question:

> **"Who depends on whom?"**

This question determines:
- **Maintainability**: How easily can we modify or extend the system?
- **Testability**: Can we test components in isolation?
- **Flexibility**: Can we swap implementations without breaking the system?
- **Clarity**: Does the architecture reveal its intent?

## 📖 Core Philosophy

### The Power Structure

Every software system has a power structure. The art lies in establishing the right hierarchy:

- **The Core (Boss)**: Stable business rules, domain logic, and data models that define *what* the system does
- **The Edge (Runner)**: Volatile implementations, UI, hardware interfaces, and third-party integrations that define *how* it's done

**The Golden Rule**: The Core must never depend on the Edge.

### Separation of Concerns

We use **Interfaces** as neutral contracts to separate:

- **Policy (What)**: Business rules and domain logic—the "why" behind the system
- **Mechanism (How)**: Implementation details—the "what" that can change

This separation allows us to:
- Modify implementations without touching business logic
- Test business logic without external dependencies
- Replace entire subsystems (UI, hardware, services) without breaking the core

## 📚 Contents

### [Dependency.md](./Dependency.md) - The Complete Guide

A comprehensive exploration of dependency design as the foundation of software architecture:

#### 1. The Golden Rules of Dependency

Three fundamental principles that guide all architectural decisions:

- **Rule 1: Depend on the "Stable", not the "Volatile"**
  - Build on solid foundations (core rules, data models)
  - Avoid coupling to changing implementations (UI, hardware, third-party)

- **Rule 2: Depend on "Abstractions", not "Concretions"**
  - Use interfaces to invert dependencies (Dependency Inversion Principle)
  - Separate high-level policy from low-level mechanisms

- **Rule 3: Dependencies must be "Unidirectional"**
  - Control flows downward (upper layers command lower layers)
  - Notifications flow upward (lower layers communicate via events)

#### 2. The Refined Onion Architecture

A layered architecture where dependencies only point inwards:

```
┌─────────────────────────────────────┐
│  Layer 3: Adapters (View & IO)     │ ← Outermost (Volatile)
│  - UI Components                    │
│  - Hardware Interfaces              │
│  - External Services                │
├─────────────────────────────────────┤
│  Layer 2: System (Application)      │ ← Middle (Orchestration)
│  - Game Managers                    │
│  - Controllers                      │
│  - Application Logic                │
├─────────────────────────────────────┤
│  Layer 1: Model (Core / Domain)    │ ← Innermost (Stable)
│  - Data Models                      │
│  - Business Rules                   │
│  - Domain Logic                     │
└─────────────────────────────────────┘
```

**Key Concept:** Dependencies only point inwards. The core never knows about the edge.

#### 3. Unity Implementation: MVC & Passive View

Practical patterns for Unity game development:

- **Passive View Pattern**: Views are "dumb" displays that don't know about controllers
- **Event-Driven Communication**: Views emit events; controllers subscribe
- **Unidirectional Data Flow**: Models change → Views update automatically

#### 4. Practical Patterns & Tools

- **Dependency Injection (DI)**: Solving structural coupling
- **Event Strategy**: Solving logical coupling
- **When to use Member Events vs Global Event Bus**

### [AI-Facilitated-Programming.md](./AI-Facilitated-Programming.md) - The New Art ⚠️ WIP

> **Work In Progress** - This document is currently under development.

A guide to maintaining architectural integrity when working with AI coding assistants:

#### 1. The New Golden Rules of AI-Assisted Development

- **Design First, Generate Second**: You define architecture; AI implements within your boundaries
- **Communicate Architecture, Not Just Requirements**: AI needs context about design decisions
- **Maintain Architectural Boundaries**: AI-generated code must respect dependency rules

#### 2. The AI-Human Collaboration Model

Understanding the division of labor between human architects and AI implementers, and how to collaborate effectively.

#### 3. Prompting for Architecture

Effective techniques for communicating architectural requirements to AI:
- Reference existing architecture
- Enforce dependency rules
- Apply design patterns consistently

#### 4. Maintaining Architectural Integrity

- Code review checklists for AI-generated code
- Common anti-patterns and how to avoid them
- Validation techniques

#### 5. AI as an Architectural Partner

Leveraging AI for interface design, pattern application, and refactoring while maintaining architectural principles.

## 🏗️ Architecture Principles

### The Three Pillars

1. **Stability First**
   - Identify what changes rarely (core rules) vs. what changes often (implementations)
   - Build dependencies toward stability

2. **Abstraction Over Concretion**
   - Define contracts (interfaces) that both high and low levels depend on
   - Invert the traditional dependency direction

3. **Unidirectional Flow**
   - Control: Upper layers command lower layers
   - Notification: Lower layers inform via events, not direct references

### The Onion Architecture

The Onion Architecture (also known as Hexagonal or Ports & Adapters) organizes code into concentric layers:

- **Inner Layers**: Core business logic, independent of external concerns
- **Outer Layers**: Adapters that translate between the core and the outside world
- **Dependency Rule**: All dependencies point inward toward the core

This structure ensures that:
- Business logic remains pure and testable
- External concerns (UI, database, APIs) are replaceable
- The system can evolve without breaking the core

## 🎮 Unity-Specific Patterns

This guide provides battle-tested patterns for Unity game development:

### MVC & Passive View

- **Model**: Pure C# data structures and business rules
- **View**: Unity components that display data and emit events
- **Controller**: Orchestrates between Model and View

### Dependency Injection

- Use frameworks like **Reflex** or **VContainer**
- Avoid race conditions with method injection
- Ensure dependencies are resolved before logic runs

### Event-Driven Architecture

- **Member Events**: For tightly-coupled, high-cohesion components
- **Global Event Bus**: For cross-system communication where sender/receiver are unknown

## 💡 Key Insights

> **The art of software design lies in controlling "Change".**

### Why Controller Depends on View

We let the Controller depend on the View because **Logic should dictate when screens appear or disappear**. The controller orchestrates the user experience.

### Why View Does NOT Depend on Controller

We ensure the View does NOT depend on the Controller because **UI should be replaceable by artists** or reusable in different contexts without breaking code. Views are "dumb" displays.

### Why Both Depend on Interfaces

We make both sides depend on Interfaces so that **when hardware changes** (Keyboard → Serial Port → VR Controller), the Game Logic remains untouched. The core is protected from volatility.

### The Ultimate Principle

> **Remember: The Core must never depend on the Edge.**

## 📖 How to Use This Repository

1. **Start Here**: Read [Dependency.md](./Dependency.md) for the complete guide on dependency design
2. **Understand the Philosophy**: Grasp why dependency direction matters
3. **Study the Patterns**: Learn the Onion Architecture and MVC patterns
4. **See It in Action**: Examine the Unity implementation examples
5. **Work with AI**: Read [AI-Facilitated-Programming.md](./AI-Facilitated-Programming.md) to learn how to maintain architectural integrity when using AI coding assistants
6. **Apply to Your Projects**: Use these principles to structure your own code

## 🔗 Related Concepts

This guide touches on several important software design principles:

- **Dependency Inversion Principle (DIP)**: High-level modules should not depend on low-level modules
- **Separation of Concerns (SoC)**: Each component should have a single, well-defined responsibility
- **Clean Architecture**: Organizing code into layers with clear boundaries
- **MVC Pattern**: Separating Model, View, and Controller concerns
- **Passive View Pattern**: Making views unaware of controllers
- **Event-Driven Architecture**: Decoupling components through events
- **Onion Architecture**: Layered architecture with inward dependencies

## 🎓 Learning Path

1. **Beginner**: Understand why dependencies matter and the three golden rules
2. **Intermediate**: Learn the Onion Architecture and how to structure layers
3. **Advanced**: Master the Passive View pattern and event-driven design
4. **Expert**: Apply these principles to create maintainable, testable systems

## 📝 About This Repository

This repository contains educational content about software architecture principles, with a focus on dependency management as the foundation of good design. The concepts apply broadly, but examples are tailored for Unity game development.

Feel free to use and share these concepts in your projects. The goal is to help developers create better software through better architecture.

---

**The art of software design lies in controlling "Change".**

*Master the dependencies, master the design.*
