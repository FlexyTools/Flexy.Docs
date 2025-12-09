![Image Sequence_038_0002](https://github.com/user-attachments/assets/792efb83-33db-4c8c-8e92-2c8e5a363522)
[Start Guide](StartGuide.md) | [Showcase(Template project)](../GameTemplates.md) | [FAQ](FAQ.md)

<!-- 
| [Unity Forum](https://discussions.unity.com/t/flexy-assetrefs-v5-0-0-released/1605799) 
| [Asset Store](https://u3d.as/3u78)
-->
# Flexy.GameFlow

Any Game is set of Game States that transition into each other  
Big ones like Boot, Lobby(Metagame), Battle(Coregame)  
And small ones like main menu, settings, loading, play state, pause state, cutscene, win\loose screen etc.

Hierarchical GameState machine is fundamental piece of every game


## Want to control game flow with ease but:

- Don't want to write everything from scratch
- Your code become messy very fast and sometimes state switch become nightmare
- Adding new state to game become harder and harder while project grows
- Your code looks like everything depend on everything even with DI
- Hard to create unique state transition sequences
- Hard to test, debug and maintain


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
- Universal: One component State for any state (Big, small, sub, UI, Play...)
- Extensible: Various Show/Hide callbacks and actions to override or subscribe
- Separated View: Have 2 layers of operation Logical and View
- Easy launch: Enter play mode from any scene
- Launch from state: No need to launch entire game and go deep to your UI or Play State to test, debug or develop
- Easy cleanup: Close and destory cleanup flow
- **[Pro]** Await Result: await for state result like popup answer or StatePlay results
- **[Pro]** Extensible: Various logical Open/Close callbacks to override or subscribe
- **[Pro]** Precise: await for exact moment where logical event is raised
- GameContext based: every big state have it own Flexy.GameContext by design
- TDD-Friendly: Start from any scene and support of disabled domain reload
- Robust: Correct State hierarchy populates upon entering play mode for each scene
- **[Pro]** Robust: even more control and dynamic behaviour on enter play mode
- Simple To Use: Once setup you care only about **one** class State 99% of time
- Ready to go: Provides super simple template to see all states in one place
- **[Pro]** Split screen ready: separate BigState for each screen
- **[Pro]** Felxy transitions: Fully customizable, UniTask based logic of transition behavior
- Network ready: good fit for network state transitions
- **[Pro]** Async preload: preload state views for instant transitions later (no load spikes)
- Easy bootstrap: simple and short bootstrap script that use only public Api, so you can write your own
- Mature: First version was born in 2012


See [StartGuide](StartGuide.md) for usage samples


## Flexy.GameFlow is

Universal Hierarchical stater machine that will manage your  
game states, transitions,  in a so simple way you never seen before


## Technical details

- C# 10
- Native C# Nullability annotations
- Fast Enter Play Mode support