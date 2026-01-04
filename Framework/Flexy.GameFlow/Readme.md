![Img](Src/Cover.webp)

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.GameFlow


# Flexy.GameFlow


Stop fighting menus, meta, gameplay, and scenes  
A hierarchical game state architecture for managing game states and scenes 
clean and testable from prototype to production

[Github](https://github.com/FlexyTools/Flexy.GameFlow)
<!-- | [Unity Forum](https://discussions.unity.com/t/a/1700923)
| [AssetStore](https://u3d.as/3LKx) -->  
[Start Guide](StartGuide.md)
| [How It Works & Use Cases](HowItWorks_UseCases.md)
| [Scripting Api](ScriptingApi/Readme.md)
| [Showcase(Template project)](../../GameTemplates/Barley-Breaks/Readme.md)

Production-proven architecture, used and refined in real projects since 2012  
Start small: install Lite, launch a state from any scene, and validate the approach in minutes

Design your game as explicit, testable states — from Boot and Meta to Core gameplay  
Change and extend your game safely, even late in development


## When game flow starts working against you

**Architecture**
- Game flow logic becomes fragile as the project grows
- Dependencies spread across systems, even when using DI
- Adding a new game state introduces hidden coupling and side effects

**Scalability**
- Adding new game states becomes harder as the project grows
- Custom flow solutions break when requirements change
- Complex transition chains become hard to build and reason about

**Development workflow**
- Testing a single state requires running the entire game
- Passing data between states or scenes becomes noisy and error-prone
- Debugging game states and transitions slows development


## How Flexy.GameFlow solves this

- **One state model for everything**: gameplay, meta, UI, cutscenes, and overlays are all game states
- **Launch and test any state instantly**: the correct state hierarchy is initialized before the first frame
- **Awaitable states and transitions**: treat game states like async code and await results cleanly
- **Explicit data flow between states**: pass data in and out without singletons or hidden dependencies
- **Strong state isolation by design**: each state owns its lifecycle and cleanup
- **Architecture that scales with complexity**: the same model works from prototype to production
- **Framework-agnostic by intent**: no forced UI system, scene structure, or networking stack


## Who this is for

Flexy.GameFlow is designed for:
- Unity developers and studios, from solo developers to large teams
- Projects that grow over time, from small prototypes to complex productions
- Games with multiple scenes, modes, menus, or non-trivial UI flow
- Developers who value clean architecture, testability, and long-term maintainability


## Who this is not for

This asset may not be a good fit if:
- You are looking for a visual-only solution without writing code
- Your game states are simple and unlikely to grow in complexity


## Why Flexy.GameFlow specifically?

- Designed by a developer who builds complete games, not just frameworks
- Used as a foundation for other Flexy.Tools systems and real projects
- Free Lite version to validate the architecture before committing


## Flexy Game.Flow vs Other Solutions

<details><summary> Is this just a classic FSM? </summary>

Classic FSMs work well for isolated systems like AI or animation  
They do not scale to managing the entire game state space of a project

They break down when:
- Game states are spread across scenes and managers
- Hierarchy and parallel state layers are required
- Transitions depend on context or async logic

<br></details>

<details><summary> Why not Scene Managers? </summary>

Scene managers treat scenes as the primary unit of control  
This works early, but breaks down as projects grow

Typical scene-centric problems:
- Game logic becomes tightly coupled to scene structure
- UI, gameplay, and meta are handled by separate systems
- Testing a single state requires loading the whole game
- Late changes introduce fragile dependencies

Flexy.GameFlow takes the opposite approach:
- Game states are first-class citizens
- Scenes are an implementation detail, not the driver of logic
- Gameplay states, overlays, and popups use the same model
- Behavior is explicit, awaitable, and testable in isolation

**You do not manage scenes**  
**You orchestrate game behavior — scenes simply follow**

<br></details>

<details><summary> Why not custom state management? </summary>

Custom solutions usually:
- Start simple and rot over time
- Become tightly coupled to scene structure
- Are hard to test in isolation
- Require full game boot to debug specific states

Flexy.GameFlow gives you:
- A proven architecture without rigid patterns
- Full control via a public API
- Freedom to extend, override, or replace parts as the project evolves
- Structure without rigidity

<br></details>


## Advanced Capabilities

### Architecture

- Hierarchical game state composition with nested and layered states
- Clear separation between state lifecycle, logic, and view
- Dedicated GameContext per major game state
- Transition model suitable for singleplayer and multiplayer projects


### Workflow

- Enter Play Mode from any scene with correct state hierarchy from the first frame
- Compatible with Domain Reload disabled
- Close & Destroy ensures correct cleanup by design
- Game states can be developed and tested in isolation (TDD-friendly)


### Scene & Navigation

- Scene loading and unloading driven by game states
- CrossSceneRef for portals, transitions, and similar cases
- Support for multi-scene maps with portals
- No manual scene management in Build Settings (thanks to AssetRefs.Pipelines)

## Preface

Any game is a set of game states that transition into each other  
Major stages like Boot, Lobby (Metagame), and Battle (Coregame),  
with states such as main menu, settings, loading, play, pause, cutscene, and win or lose screens

Hierarchical game state management is a fundamental part of every game  
Flexy.GameFlow is a **game state manager**, not a UI manager

Most states require some form of UI for player interaction  
How that UI is implemented remains the developer’s responsibility

Flexy.GameFlow is intentionally agnostic to rendering, UI frameworks, and networking solutions  
It supports singleplayer, multiplayer, coop, and split-screen projects without structural changes


[Start Guide](StartGuide.md) | [How It Works & Use Cases](HowItWorks_UseCases.md) | [Scripting Api](ScriptingApi/Readme.md) | [Showcase(Template project)](../GameTemplates.md)


## Technical details

- C# 10
- Native C# nullability annotations enabled
- Designed to work with Domain Reload disabled


### Features

- Universal: single `State` base class for all state types (gameplay, UI, substates)
- Extensible: virtual Show/Hide and BackShow/ForwardHide methods to override
- Robust bootstrap: correct state hierarchy initializes for any scene
- Early initialization: start from any scene or state with automatic GameFlow setup before the first frame
- Explicit cleanup: `Stage.CloseAndDestroy` ensures proper cleanup of states, resources, and scenes
- Clear data exchange: pass data into a state and receive results back
- Awaitable results: await state results such as popup answers or gameplay outcomes
- TDD-friendly: start from any scene, state, or test case
- Network-ready: tested in networked game projects


### Core Architecture & Runtime

- GameFlow bootstrap prefab to initialize the entire system
- Central `ServiceGameFlow` entry point for controlling game states from code
- Explicit `GameStage` abstraction for major phases such as Boot, Meta, and Core
- `FlowLibrary` for centralized registration and lookup of game states
- Graph-based state model built on `FlowGraph` and `FlowNode`
- Runtime tracking of current and active state nodes
- Explicit `TransitionOperation` for safe and predictable state transitions
- `Opener` interface to decouple state creation from activation


### GameFlow Pro Features

- Extended control over Play Mode initialization
- Additional virtual Open/Close and Forward/Back lifecycle methods
- Layered substates support (e.g. popup layers)
- Fully customizable UniTask-based transition logic
- Precise control over logical events before any view changes
- Asynchronous preload of state views to avoid load spikes
- Split-screen support with a separate `BigStage` per screen


<br/>

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.GameFlow