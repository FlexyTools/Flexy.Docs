![Img](Src/Cover.webp)

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.GameFlow


# Flexy.GameFlow

Universal, hierarchical, dynamic state machine that will manage your  
game states, scenes and transitions as <b>simply and extensibly</b> as  
<b>you have never</b> seen before

[Github](https://github.com/FlexyTools/Flexy.GameFlow)
<!-- | [Unity Forum](https://discussions.unity.com/t/a/1700923)
| [AssetStore](https://u3d.as/3LKx) -->  
[Start Guide](StartGuide.md)
| [How It Works & Use Cases](HowItWorks_UseCases.md)
| [Scripting Api](ScriptingApi/Readme.md)
| [Showcase(Template project)](../../GameTemplates/Barley-Breaks/Readme.md)


## Preface

Any Game is set of Game States that transition into each other  
Big ones like Boot, Lobby(Metagame), Battle(Coregame)  
And small ones like main menu, settings, loading, play state, pause state, cutscene, win\loose screen etc.

Hierarchical GameState machine is fundamental piece of every game  
If you just thought about UI Manager no! It is not UI manager but Flexy.UI builds on top of it because loosing your UI is Big Fail for game 

## Want to control game flow with ease but:

- Don't want to write everything from scratch
- Your code become messy very fast and sometimes state switch become nightmare
- Adding new state to game become harder and harder while project grows
- Your code looks like everything depend on everything even with DI
- Hard to create unique state transition sequences
- Hard to test, debug and maintain
- Passing data between scenes is painful


**Flexy.GameFlow** will manage game states and transitions seamlessly and effortless for you
drastically simplifying management complexity:

- Load game PlayStates and UIStates(screens) **on demand** with one line of code
- Almost **zero** setup and glue code
- Production-proven
- Extensible
- **Easy to use**
- **Easy to clean up**


## Key Strengths

- Lite version is Free :)
- Mature: First version was born in 2012
- Universal: One component State for any state (Big, small, sub, UI, Play...)
- Extensible: Various Show/Hide callbacks and actions to override or subscribe
- Simple To Use: Once setup you care only about **one** class State 99% of time
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

### Pro Features
- Robust: even more control and dynamic behaviour on enter play mode
- Extensible: Various logical Open/Close callbacks to override or subscribe
- Layers support: place substates on different layers in state e.g. popups layer 
- Felxy transitions: Fully customizable, UniTask based logic of state transition behavior
- Precise: await for exact moment where logical event is raised
- Async preload: preload state views for instant transitions later (no load spikes)
- Split screen ready: separate BigState for each screen


[Start Guide](StartGuide.md) | [How It Works & Use Cases](HowItWorks_UseCases.md) | [Scripting Api](ScriptingApi/Readme.md) | [Showcase(Template project)](../GameTemplates.md)


## Technical details

- C# 10
- Native C# Nullability annotations
- Fast Enter Play Mode support

<br/>

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.GameFlow