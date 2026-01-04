![Img](Src/Cover.webp)

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.GameFlow


# Flexy.GameFlow


Stop fighting menus, meta, gameplay, and scenes  
A hierarchical game state architecture for managing states and scenes  
Clean and testable from prototype to production


[Github](https://github.com/FlexyTools/Flexy.GameFlow)
<!-- | [Unity Forum](https://discussions.unity.com/t/a/1700923)
| [AssetStore](https://u3d.as/3LKx) -->  
[Start Guide](StartGuide.md)
| [How It Works & Use Cases](HowItWorks_UseCases.md)
| [Scripting Api](ScriptingApi/Readme.md)
| [Showcase(Template project)](../../GameTemplates/Barley-Breaks/Readme.md)

Production-proven architecture, refined in real projects since 2012  
Design your game as explicit, testable states — from Boot and Meta to Core gameplay


## When game flow starts working against you

As projects grow, game state logic becomes fragile and hard to reason about

- Dependencies spread across systems, even when using DI
- Adding new game states introduces hidden coupling and side effects
- Custom flow solutions break as requirements change
- Transition chains become complex and difficult to maintain
- Testing a single state requires running the entire game

Flexy.GameFlow addresses this by design:

- A single hierarchical state model for gameplay, meta, UI, and overlays
- Any state can be launched and tested instantly, in isolation
- States and transitions are awaitable, with explicit input and output data flow
- Each state owns its lifecycle and cleanup
- The same architecture scales from prototype to production


## Is this for you?

Flexy.GameFlow is a good fit if:
- Your project grows beyond a simple prototype
- You have multiple game states such as menus, meta, gameplay, or overlays
- Your game states need separate scenes or non-trivial scene navigation
- You care about clean architecture, testability, and long-term maintainability

This asset is likely not a good fit if:
- You want a visual-only solution without writing code
- Your game states and scenes are simple and unlikely to grow in complexity


## Why Flexy.GameFlow specifically?

- Designed by a developer who builds complete games, not just frameworks
- Used as a foundation for other Flexy.Tools systems and real projects
- Framework-agnostic by intent, with no forced UI system, scene structure, or networking stack
- Free Lite version to validate the architecture before committing


## Flexy Game.Flow vs Other Solutions

<details><summary> Is this just a classic FSM? </summary>

Classic FSMs work well for isolated systems like AI or animation  
They do not scale to managing the full game state hierarchy

They break down when:
- States are spread across scenes and managers
- Hierarchy or parallel state layers are required
- Transitions depend on context or async logic

<br></details>

<details><summary> Why not Scene Managers? </summary>

Scene managers treat scenes as the primary unit of control  
This works early, but breaks down as projects grow

Common problems:
- Game logic becomes tightly coupled to scene structure
- UI, gameplay, and meta are handled by separate systems
- Testing a single state requires loading the whole game

Flexy.GameFlow inverts this:
- Game states are first-class citizens
- Scenes are an implementation detail
- Gameplay states, overlays, and popups share one model

**You orchestrate game behavior — scenes follow**

<br></details>

<details><summary> Why not custom state management? </summary>

Custom solutions often:
- Start simple and degrade over time
- Become tightly coupled and hard to test
- Require full game boot to debug specific states

Flexy.GameFlow provides:
- A proven architecture with clear boundaries
- Full control via a public API
- Structure without rigidity

<br></details>


## Advanced Capabilities

- Hierarchical game state composition with nested and layered states
- Clear separation between state lifecycle, logic, and view
- Enter Play Mode from any scene with the correct state hierarchy from the first frame
- Game states can be developed and tested in isolation
- Scene loading and unloading driven by game states
- Support for multi-scene maps and non-trivial navigation


[Start Guide](StartGuide.md) | [How It Works & Use Cases](HowItWorks_UseCases.md) | [Scripting Api](ScriptingApi/Readme.md) | [Showcase(Template project)](../GameTemplates.md)


## Technical details

- Modern C# (C# 10)
- Designed to work with Domain Reload disabled


### Features

- Single `State` base class for all state types (gameplay, UI, substates)
- Extensible lifecycle via virtual Show/Hide and BackShow/ForwardHide methods
- Deterministic bootstrap that initializes the correct state hierarchy for any scene
- Early initialization allowing Play Mode entry from any scene or state before the first frame
- Explicit state cleanup via `Stage.CloseAndDestroy`
- Explicit input and output data passed between states
- Awaitable states and transitions with strongly defined results
- Cross-scene references without hard scene dependencies
- Game states can be instantiated and tested in isolation


### Core Architecture & Runtime

- Bootstrap prefab initializes the GameFlow runtime
- Central `ServiceGameFlow` API for controlling game states from code
- Explicit `GameStage` abstraction for major phases (Boot, Meta, Core)
- `FlowLibrary` for centralized registration and lookup of states
- Graph-based state model using `FlowGraph` and `FlowNode`
- Runtime tracking of active and current state nodes
- Explicit `TransitionOperation` for deterministic state transitions


### GameFlow Pro Features

- Extended control over Play Mode initialization
- Additional virtual Open/Close and Forward/Back lifecycle methods
- Support for substate layers (e.g. popup layer)
- Customizable UniTask-based transition logic
- Deterministic await points for logical and visual state changes
- Asynchronous preload of state views
- Split-screen support via separate `BigStage` instances



<br/>

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.GameFlow