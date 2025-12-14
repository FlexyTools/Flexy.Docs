# State

[Flexy.Tools](../../../README.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / State


## Description

Inherits from: Flexy.Core.Binding.BindableBehaviour

Main working horse 
Derive from this class to create states of Your Game create prefabs of them and Open when needed


## Component

| Fields  | Description                             |  
|---------|-----------------------------------------|
| Showing | FlexyAction that raise right after show |
| Hiding  | FlexyAction that raise right after hide |

## Properties

| Property                | Description                                                        |  
|-------------------------|--------------------------------------------------------------------|
| Graph                   | Access FlowGraph                                                   |
| Node                    | FlowNode currently connected to State                              |
| PrefabRef               | AssetRef to state Prefab                                           |
|                         |                                                                    |
| OpenParams              | Parameters this node is opened with                                |
|                         |                                                                    |
| IsOpened                | true if node still part of the graph false otherwise               |
| IsShowed                | true if node state is currently showed                             |
| AnySubStateOpened       | true if node has opened substates                                  |
|                         |                                                                    |
| GameStage               | gets neares parent GameStage                                       |
|                         |                                                                    |
| virtual MainSubStateRef | Must return StateRef in case state designerd to have main substate |
see [BindableBehaviour](../../Flexy.Core/Bindings.md) for inherited ones

## Methods

| Method                          | Description                                                                                                                     |  
|---------------------------------|---------------------------------------------------------------------------------------------------------------------------------|
| OpenMainSubState                | Opens Main Sub State if State has MainSubStateRef and close all to the main if it already opened                                |
| Close                           | Close state. GameObject remain alive and will be reused for future opening                                                      |
| CloseAndDestroy                 | Close state and Destroy state GameObject                                                                                        |
| CloseSubStates                  | Close all substates with or whtout main substate                                                                                |
|                                 |                                                                                                                                 |
| RebindAllHierarchy              | Get all BindableBehaviours in Children and call RebindAll on them                                                               |                                
|                                 |                                                                                                                                 |
| virtual TryGoBack               | override reaction ToTryGoBack, return true to allow go back otherwise false                                                     |  
| virtual GetLayers               | override to setup additional layers for this state. You need to provide InstantiateSubState and GetTransition to make them work |
| virtual InstantiateSubState     | override to decide where to instantiate each substate. For GameStages by default it is _statesContainer                         |
| virtual DestroySubState         | override to correctly destroy Instantiated Substate                                                                             |
|                                 |                                                                                                                                 |
| virtual OnOpen                  | Event. Happens when State Open                                                                                                  |
| virtual OnShow                  | Event. Happens when State Shows first time for Opened FlowNode                                                                  |
| virtual OnForward               | Event. Happens when next State Open when this stop becoming Last one in history                                                 |
| virtual OnFwdHide               | Event. Happens when State Hidden because next one in hostory Showing                                                            |
| virtual OnBack                  | Event. Happens when next State closed and current become last in history again                                                  |
| virtual OnBackShow              | Event. Happens when State Showing because next was closed                                                                       |
| virtual OnClosing               | Event. Happend when State is closed and no more part of history                                                                 |
| virtual OnHide                  | Event. Happens when State Hidden because node closed and no more part of history                                                |                                                                        |
|                                 |                                                                                                                                 |
| virtual OnFirstChildOpen        | Event. Happens before first child opened                                                                                        |
| virtual OnFirstChildShow        | Event. Happens before first child showed                                                                                        |
| virtual OnLastChildClose        | Event. Happens after last child hide                                                                                            |
| virtual OnLastChildHide         | Event. Happens after last child hide                                                                                            |
| virtual OnFirstChildOpenOnLayer | Event. Happens before first child opened on layer                                                                               |
| virtual OnFirstChildShowOnLayer | Event. Happens before first child showed on layer                                                                               |
| virtual OnLastChildCloseOnLayer | Event. Happens after last child hide on layer                                                                                   |
| virtual OnLastChildHideOnLayer  | Event. Happens after last child hide on layer                                                                                   |
see [BindableBehaviour](../../Flexy.Core/Bindings.md) for inherited ones

<br/>

[Flexy.Tools](../../../README.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / State

