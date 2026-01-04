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

Production-proven architecture, evolving in real projects since 2012  
Start small: install Lite, launch a state from any scene, and feel the difference in minutes — not days

Design your game as explicit, testable states — from Boot and Meta to Core gameplay — so you can change and extend game flow safely, even late in development
  

## When game flow starts working against you

**Architecture**
- Game flow logic becomes messy and fragile as the project grows
- Everything starts depending on everything, even when using DI
- Adding a new game state creates dependency hell and unexpected side effects

**Scalability**
- Complex transition sequences are hard to build and reason about
- Adding new state to game becomes harder and harder while project grows
- Custom flow solutions break when requirements change

**Development workflow**
- Testing a specific state requires running the whole game
- Passing data between states or scenes becomes cumbersome
- Debugging game states and transitions is painful


## How Flexy.GameFlow solves this

- **One State model for everything**  
Gameplay, Meta flow, UI, cutscenes, and overlays are all game states


- **Launch and test any game state instantly**  
Game Flow initializes the correct state hierarchy before the first frame 


- **Awaitable states and transitions**  
Treat game flow like async code and await results cleanly


- **Explicit data flow between states**  
Pass data in and out without singletons or hidden dependencies


- **Strong state isolation by design**  
States own their lifecycle and cleanup


- **Architecture that scales with complexity**  
Same model works from prototype to production


- **Framework-agnostic by intent**  
No forced UI system, scene structure, or networking stack


## Preface

Any Game is set of Game States that transition into each other  
Big Stages like Boot, Lobby(Metagame), Battle(Coregame)  
And their states like main menu, settings, loading, play state, pause state, cutscene, win\loose screen etc

Hierarchical game state management is a fundamental part of every game  
Flexy.GameFlow is a **Game State manager**, not a UI manager
Every state must have some UI to allow control for Gamer but this in developer responsibility

Flexy.GameFlow is intentionally agnostic to rendering, UI frameworks, and networking solutions  
Support singleplayer, multiplayer, coop, and split-screen projects without structural changes


## Advanced Capabilities

### Architecture

- Hierarchical game state composition  
  Build game flow using nested and layered states instead of flat logic

- Clear separation between state bearch/death, logic and view
  State bearth/Death, logical Show/Hide and View are all separated and allow more fain grained control

- Dedicated GameContext per major game state  
  Each state has its own scoped data and dependencies

- Transition model ready for networking  
  State transitions are designed to work in singleplayer and multiplayer flows


### Workflow

- Enter Play Mode from any scene  
  Game flow initializes the correct state hierarchy before the first frame

- Works with Domain Reload disabled  
  No hidden static state or broken initialization

- Clean spawn / destroy lifecycle  
  States always shut down correctly, destroy and forget is safe by design

- TDD-friendly by design  
  Game states can be tested in isolation


### Scene & Navigation

- State-driven scene management  
  Game states explicitly control which scenes are loaded and unloaded

- Cross-scene references  
  Reference object from other scenes to connect portals or other cases

- Multi-scene maps and portals  
  Supports complex maps split into multiple scenes

- No need to add scenes to Build Settings  
  Scenes & Maps collects automatically and sends to build (thanks to AssetRefs.Pileines)



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
- You prefer ad-hoc managers and scene-based logic


## Flexy Game.Flow vs Other Solutions 

<details><summary> Why not a classic FSM?</summary>

Classic FSMs work well for isolated systems like AI or animation,
but they do not scale to managing the entire game flow

They break down when:
- Game flow is spread across many scenes and managers
- States need hierarchy and parallel layers
- Transitions depend on context or async logic

<br></details>

<details><summary> Why Not Scene Managers?</summary>

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

You do not manage scenes  
You orchestrate game behavior — scenes simply follow

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

- Evolving since 2012
- Designed by a developer who builds full games, not just frameworks
- Used as a foundation for other Flexy.Tools systems
- Free Lite version to validate the approach before committing


[Start Guide](StartGuide.md) | [How It Works & Use Cases](HowItWorks_UseCases.md) | [Scripting Api](ScriptingApi/Readme.md) | [Showcase(Template project)](../GameTemplates.md)


## Technical details

- C# 10
- Native C# Nullability annotations
- Domain Reload disabled friendly
	
### Features 

- Universal: One component `State` for any state (Big, small, sub, UI, Play...)
- Extensible: Various virtual methods Show/Hide BackShow/ForwardHide to override
- Simple To Use: Once setup you care only about **one** class `State` 99% of time
- Easy launch: Enter play mode from any scene
- Launch from state: No need to launch entire game and go deep to your UI or Play State to test, debug or develop
- Easy cleanup: Close and destory cleanup flow
- Easy data exchange: Pass data to state and back with one line of code
- Await Result: await for state result like popup answer or StatePlay results
- Scene Friendly: States is responsible to load scenes. So you can load any scene from any state
- Easy bootstrap: simple and short bootstrap script that use only public Api, so you can write your own
- GameContext based: every big state have it own Flexy.GameContext by design
- TDD-Friendly: Start from any scene and support of disabled domain reload
- Separated View: Have 2 layers of operation Logical and View
- Network ready: good fit for network state transitions
- Robust: Correct State hierarchy populates upon entering play mode for each scene


### GameFlow Pro Features
- Robust: even more control and dynamic behaviour on enter play mode
- Extensible: Various logical Open/Close callbacks to override or subscribe
- Layers support: place substates on different layers in state e.g. popups layer
- Flexy transitions: Fully customizable, UniTask based logic of state transition behavior
- Precise: await for exact moment where logical event is raised
- Async preload: preload state views for instant transitions later (no load spikes)
- Split screen ready: separate BigStage for each screen

<br/>

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.GameFlow