# Scripting Api

[Flexy.Tools](../README.md) / [Flexy.GameFlow](../README.md) / ScriptingApi



| Class                                          | Description                                                                                                         |  
|:-----------------------------------------------|:--------------------------------------------------------------------------------------------------------------------|
| [Game Flow Bootstrap](GameFlowBootstrap.md)    | Boot script/prefab that bootstraps GameFlow                                                                         |  
| [Service GameFlow](Service_GameFlow.md)        | Entry point into GameFlow                                                                                           |
| [Flow Library](FlowLibrary.md)                 | Library that collects ref to all states of the game                                                                 |
| [Game Stage](GameStage.md)                     | Big state of a game like Boot, Meta, Core, etc.                                                                     |
| [State](State.md)                              | Main working horse Derive from this class to create states of Your Game create prefabs of them and Open when needed |
| [Opener](Opener.md)                            | Open interface of State                                                                                             |
| [Transition Root](TransitionRoot.md)           | Responsible for Switching states and storing current Tip Node and Active State Nodes to know where we are currently |
| [Transition Operation](TransitionOperation.md) | It is a struct that carries transition data and has methods that help you write correct State Transition Logic      |
| [Flow Graph](FlowGraph.md)                     | Stores state graph starting from root FlowNode and allows to manipulate it                                          |
| [Flow Node](FlowNode.md)                       | It is building block of FlowGraph                                                                                   |


[Flexy.Tools](../README.md) / [Flexy.GameFlow](../README.md) / ScriptingApi