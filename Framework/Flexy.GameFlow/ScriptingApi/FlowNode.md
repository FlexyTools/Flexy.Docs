# Flow Node

[Flexy.Tools](../../../README.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / FlowNode


## Description

It is building block of FlowGraph RootNode graph create on construction, all other created from Open methods

   
We have 2 layers of operation Logical and View
 - Nodes is logical one
 - States is view one

This means that logic changes independently from view so when you open new  

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
| GameStageNode     | gets neares parent GameStage node                              |


## Methods

| Method              | Description                                                                                           |  
|---------------------|-------------------------------------------------------------------------------------------------------|
| Close               | Close this node                                                                                       |  
| SpawnTransitionRoot | Spawn Transition Root in this node so all child transitions will do in parralel with global ones      |

<br/>

[Flexy.Tools](../../../README.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / FlowNode

