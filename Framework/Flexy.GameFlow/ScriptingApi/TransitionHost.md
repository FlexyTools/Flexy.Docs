# Transition Host

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / Transition Host


## Description

Inherits from: object

Responsible for Switching states and storing current Tip Node and Active State Nodes to know where we are currently
Launches TransitionOperation in correct frame spot if Transition Requested 

## Properties

| Property       | Description                                                              |  
|----------------|--------------------------------------------------------------------------|
| Node           | FlowNode this host lives on                                              |
| TipNode        | FlowNode tha is logically last one in History                            |
| ActiveNode     | FlowNode tha is last showed and currently showing                        |
|                |                                                                          |  
| LockOn? (Pro)  | FlowNode? current host locked on                                         |
| IsInTransition | Return true if host currently in the middle of state transition          |
| TransitionFrom | Return FlowNode we transition from or null if there is no transition now |
| TransitionTo   | Return FlowNode we transition to or null if there is no transition now   |


## Methods

| Method        | Description                                                                                                |  
|---------------|------------------------------------------------------------------------------------------------------------|
| TryGoBack     | Try Go Back in history of opened states if current state allows                                            |
| LockOn (Pro)  | Lock FlowNode so any try to open new state not from Tip Node will be opened behind Locked node in historey |
| UnLock (Pro)  | Unlock locked node                                                                                         |


<br/>

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / Transition Host
