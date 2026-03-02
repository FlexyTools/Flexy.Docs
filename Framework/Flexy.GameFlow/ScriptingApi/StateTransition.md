# State Transition

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / TransitionOperation


## Description

It is carries transition root FlowNode and methods that define transition behaviour of node  
In custom transition Functions you need to close old states and open new ones visually


## Properties

| Property      | Description                                                                                                                                                       |  
|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Node          | Root FlowNode transition belong to (transiting its chukldren)                                                                                                     |
|               |                                                                                                                                                                   |  
| PlanFullHide  | Customisation point for Planning full state hide                                                                                                                  |
| PlanNormal    | Customisation point for Planning normal state children transition to new visual states. This is where custom layer logic implemented (i.e. default Popups layer ) |
| ExecutePlan   | Customisation point for async executing plan (hiding prev states and showing new ones) with custom visual accompaniment                                           |
| HideAsync     | Customisation point for async hiding one state                                                                                                                    |
| ShowAsync     | Customisation point for async showing one state                                                                                                                   |


## Methods

| Method             | Description                                             |  
|--------------------|---------------------------------------------------------|
| HideStateListAsync | Default way to Hide planned state list                  |  
| ShowStateListAsync | Default way to Show planned state list                  |
| HideChildren       | if state has children run its StateTransition Full Hide |
| ShowChildren       | if state has children run its StateTransition Show      |
| Hide               | Hide prev state and call all events                     |
| Show               | Show next state and call all events                     |


<br/>

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / TransitionOperation
