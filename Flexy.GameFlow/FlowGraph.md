# **Flow Graph**

[Home](README.md) | [Actions](Actions.md) | [Bindings](Bindings.md) | [Common Utilities](CommonUtilities.md)


This graph stores state graph starting from root FlowNode and allows to manipulate it   
Each node in graph have parent, firstchild, left and right siblings and history forward and back nodes  
So we have 6 axes of freedom here :)

## Structure

### Hierarchy
Parent-child relationship is used to organize hierarchy  
Root Node in hierarchy created with graph itself. Then you spawn GameStages (Boot, Meta, Core). It is first level of nesting  
Game stages spawn states inside of it. Meta:MainMenu, Leaderboard, Settings. Core: PlayState, PauseState, WindState.
States can have substates inside of them. e.g. Shop with Tabs
You can nest as deep as you like, but most of the time 3 levels is enough 

### Siblings
siblings are used travel all substates of a state.  
Get first\last state of GameStage etc 

### History
Forward-back navigation is used to navigate through history of state switches  
Mostly is used to go back on back button press


## Methods

### Open
Opens new state and switches to it

### GoBack
Try to go back if current state allows

### LockOn\UnLock (Pro feature)
Allows to lock graph on some state so any **external** attempts to change state will open it before locked one in graph   
Current state is allowed to change itself to any other

E.g. in Networked FPS you open PauseState and lock it. You can freely navigate to setting and other states but 
if game try to put you from PlayState to KilledState and back it will happens under pause menu so 
user flow will not be interrupted. When user exits pauseState it will go back to PlayState or KilledState based on what is actually active here  
 

[Home](README.md) | [Actions](Actions.md) | [Bindings](Bindings.md) | [Common Utilities](CommonUtilities.md)