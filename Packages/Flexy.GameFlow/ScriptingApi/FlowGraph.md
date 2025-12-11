# Flow Graph

[Flexy.Tools](../README.md) / [Flexy.GameFlow](../README.md) / [Scripting Api](Readme.md) / FlowGraph


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

Close?

<br/>

[Flexy.Tools](../README.md) / [Flexy.GameFlow](../README.md) / [Scripting Api](Readme.md) / FlowGraph