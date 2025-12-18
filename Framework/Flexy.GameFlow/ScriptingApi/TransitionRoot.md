# Transition Root

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / TransitionRoot


## Description

Inherits from: object

Responsible for Switching states and storing current Tip Node and Active State Nodes to know where we are currently
Launches TransitionOperation in correct frame spot if Transition Requested 

## Properties

| Property    | Description                                       |  
|-------------|---------------------------------------------------|
| Tip Node    | FlowNode tha is logically last one in History     |
| Active Node | FlowNode tha is last showed and currently showing |  


## Methods

| Method         | Description                                                                                                |  
|----------------|------------------------------------------------------------------------------------------------------------|
| Try Go Back    | Try Go Back in history of opened states if current state allows                                            |
| Transition Now | Launch Transition logic now. Mostly for Bootstrapper                                                       |
| LockOn         | Lock FlowNode so any try to open new state not from Tip Node will be opened behind Locked node in historey |
| UnLock         | Unlock locked node                                                                                         |


<br/>

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / TransitionRoot
