![Img](Src/GameStage.png)

# Game Stage

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / Game Stage

## Description

Inherits from: State

Big state of a game like Boot, Meta, Core, etc.  
They always spawned as children of Graph Root and by default live as root GameObjects of DontDestroyOnLoad scene
Also every GameStage has its own GameContext

## Component

| Field             | Description                                                                 |  
|-------------------|-----------------------------------------------------------------------------|
| Main State Ref    | Optional. Reference to main state of stage to auto load                     |
| States Container  | Transform inside stage where all states of **Base** layer will be spawned   |
| Popups Container  | Transform inside stage where all states of **Popups** layer will be spawned | 


## Properties

| Property          | Description                      |  
|-------------------|----------------------------------|
| Context           | GameContext spawned on GameState |
see [State](State.md) for inherited ones

## Methods

| Method                                               | Description                                                                                                |  
|------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| MoveToLoadedScene                                    | Moves Stage GameObject to provided scene. This is to grant access to GameContext of scene to all substates |  
| MoveToServiceScene                                   | Moves Stage GameObject back to DontDestroyOnLoad scene. Useful while unloading scene                       |

see [State](State.md) for inherited ones

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / Game Stage