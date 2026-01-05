![Img](Src/Cover.webp)

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.GameFlow


# Flexy.GameFlow


Stop fighting scene transitions  
A production-proven game state architecture for Unity  
Manage menus, gameplay, and scenes as explicit, testable states — from prototype to shipped game


[Github](https://github.com/FlexyTools/Flexy.GameFlow)
<!-- | [Unity Forum](https://discussions.unity.com/t/a/1700923)
| [AssetStore](https://u3d.as/3LKx) -->  
[Start Guide](StartGuide.md)
| [How It Works & Use Cases](HowItWorks_UseCases.md)
| [Scripting Api](ScriptingApi/Readme.md)
| [Showcase(Template project)](../../GameTemplates/Barley-Breaks/Readme.md)


Flexy.GameFlow replaces fragile menu, gameplay, and scene transition code with explicit, testable game states.
Production-proven architecture, refined in real projects since 2012  


## When game state architecture starts working against you

As projects grow, game state logic becomes fragile and hard to reason about

- Adding new menu, scene or gameplay state introduces hidden coupling and side effects
- Scene-driven flows break as requirements change
- Async transitions turn into complex callback chains
- Dependencies spread across MonoBehaviours, even when using DI
- Testing a single state requires running the entire game

Flexy.GameFlow addresses this by design:

- One hierarchical state model for boot, menus, and gameplay states
- Any state can be launched and tested directly, without running entire game from boot
- Enter Play Mode from any scene with the correct state hierarchy from the first frame
- Game states can be developed and tested in isolation
- Scene loading and unloading driven by game states
- States and transitions are awaitable, with explicit input/output
- Each state owns its lifecycle and cleanup
- Support for multi-scene maps and non-trivial navigation
- Scales cleanly from prototype to production 


## Is this for you?

Flexy.GameFlow is a good fit if:
- Your project grows beyond a simple prototype
- You have multiple game states such as menus, gameplay states, or overlays
- Scene management is no longer trivial
- You care about clean architecture, testability, and long-term maintainability

**Flexy.GameFlow is an architectural foundation and is intended to be adopted early in a project**

This asset is likely not a good fit if:
- You want a visual-only, no-code solution
- Your game flow is simple and unlikely to grow


## Why not FSMs, Scene Managers?

- **Classic FSMs** do not scale to full game state hierarchies with async transitions
- **Scene managers** couple logic to scenes and make state testing difficult

**Flexy.GameFlow** treats **game states as first-class**, with hierarchy, isolation, and deterministic async transitions


## Why Flexy.GameFlow specifically?

- Free Lite version to validate the architecture before committing
- Designed and used by a developer shipping full games — not just demo frameworks
- Used as a foundation in multiple shipped games and long-term production projects
- including large-scale projects under NDA
- No forced UI system, scene structure, or networking stack


[Start Guide](StartGuide.md) | [How It Works & Use Cases](HowItWorks_UseCases.md) | [Scripting Api](ScriptingApi/Readme.md) | [Showcase(Template project)](../GameTemplates.md)


## Technical details

### Compatibility

- Modern C# (C# 10)
- Designed to work with Domain Reload disabled
- Tested from Unity 2022.3 and up to Unity 6.3
- Depend on Flexy.Core and Flexy.AssetRefs
- Render pipeline agnostic
- Platform agnostic (shipped on Windows, macOS, Linux, Android, iOS)


### Capabilities

- Single `State` base class for all state types (gameplay, UI, substates)
- Extensible lifecycle via virtual Show/Hide and BackShow/ForwardHide methods
- Deterministic bootstrap that initializes the correct state hierarchy for any scene
- Early initialization allowing Play Mode entry from any scene or state before the first frame
- Explicit state cleanup via `Stage.CloseAndDestroy`
- Explicit input and output data passed between states
- Awaitable states and transitions with strongly defined results
- Cross-scene references without hard scene dependencies
- Game states can be instantiated and tested in isolation
- Bootstrap prefab initializes the GameFlow runtime
- Central `ServiceGameFlow` API for controlling game states from code
- Explicit `GameStage` abstraction for major phases (Boot, Meta, Core)
- `FlowLibrary` for centralized registration and lookup of states
- Graph-based state model using `FlowGraph` and `FlowNode`
- Runtime tracking of active and current state nodes
- Explicit `TransitionOperation` for deterministic state transitions


### Additional GameFlow Pro Capabilities

- Extended control over Play Mode initialization
- Additional virtual Open/Close and Forward/Back lifecycle methods
- Support for substate layers (e.g. popup layer)
- Customizable UniTask-based transition logic
- Deterministic await points for logical and visual state changes
- Asynchronous preload of state views
- Split-screen support


<br/>

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.GameFlow