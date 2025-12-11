# How It Works & Use Cases

[Flexy.Tools](../README.md) / [Flexy.GameFlow](README.md) / [Index](Index.md) / How It Works & Use Cases

## Main Idea

Game is set of states that transition to each other  
Every state has some visual representation like UIWindow or PlayState  

Because of this GameFlow looks like a UI thing, but it is not   
It is more fundamental, but you will build UI on top of it  

When you play game in Coregame Stage you see GameWorld and something on top of it  
That something is HUD and it is main PlayState of a game   
When that something changes, it means the game switches to a new state (in gamer mind), regardless of how it works under the hood   

Any new state of Game will show new visual representation for gamer so he knows what happens, Cutscene started, Player was killed, Bossfight started, NPC dialog, entered Freecam mode  
All they not only change game visual representation, but also how gamer interact with it, controls changed, camera changed, etc.  
So it is truly different state of a game   
State not only represent new State of a game but actually controls the game in current state and decide when it is ready to switch to another one 

**Flexy.GameFlow** make those states and transition obvious in code too and easy to work with, develop, test

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
Every GameStage has its own GameContext
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


## Use Cases

### Just Default It
Simple game starts from MainMenu (MetaStage) and then transition to PlayState (CoreStage)
Bigger ones have:
- Boot (Splash, EULA, AgeSelect, Consent, Load Profile, Load Resources, etc )
- Meta (Main menu, Settings, Shop, Leaderboard, Arsenal, etc)
- Core (BattleHud, KillKam, Pause, Freecam, Cutscene, Screeshot state, NPCDialog, GameOver, BossFight substate, etc) 

### Split Screen
Super easy implementation of split screen games  
Spawn Separate GameStage for every player with their own TransitionRoots and spawn player specific objects inside GameContext of corresponding GameStage  
This way you almost dont need to change you single player code because everyone trying to access GameStage or PlayerMob or PlayerCamera will access it from local context  
Line like Game.UI.Killcam.Open() will open Kilcam State for current player  

### TabWidows
Windows with tabs inside very handy to implement like State with substates   
So you can implement and test every tab in isolation and if it needs to show in other places  
Tab window itself responsible only for switching tabs nicely with animations  

[Flexy.Tools](../README.md) / [Flexy.GameFlow](README.md) / [Index](Index.md) / How It Works & Use Cases