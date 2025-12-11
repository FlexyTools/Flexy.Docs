# Transition Root

[Flexy.Tools](../../../README.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / TransitionRoot


## Description

This graph stores state graph starting from root FlowNode and allows to manipulate it   
Each node in graph have parent, firstchild, left and right siblings also history forward and back nodes  
So we have 6 axes of freedom here :)


## Properties

| Property | Description              |  
|----------|--------------------------|
| Service  | Access Service_GameFlow  |
| Root     | Access RootNode of graph |  


## Methods

| Method                                              | Description                                                                                               |  
|-----------------------------------------------------|-----------------------------------------------------------------------------------------------------------|
| Open ( AssetRef<GameStage> stageRef )               | Load, Spawn and Open Stage by AssetRef                                                                    |  
| Open ( AssetRef<State> stateRef, State callSource ) | Load if not loadedm Spawn if not spawned and Open state by AssetRef and callSource to know where to spawn |
| TryGoBack                                           | Try Go Back in history of opened states if current node allows                                            |



### LockOn\UnLock (Pro feature)
Allows to lock graph on some state so any **external** attempts to change state will open it before locked one in graph   
Current state is allowed to change itself to any other

E.g. in Networked FPS you open PauseState and lock it. You can freely navigate to setting and other states but
if game try to put you from PlayState to KilledState and back it will happens under pause menu so
user flow will not be interrupted. When user exits pauseState it will go back to PlayState or KilledState based on what is actually active here


<br/>

[Flexy.Tools](../../../README.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / TransitionRoot
