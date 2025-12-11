# How It Works

[Flexy.Tools](../README.md) / [Flexy.GameFlow](README.md) / [Index](Index.md) / How It Works & Use Cases

## Core Concepts

### Bootstrap
Main entry point of game.  
It runs first spawns Service_GameFlow (with global GameContext) and first GameStage to start from  
Typical setup is bootstrap open Boot GameStage. Boot then drive game loading process and Opens Meta GameStage

### Service_GameFlow
Main service of GameFlow.  
It keeps startup ref like root node, library, BackAction and constructs FlowGraph in runtime

### Flow Library
Scriptable object that keeps track of all states the game has, scattered across different directories
Typical usage is RootLibrary, CommonLibrary and one library for each GameStage Boot, Meta and Core  
This is for simplicity of project organization

### Game Stage
Represents big states of a game like Boot, Meta, Core, etc.  
They always spawned as children of Graph Root and by default live as root GameObjects of DontDestroyOnLoad scene
Regular States spawned on different Stage layers by default Base layer sometimes popups layer or any other layer you create        
By default there is one Active State on each layer but this is up to TransitionRoot to decide

### State
Main working horse  
Many states will represent UIWindows and some of them will be PlayStates
Typical states of game: MainMenu, Leaderboard, Settings, PlayState, PauseState, WindState  
States can have substates inside of them. e.g. Shop with Tabs  
You can nest as deep as you like, but most of the time 3 levels is enough

To create new GameState you derive from state class and create prefab from it
Then open state by calling Service_GameFlow.Open<MyStateClass>() or using Openers
 
### Opener
Is small record struct designed to provide statically typed signature of State open interface
It defines all ways state can be opened all Open method signatures

### Transition Root
Responsible for managing transitions between states  

Logical transitions are driven by FlowGraph but Visual ones are driven by TransitionRoot  
TransitionRoot can do only one transition at a time so if you want to show more state transitions at once you need to spawn more TransitionRoot (this is useful in split screen games)  
Transition runs last in Update so code can create many different changes in FlowGraph in frame from different callbacks but,  
transition happens only once in final state from currently active State to new logical Tip     
FlowGraph spawn TransitionRoot on RootNode  

Transition root resolve transition operation for 2 states prev and next from their common parent and operation will do all logic of transition  
Default TransitionOperation is InstantTransition that just deactivate old state and active new one synchronously  
You can define any custom logic of state transitions like animations or overlays that cover screen while transition happening  

Typically GameStage will show Loader screen on opening and closing of itself but sometimes is it handy to have single LoaderScreen covering transition between two GameStages  
because GameStages are Fat, and they often unload old scenes and load new ones as part of transition   
e.g. transition from Meta to Core. Meta first unload Lobby scene and than Core will load requested BattleMap scene 

### Flow Graph
Graph of all opened nodes     
It spawns RootNode on construction and have methods to open, close nodes  
Graph will correctly spawn new node for state open, connect it to graph (set all 6 links) and call LogicalEvents on state like Open, Close, etc 
After any change graph will schedule transition on closest TransitionRoot (in parent hierarchy from change) to do actual transition

### Flow Node 
Each node in graph have parent, firstchild, prev and next siblings and also history forward, back nodes  
So we have 6 axes of freedom here :)

Siblings are used travel all substates of a state.  
Get first\last state of GameStage etc

Forward-back navigation is used to navigate through history of state switches  
Used to go back on back button press


# Use Cases

- Lite version is Free :)
- Universal: One component State for any state (Big, small, sub, UI, Play...)
- Extensible: Various Show/Hide callbacks and actions to override or subscribe
- Separated View: Have 2 layers of operation Logical and View
- Easy launch: Enter play mode from any scene
- Launch from state: No need to launch entire game and go deep to your UI or Play State to test, debug or develop
- Easy cleanup: Close and destory cleanup flow
- Easy data exchange: Pass data to state and back with one line of code
- Await Result: await for state result like popup answer or StatePlay results
- Scene Friendly: States is responsible to load scenes. So you can load any scene from any state
- **[Pro]** Extensible: Various logical Open/Close callbacks to override or subscribe
- **[Pro]** Precise: await for exact moment where logical event is raised
- GameContext based: every big state have it own Flexy.GameContext by design
- TDD-Friendly: Start from any scene and support of disabled domain reload
- Robust: Correct State hierarchy populates upon entering play mode for each scene
- **[Pro]** Robust: even more control and dynamic behaviour on enter play mode
- Simple To Use: Once setup you care only about **one** class State 99% of time
- Ready to go: Provides super simple template to see all states in one place
- **[Pro]** Split screen ready: separate BigState for each screen
- **[Pro]** Felxy transitions: Fully customizable, UniTask based logic of state transition behavior
- Network ready: good fit for network state transitions
- **[Pro]** Async preload: preload state views for instant transitions later (no load spikes)
- Easy bootstrap: simple and short bootstrap script that use only public Api, so you can write your own
- Mature: First version was born in 2012


[Flexy.Tools](../README.md) / [Flexy.GameFlow](README.md) / [Index](Index.md) / How It Works & Use Cases