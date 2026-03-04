[Flexy.Tools](../Readme.md) / [Flexy.GameFlow](../Readme.md) / ScriptingApi

# Scripting Api

| Class                                                      | Description                                                                                                         |  
|:-----------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------|
| [Game Flow Bootstrap](GameFlowBootstrap.md)                | Boot script/prefab that bootstraps GameFlow                                                                         |  
| [Service GameFlow](Service_GameFlow.md)                    | Entry point into GameFlow                                                                                           |
| [Flow Library](FlowLibrary.md)                             | Library that collects ref to all states of the game                                                                 |
| [Game Stage](GameStage.md)                                 | Big state of a game like Boot, Meta, Core, etc.                                                                     |
| [State](State.md)                                          | Main working horse Derive from this class to create states of Your Game create prefabs of them and Open when needed |
| [Opener](Opener.md)                                        | Open interface of State                                                                                             |
| [Transition Host](TransitionHost.md)                       | Responsible for Switching states and storing current Tip Node and Active State Nodes to know where we are currently |
| [State Transition](StateTransition.md)                     | It is a struct that carries transition data and has methods that help you write correct State Transition Logic      |
| [Flow Graph](FlowGraph.md)                                 | Stores state graph starting from root FlowNode and allows to manipulate it                                          |
| [Flow Node](FlowNode.md)                                   | It is building block of FlowGraph                                                                                   |
|                                                            |                                                                                                                     |
| [Cross Scene Refs](CrossSceneRefs.md)                      | This is ref to MonoBehaviour T on another scene and few utils to make it work                                       |
| [Map Portals & Transitions](MapPortalsAndTransitions.md)   | MapPortal that allow to jump to other scene. And few classes that make it happen                                    |

<br/>

[Flexy.Tools](../Readme.md) / [Flexy.GameFlow](../Readme.md) / ScriptingApi