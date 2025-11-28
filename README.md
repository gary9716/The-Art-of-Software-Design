# Decoupling Art

> The Art of Software Design through Dependency Management

A comprehensive guide to understanding and implementing proper dependency design in software architecture, with a focus on Unity game development.

## 📖 Overview

This repository explores the fundamental principles of software architecture through the lens of **dependency management**. The core philosophy is that the ultimate goal of software architecture is not to shatter everything into fragments, but to establish a **healthy, unidirectional, and stable power structure**.

## 🎯 Core Philosophy

Deciding "who depends on whom" is about clarifying:
- **Who is the Core Rule (Boss)** - The stable, unchanging business logic
- **Who is the Implementation Detail (Runner)** - The volatile, replaceable components

We use **Interfaces** as contracts to thoroughly separate:
- **What to do (Policy)** - Business rules and logic
- **How to do it (Mechanism)** - Implementation details

## 📚 Contents

### [Dependency.md](./Dependency.md) - The Complete Guide

A comprehensive guide covering:

1. **The Golden Rules of Dependency**
   - Depend on the "Stable", not the "Volatile"
   - Depend on "Abstractions", not "Concretions" (DIP & SoC)
   - Dependencies must be "Unidirectional"

2. **The Refined Onion Architecture**
   - Layer 1: Model (Core / Domain) - The Innermost Layer
   - Layer 2: System (Application Logic) - The Middle Layer
   - Layer 3: Adapters (View & Infrastructure) - The Outermost Layer

3. **Unity Implementation: MVC & Passive View**
   - Relationship definitions between Controller, View, and Model
   - Architecture flow diagrams
   - Practical code examples

4. **Practical Patterns & Tools**
   - Dependency Injection (DI) - Solving Structural Coupling
   - Event Strategy - Solving Logical Coupling

5. **Conclusion**
   - Key takeaways and principles

## 🏗️ Architecture Principles

### The Three Golden Rules

1. **Stability First**: Depend on stable core rules, not volatile implementations
2. **Abstraction Over Concretion**: Use interfaces to invert dependencies
3. **Unidirectional Flow**: Control flows down, notifications flow up

### The Onion Architecture

```
┌─────────────────────────────────────┐
│  Layer 3: Adapters (View & IO)     │ ← Outermost (Volatile)
├─────────────────────────────────────┤
│  Layer 2: System (Application)      │ ← Middle (Orchestration)
├─────────────────────────────────────┤
│  Layer 1: Model (Core / Domain)    │ ← Innermost (Stable)
└─────────────────────────────────────┘
```

**Key Concept:** Dependencies only point inwards. The core never depends on the edge.

## 🎮 Unity-Specific Patterns

This guide provides practical patterns for Unity development:

- **MVC & Passive View Pattern**
- **Dependency Injection** (Reflex, VContainer)
- **Event-Driven Architecture** (UniRx)
- **Separation of Concerns** between Logic, View, and Model

## 💡 Key Takeaways

> **Remember:** The Core must never depend on the Edge.

- We let the Controller depend on the View because Logic should dictate when screens appear or disappear
- We ensure the View does NOT depend on the Controller because UI should be replaceable by artists without breaking code
- We make both sides depend on Interfaces so that when hardware changes, the Game Logic remains untouched

## 📖 Reading Guide

1. Start with [Dependency.md](./Dependency.md) for the complete guide
2. Review the three golden rules and understand the philosophy
3. Study the Onion Architecture layers
4. Examine the Unity implementation examples
5. Apply the patterns to your own projects

## 🔗 Related Concepts

- **Dependency Inversion Principle (DIP)**
- **Separation of Concerns (SoC)**
- **Clean Architecture**
- **MVC Pattern**
- **Passive View Pattern**
- **Event-Driven Architecture**

## 📝 License

This repository contains educational content about software architecture principles. Feel free to use and share these concepts in your projects.

---

**The art of software design lies in controlling "Change".**

