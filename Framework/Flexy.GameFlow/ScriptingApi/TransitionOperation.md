# Transition Operation

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / TransitionOperation


## Description

Inherits from: struct

It is a struct that carries transition data and has methods that help you write correct State Transition Logic  
In custom transition Function you need to close old state and open new one visually


## Properties

| Property      | Description                                      |  
|---------------|--------------------------------------------------|
| PrevNode      | Node we go from                                  |
| NextNode      | Node we go to                                    |  
| PresIsForward | true if prev node going forward, otherwise false |
| NextIsForward | true if next node going forward, otherwise false |


## Methods

| Method                | Description                         |  
|-----------------------|-------------------------------------|
| HidePrev              | Hide prev state and call all events |  
| ShowNext              | Show next state and call all events |
| under construction... |                                     |


<br/>

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / TransitionOperation
