# Flow Node

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / FlowNode


## Description

Inherits from: object

It is building block of FlowGraph  
RootNode graph creates on construction, all others created from Open methods
Upon calling FlowGraph.Open new Node is created, added to history and returned back to caller

## Properties

| Property           | Description                                                    |  
|--------------------|----------------------------------------------------------------|
| Graph              | Access FlowGraph                                               |
| State              | State instance of this node                                    |
|                    |                                                                |
| WasShowed          | true if node already was showed earlier                        |
| ChildrenShowed     | true when at least one child of this node is showed            |
| OpenParams         | Parameters this node is opened with                            |
| StateData          | Custom data linked from node state                             |
| UserData           | Custom data linked from outside node state                     |
|                    |                                                                |
| Back               | Link to previous node in history                               |
| Forward            | Link to next node in history                                   |
| PrevSibling        | Link to prev sibling node                                      |
| NextSibling        | Link to next sibling node                                      |
|                    |                                                                |
| Parent             | Link to parent node                                            |
| LayerName          | Name of layer this node spawned on                             |
| BaseLayer          | Base layer for children of this node (have link to next layer) |
| FirstBaseChild     | Link to first child node if layer **Base**                     |
|                    |                                                                |
| IsOpened           | true if node still part of the graph false otherwise           |
| IsShowing          | true if node state is currently showing                        |
| IsOpenedAndShowing | true if node is opened state is currently showing              |
| TransitionHost     | gets nearest TransitionHost in parent hierarchy                |
| GameStageNode      | gets nearest parent GameStage node                             |

## Events

| Event         | Description                      |  
|---------------|----------------------------------|
| GotForward    | event. raised right after hook   |
| GotNext       | event. raised right after hook   |
| ForwardHidden | event. raised right after hook   |
| GotBack       | event. raised right after hook   |
| GotPrev       | event. raised right after hook   |
| BackShowed    | event. raised right after hook   |


## Methods

| Method                  | Description                                                                                                             |  
|-------------------------|-------------------------------------------------------------------------------------------------------------------------|
| OpenMainSubState        | Open Main Substate if exists                                                                                            |
| Close                   | Close this node                                                                                                         |  
| SpawnTransitionRoot     | Spawn Transition Root in this node so all child transitions will do in parralel with global ones                        |
| WaitResultOnHide < T >  | Async Operation to wait for state hide and return result of ExpectedType (state must implement IStateWithResult < T >)  |
| WaitResultOnClose < T > | Async Operation to wait for state close and return result of ExpectedType (state must implement IStateWithResult < T >) |


## Extensions

| Method          | Description                                                                               |  
|-----------------|-------------------------------------------------------------------------------------------|
| WaitShow        | Async wait for Node WaitShow event. Continuation happens right after event in code        |  
| WaitClose       | Async wait for Node WaitClose event. Continuation happens right after event in code       |
| WaitHide        | Async wait for Node WaitHide event. Continuation happens right after event in code        |


<br/>

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / FlowNode

