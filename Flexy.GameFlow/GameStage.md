# Game Stage

[Home](README.md) | [Actions](Actions.md) | [Bindings](Bindings.md) | [Common Utilities](CommonUtilities.md)

This is the main building block in GameFlow
Typical game consists of 3 Stages 
- Boot - init and load game
- Meta - main menu and all game navigation before entering coregame (battle/run/race/fight) 
- Core - coregame. play some GameMode on some Map or what your game looks like 

 This is Frontnend of hierarchical state machine that controls entire game (backend id FlowGraph)   
 You create your stages (each one is prefab) and than spawn when it is time  
 Game starts from spawning first stage (usually Boot) and control moves to it  
 Every stage can have sub states that can have substates and so on, but for most cases 3 levels is enough      

Simple game looks like this:
- Stage_Boot
  - EULA
  - Age Select 
- Stage_Meta
  - MainMenu
  - Settings
    - Graphics
    - Audio
    - Controls  
  - Shop
  - Arsenal
  - Choose Match
  - ... 
- Stage_Core
  - State_PressAnyKeyToPlay
  - State_Play
  - State_Pause
  - State_Loose
  - State_Victory
  - PlayResults
  - ...  


##  Key Strengths

- Easy to use! After proposed project setup state open look like: ```Game.UI.Settings.Open();``` 
- Starts before any other game logic in project withbout any requirements to game code
- Start from any battle scene and before any code on your objects can run Entire Hierarchy of states will be populated and all events called same way as if you go from Boot co Meta to Core by hand  
- Easily create TEST scenes to test any game mechanics and start from them with choosen TestCase of state
- Create separate TEST scene for every UIWIndows to speed up development and testing of it by start from that window with exact TestCase   
- Easily Customize transitions between states and only their look but even logic of transition
- Ready for and demand loading, prealoding and packing to bundles
- Works with Domain Reload off
- Written in modern code. C# 10 features like Records, Generics, and more
- Easy drop in solution for adding new states int the game. Just duplicate state prefab replace state class and open from code. Everything else already works

While it looks like GameFlow tied to UI. It is not  
It is only very flexible and universal, hierarchical state machine designed specifically for games and Unity  
But UI System like Flexy.UI depends on it 

##  Uasge Sample

Ready to use [Barley-Breaks Flexy.GameTemplate](../GameTemplates.md) showcase all currently available flexy packages including GameFlow

[Home](README.md) | [Actions](Actions.md) | [Bindings](Bindings.md) | [Common Utilities](CommonUtilities.md)