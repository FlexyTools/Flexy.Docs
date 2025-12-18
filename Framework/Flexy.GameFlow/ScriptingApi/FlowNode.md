# Flow Node

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / FlowNode


## Description

Inherits from: object

It is building block of FlowGraph  
RootNode graph creates on construction, all others created from Open methods
Upon calling FlowGraph.Open new Node is created, added to history and returned back to caller

## Properties

| Property          | Description                                                    |  
|-------------------|----------------------------------------------------------------|
| Graph             | Access FlowGraph                                               |
| State             | State instance of this node                                    |
|                   |                                                                |
| FullyInited       | If it is false in OnShow than first show came from BackShow    |
| HasShowedChildren | true when at least one child of this node is showed            |
| OpenParams        | Parameters this node is opened with                            |
| StateData         | Custom data linked from node state                             |
| UserData          | Custom data linked from outside node state                     |
|                   |                                                                |
| Back              | Link to previous node in history                               |
| Forward           | Link to next node in history                                   |
| PrevSibling       | Link to prev sibling node                                      |
| NextSibling       | Link to next sibling node                                      |
|                   |                                                                |
| Parent            | Link to parent node                                            |
| LayerName         | Name of layer this node spawned on                             |
| BaseLayer         | Base layer for children of this node (have link to next layer) |
| FirstChild        | Link to first child node                                       |
|                   |                                                                |
| IsOpened          | true if node still part of the graph false otherwise           |
| IsShowed          | true if node state is currently showed                         |
| TransitionRoot    | gets nearest TransitionRoot in parent hierarchy                |
| GameStageNode     | gets nearest parent GameStage node                             |


## Methods

| Method              | Description                                                                                                             |  
|---------------------|-------------------------------------------------------------------------------------------------------------------------|
| Close               | Close this node                                                                                                         |  
| SpawnTransitionRoot | Spawn Transition Root in this node so all child transitions will do in parralel with global ones                        |
| WaitResult < T >    | Async Operation to wait for state close and return result of ExpectedType (state must implement IStateWithResult < T >) |


## Extensions

| Method          | Description                                                                               |  
|-----------------|-------------------------------------------------------------------------------------------|
| WaitShow        | Async wait for Node WaitShow event. Continuation happens right after event in code        |  
| WaitForward     | Async wait for Node WaitForward event. Continuation happens right after event in code     |
| WaitForwardHide | Async wait for Node WaitForwardHide event. Continuation happens right after event in code |
| WaitBack        | Async wait for Node WaitBack event. Continuation happens right after event in code        |
| WaitBackShow    | Async wait for Node WaitBackShow event. Continuation happens right after event in code    |
| WaitClose       | Async wait for Node WaitClose event. Continuation happens right after event in code       |
| WaitHide        | Async wait for Node WaitHide event. Continuation happens right after event in code        |


<br/>

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / FlowNode

