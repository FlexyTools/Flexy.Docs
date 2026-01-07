![Img](Src/Cover.webp)

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / [Flexy.UI](Readme.md) / Details

# Flexy.UI — Detailed Overview, Philosophy, and Boundaries

This page explains what Flexy.UI **is**, what it **is not**, where it **shines**, where it **does not**, and how it compares to common Unity UI approaches

It is intended to remove ambiguity before adoption

---

## What Flexy.UI Is

Flexy.UI is a **UI manager and orchestrator** for Unity

Its primary responsibility is to:
- Control **when** UI screens open and close
- Guarantee that UI always runs inside a **valid runtime context**
- Provide **ready-to-use building blocks** for fast UI development

Flexy.UI also provides:
- A Screen-based UI model
- ViewModel-style UI logic implemented as MonoBehaviours
- A ready-to-use View layer for Unity uGUI
- Visual setup through binders
- TestCases for fast UI testing
- UI navigation with history and transitions
- Seamless integration with Flexy.GameFlow and Flexy.AssetRefs

Flexy.UI is designed so users can **get results immediately**, without learning architecture or theory

---

## What Flexy.UI Is Not

Flexy.UI is **not**:
- A visual UI builder
- A no-code UI solution
- A replacement for Unity uGUI or UI Toolkit
- A design tool for UI artists
- A code generator
- A static or global UI system

Flexy.UI does not try to:
- Hide Unity concepts
- Remove the need for basic C# knowledge
- Replace UI frameworks
- Enforce a specific architectural dogma

If you want a tool where UI logic is created without writing any code, Flexy.UI is not a good fit

---

## Core Design Philosophy

Flexy.UI is built around the idea that **UI should be fast to create, fast to change, and safe to evolve**

The framework prioritizes:
- Iteration speed over theoretical purity
- Visual setup over hardcoded wiring
- Explicit code over implicit magic
- Scalability without rewrites

Architecture exists internally to **remove problems**, not to introduce concepts users must learn

---

## Speed and Iteration

Flexy.UI is optimized for **speed on every screen**, not just the first one

Typical workflows:
- Duplicate an existing Screen prefab
- Create a new Screen MonoBehaviour
- Adjust layout visually
- Bind properties using binders
- Open the screen from a button or code

There is:
- No registration step
- No enums to update
- No string identifiers
- No prefab path wiring
- No Resources folder requirements

Iteration remains fast throughout the project lifecycle

---

## Creating a New UI Screen

In most Unity projects, creating a new UI screen requires:
- Adding enum values
- Updating managers
- Registering prefabs
- Adding hardcoded paths
- Updating loading logic
- Refactoring when moving to Asset Bundles

In Flexy.UI:
- Create a new Screen MonoBehaviour
- Duplicate a Screen prefab
- That is enough

Loading works automatically through Flexy.AssetRefs  
Moving from Resources to Bundles requires no UI changes

---

## UI Logic and Code

Flexy.UI does **not** eliminate code

Code is used to:
- Express UI intent explicitly
- Pass parameters between screens
- Control navigation logic
- Bind UI state to data

For very simple UI:
- Ready-to-use scripts like ButtonClick_OpenWindow can be used

For more explicit control:
- Callable methods on Screen MonoBehaviours are recommended

This keeps UI behavior readable and intentional

---

## Visual Setup and Binders

Flexy.UI uses **visual binders** to connect UI elements to Screen logic

Binders:
- Are configured in the Inspector
- Work with standard uGUI components
- Reduce boilerplate code
- Keep UI logic declarative

UI designers can:
- Work on layout
- Add binders
- Test screens visually

Programmers can:
- Focus on Screen logic
- Avoid touching layout prefabs unnecessarily

---

## Runtime Safety and Execution Order

Flexy.UI guarantees that UI:
- Opens only inside a valid runtime environment
- Runs after all required systems are initialized
- Behaves predictably even in complex scenarios

This is especially important for:
- Networked games
- Pause screens
- Settings screens
- State transitions during gameplay

Because Flexy.UI is built on Flexy.GameFlow:
- UI respects game state
- UI navigation integrates with state transitions
- Edge cases like overlapping states are handled safely

Users do not need to understand GameFlow to benefit from this

---

## UI Testing and TestCases

Flexy.UI allows UI Screens to be:
- Opened directly
- Tested in isolation
- Verified under exact runtime conditions

TestCases:
- Represent specific UI scenarios
- Allow fast iteration
- Remove the need for mock setups

This dramatically reduces UI debugging time

---

## Advanced UI Transitions

Flexy.UI supports:
- Animated transitions between UI screens
- Loader screens
- Seamless transitions between game stages

Because it is built on GameFlow:
- Transitions can be arbitrarily complex
- UI can blend with gameplay states
- Cinematic flows similar to large commercial games are possible

Flexy.UI does not limit how complex transitions can be

---

## Scalability Across Team Sizes

### Solo Developers

Benefits:
- Fast iteration
- Less code
- No throwaway UI
- Good habits from the start

Flexy.UI does not slow down small projects

---

### Small Teams

Benefits:
- Clear separation of responsibilities
- UI designers and programmers can work independently
- Reduced merge conflicts
- Predictable UI behavior

---

### Large Studios

Benefits:
- Screen logic and View logic are separated
- UI designers can own screen behavior
- Programmers can own data and navigation
- Multiple UI systems can coexist
- Flexy.UI is instance-based, not static

Flexy.UI can orchestrate UI while delegating rendering to other systems if needed

---

## Framework and UI Technology Support

- ViewModel layer is UI-framework agnostic
- Unity uGUI has a ready-to-use View layer
- Other UI frameworks can be supported by implementing a View layer

UI Toolkit:
- Planned for the future
- Depends on Unity limitations
- Not promised in the near term

Flexy.UI does not block future UI technology choices

---

## Comparison With Common Approaches

### Ad-hoc MonoBehaviour UI

Problems:
- Tight coupling
- Hardcoded references
- Fragile execution order
- Difficult refactoring

Flexy.UI:
- Centralizes orchestration
- Removes wiring boilerplate
- Improves safety and iteration speed

---

### Home-Grown UI Managers

Problems:
- Reinvented poorly
- Hard to extend
- No history or navigation safety

Flexy.UI:
- Production-proven
- Handles navigation and history
- Scales naturally

---

### Heavy Architectural Frameworks

Problems:
- High learning curve
- Slow onboarding
- Overengineering

Flexy.UI:
- Architecture exists but is hidden
- No theory required
- Learn by doing

---

## Trust and Maturity

- Used in 10+ real projects
- Latest versions used in 7 active projects
- Evolved continuously since 2012
- Refined through real production, not theory

The Showcase:
- Is a real application
- Can be built and installed
- Serves as a learning tool and starting point

Flexy.UI is safe to try and safe to remove

---

## Known Limitations

Flexy.UI does not:
- Remove the need for UI design decisions
- Replace UI frameworks
- Automatically fix poor UI logic
- Eliminate the need for code entirely

Developers who:
- Hate visual setup
- Want everything hardcoded
- Expect no-code solutions

May not enjoy Flexy.UI

---

## Summary

Flexy.UI is designed to:
- Make UI creation faster
- Make UI iteration safer
- Remove unnecessary wiring
- Scale without rewrites
- Stay out of your way

It is intentionally:
- Visual
- Explicit
- Predictable
- Extensible

If your project values **speed now and stability later**, Flexy.UI is a strong fit


<br/>

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / [Flexy.UI](Readme.md) / Details
