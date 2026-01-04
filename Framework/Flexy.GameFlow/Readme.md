![Img](Src/Cover.webp)

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.GameFlow


# Flexy.GameFlow

Stop fighting your game flow  
Universal hierarchical state system for managing game states, scenes, and transitions  
clean, testable, and scalable from prototype to production
  

[Github](https://github.com/FlexyTools/Flexy.GameFlow)
<!-- | [Unity Forum](https://discussions.unity.com/t/a/1700923)
| [AssetStore](https://u3d.as/3LKx) -->  
[Start Guide](StartGuide.md)
| [How It Works & Use Cases](HowItWorks_UseCases.md)
| [Scripting Api](ScriptingApi/Readme.md)
| [Showcase(Template project)](../../GameTemplates/Barley-Breaks/Readme.md)

Production-proven architecture, used and refined in real projects since 2012  
Start small: install Lite, launch a state from any scene, and feel the difference in minutes — not days

Design your game as explicit, testable states — from Boot and Meta to Core gameplay  
So you can change and extend game flow safely, even late in development
  

## When game flow starts working against you

**Architecture**
- Game flow logic becomes messy and fragile as the project grows
- Everything starts depending on everything, even when using DI
- Adding a new game state creates dependency hell and unexpected side effects

**Scalability**
- Adding new game states becomes harder as the project grows
- Custom flow solutions break when requirements change
- Complex transition sequences are hard to build and reason about

**Development workflow**
- Testing a specific state requires running the whole game
- Passing data between states or scenes becomes cumbersome
- Debugging game states and transitions is painful


## How Flexy.GameFlow solves this

- **One State model for everything**: Gameplay, Meta flow, UI, cutscenes, and overlays are all game states
- **Launch and test any game state instantly**: Game Flow initializes the correct state hierarchy before the first frame 
- **Awaitable states and transitions**: Treat game flow like async code and await results cleanly
- **Explicit data flow between states**: Pass data in and out without singletons or hidden dependencies
- **Strong state isolation by design**: States own their lifecycle and cleanup
- **Architecture that scales with complexity**: Same model works from prototype to production
- **Framework-agnostic by intent**: No forced UI system, scene structure, or networking stack


## Preface

Any game is a set of game states that transition into each other.  
Big stages like Boot, Lobby (Metagame), and Battle (Coregame),  
and their states like main menu, settings, loading, play, pause, cutscene, win/lose screens

Hierarchical game state management is a fundamental part of every game  
Flexy.GameFlow is a **game state manager**, not a UI manager

Most states require some form of UI for player interaction  
How this UI is implemented is the developer’s responsibility

Flexy.GameFlow is intentionally agnostic to rendering, UI frameworks, and networking solutions  
It supports singleplayer, multiplayer, coop, and split-screen projects without structural changes


## Advanced Capabilities

### Architecture

- Hierarchical game state composition with nested and layered states
- Clear separation between state lifecycle, logic, and view
- Dedicated GameContext per major game state
- Transition model suitable for singleplayer and multiplayer


### Workflow

- Enter Play Mode from any scene with correct state hierarchy from #frame 0
- Works with Domain Reload disabled
- Close & Destroy with correct cleanup is by design
- Game states can be tested in isolation (TDD-friendly)


### Scene & Navigation

- State-driven scene loading and unloading
- CrossSceneRef for portals, transitions, and similar cases
- Support for multi-scene maps with portals
- No manual scene management in Build Settings (thanks to AssetRefs.Pipelines)


## Who this is for

Flexy.GameFlow is designed for:
- Unity developers and studios, from solo developers to large teams
- Games that grow over time, from simple prototypes to complex projects
- Games with multiple scenes, modes, or non-trivial UI flow
- Developers who care about clean architecture, testability, and long-term maintainability


## Who this is not for

This asset may not be a good fit if:
- You want a visual-only tool without writing code
- Your game flow is simple and will not grow in complexity


## Flexy Game.Flow vs Other Solutions 

<details><summary> Is this just a classic FSM? </summary>

Classic FSMs work well for isolated systems like AI or animation,
but they do not scale to managing the entire game flow

They break down when:
- Game flow is spread across many scenes and managers
- States need hierarchy and parallel layers
- Transitions depend on context or async logic

<br></details>

<details><summary> Why Not Scene Managers? </summary>

Scene managers focus on scenes as the primary unit of control
This works early — but breaks down as projects grow

Typical scene-centric problems:
- Game logic becomes tightly coupled to scene structure
- UI, gameplay, and meta flow are handled by separate systems
- Testing a single flow requires loading the whole game
- Late changes introduce fragile dependencies and regressions

Flexy.GameFlow takes the opposite approach
- Game States are first-class citizens
- Scenes are an implementation detail, not the driver of logic
- Gameplay states, overlays, and popups use the same state model
- Flow is explicit, awaitable, and testable in isolation

**You do not manage scenes**  
**You orchestrate game behavior — scenes simply follow**

<br></details>

<details><summary> Why not custom state management? </summary>

Custom solutions usually:
- Start simple and rot over time
- Become tightly coupled to scene structure
- Are hard to test in isolation
- Require full game boot to debug specific flows

Flexy.GameFlow gives you:
- A proven architecture without locking you into rigid patterns
- Full control via public API
- The freedom to extend, override, or replace parts as your project evolves
- You get structure without rigidity.

<br></details>

### Why Flexy.GameFlow specifically?

- Designed by a developer who builds full games, not just frameworks
- Used as a foundation for other Flexy.Tools systems
- Free Lite version to validate the approach before committing


[Start Guide](StartGuide.md) | [How It Works & Use Cases](HowItWorks_UseCases.md) | [Scripting Api](ScriptingApi/Readme.md) | [Showcase(Template project)](../GameTemplates.md)


## Technical details

- C# 10
- Native C# nullability annotations
- Domain Reload–disabled friendly


### Features

- Universal: single `State` base class for all state types (gameplay, UI, substates)
- Extensible: virtual Show/Hide and BackShow/ForwardHide methods to override
- Robust bootstrap: correct state hierarchy initializes for any scene
- Early initialization: play any scene or state directly with automatic GameFlow setup before the first frame
- Easy cleanup: explicit `Stage.CloseAndDestroy` flow with proper cleanup of states, resources, and scenes
- Simple data exchange: pass data into a state and receive results back
- Awaitable results: await state results (e.g. popup answers, gameplay outcomes)
- TDD-friendly: start from any scene, state, or state test case
- Network-ready: tested in networked game projects


### Core Architecture & Runtime

- GameFlow bootstrap prefab/script to initialize the entire flow system
- Central `ServiceGameFlow` entry point for controlling game flow from code
- Explicit `GameStage` abstraction for major phases (Boot, Meta, Core)
- `FlowLibrary` for centralized registration and lookup of all game states
- Graph-based game flow model via `FlowGraph` and `FlowNode`
- Runtime tracking of current and active state nodes
- Explicit `TransitionOperation` struct for safe and predictable transitions
- `Opener` interface to decouple state creation from activation logic


### GameFlow Pro Features

- Extended control over Play Mode initialization
- Additional virtual Open/Close and Forward/Back lifecycle methods
- Layered substates support (e.g. popup layers)
- Fully customizable UniTask-based transition logic
- Precise control over logical events before any view changes
- Async preload of state views to avoid load spikes
- Split-screen support with a separate `BigStage` per screen



<br/>

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.GameFlow