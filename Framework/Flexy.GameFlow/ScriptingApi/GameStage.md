# Game Stage

[Flexy.Tools](../../../README.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / Game Stage

## Description

Represents big states of a game like Boot, Meta, Core, etc.  
They always spawned as children of Graph Root and by default live as root GameObjects of DontDestroyOnLoad scene
Also every GameStage has its own GameContext

## Properties

| Property          | Description                      |  
|-------------------|----------------------------------|
| Context           | GameContext spawned on GameState |
| Flow              | Access to Service_GameFlow       |


## Methods

| Method                                               | Description                                                                                                |  
|------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
| MoveToLoadedScene                                    | Moves Stage GameObject to provided scene. This is to grant access to GameContext of scene to all substates |  
| MoveToServiceScene                                   | Moves Stage GameObject back to DontDestroyOnLoad scene. Useful while unloading scene                       |
|                                                      |                                                                                                            |
| PreloadSync ( stateRef )                             | Preload State Sync by **stateRef** if not loaded already                                                   |
| PreloadAsync ( stateRef )                            | Preload State Async by **stateRef** if not loaded already                                                  |
| PreloadLibraryAsync ( library, includeDependencies ) | Preload all states of **library** optional with **dependencies**                                           |
| ClearStatesCache ( async )                           | Clean States cache by destroying those who dont used by nodes. Optionally **async**                        |


[Flexy.Tools](../../../README.md) / [Framework](../../Readme.md) / [Flexy.GameFlow](../Readme.md) / [Scripting Api](Readme.md) / Game Stage