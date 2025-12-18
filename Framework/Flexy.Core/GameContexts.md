# **Flexy.Core GameContext**

[Home](Readme.md) | [Actions](Actions.md) | [Bindings](Bindings.md) | [Common Utilities](CommonUtilities.md)


Flexy way to think about game dependencies and their composition. **Context based**  
You can think like DI Container but more clear and tied to scenes and GameObjects instead of live in thin air   

Any GameObject or Component always lives in context! actually deep inside hierarchy of contexts  
From closest to farthest:
- GameObject
- Parent line of GameObjects to the root
- Scene
- Unity
- C# Env
- OS 

Programmers can access any service from any context from any place like:
```csharp
gameObject.layer
gameObject.transform.root
gameObject.scene.name
Physics.Raycast
Screen.width
Single.Parse
Thread.Sleep
Environment.ProcessorCount
File.Exists
``` 
We know that it is safe to access any of those contexts because they was bord before our Component and will die only after it

GameContexts continue this concept to user space. 
So we create GameContexts hierarchy in game fill it with services and put objects to live in it  
Everything visually 

They replace SceneContext and default unity context hierarchy becomes (sample of Networked FPS):
- GameObject
- Parent line of GameObjects to the root
- ---
- GameModeContext
- MapContext
- CoregameContext
- BootContext
- GlobalContext
- ---
- Unity
- C# Env
- OS

There is also MetagameContext instead of Coregame amp and GameMode when we not in battle  
Every context have their own services that inits before any other code can run so it is safe to access any service  
You can access services directly or of you wish you can write simple methof that injects services from context to your component like any DI containers do

Pairing with GameFlow package it is very powerful system to manager game flow and services
FlexyTemplate Barley-Break shows many project organisation concepts and showcase proposed way to use GameContexts 

[Home](Readme.md) | [Actions](Actions.md) | [Bindings](Bindings.md) | [Common Utilities](CommonUtilities.md)