![Img](ScriptingApi/Src/GameContext.webp)

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / [Flexy.Core](Readme.md) / GameContext

# Game Context

## Description
Flexy way to think about game dependencies and their composition. **Context based**  
You can think like DI Container but more clear and tied to scenes and GameObjects so you can get GameContext from every GO or scene

## Idea
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
It is safe to access any of those contexts because they were born and initialized before our Component and will die only after it

GameContexts continue this concept into **Your Game**  
So I create GameContexts hierarchy in game, fill it with services, and put objects to live inside those contexts  
Everything visually 

They replace SceneContext and default unity context hierarchy becomes (sample of Networked FPS):
- GameObject
- Parent line of GameObjects to the root
- ---
- GameModeContext
- MapContext (strongest connection to scene)
- CoregameContext
- BootContext
- GlobalContext
- ---
- Unity
- C# Env
- OS

There is also MetagameContext instead of Coregame and GameMode when we not in the battle    
Every context have their own services that inits before any other code can run so it is safe to access any service

## Outcome
You can access services directly or you can write simple method that injects services from context to your component like any DI containers do  
Most important part is not how you access serives but how you organize and init them 

This way, implementing a new feature, you need to think only about the Context it needs to live in  
Talking about dependencies, features must not depend on other features but only on Services in Contexts  
This will make it easy to Test features in isolation but in Right context  
And this is easy to achieve using [Flexy.GameFlow](../Flexy.GameFlow/Readme.md) package and Test_Feature scenes that spawn and init Correct Context in frame 0, before any other code can execute, so your code never needs any special logic to wait context initialization     

## How it works
You create Prefab with GameContext component and fill it with services you need    
They will init in same order you visually see then on GameObject   
GameContext inspector have info about what will be registered as service from Prefab  
You can additionally control this with **IService[Async]** interface and ServiceProvider  
Services will be registered with real object types, so to autoregister base abstract types you can use [ServiceTypes] Attrbiute      

Each GameContext is linked to scene  
Can be linked only to all scenes (default behaviour), to local scene or non of them (then link manually )  
Also it has parent context to find services from the entire hierarchy, if parent is not specified before Awake context will get it from the current scene. This way contexts automatically liked to each other on spawn   

One more thing: if there is not context in time of accessing first service Global Empty context will be created automatically  

Then you can from inside any MonoBehaviour call this.GetService<T>() to get service from the context your object lives in  
[FlexyTT Barley-Break](../../GameTemplates/Barley-Breaks/Readme.md) shows how all this works in practice

## Extensibility
You add any services you with on GameObject with GameContext  

You can add Context Providers that will register anything you want into Context  
ServicesFrom_ScriptableObjects and ServicesFrom_MonoBehaviours already part of package but you can create your own

You can place IGameContextExtension MonoBehaviour alongside GameContext component and it will be registered as extension and few registration events wiill be passed to it same as GetService call in case service was not found in context itself  
This way you can add very custom service providers into context like VContainer or Zenject. While I dont recommend to use those containers as additions (unless you know what you are doing) but, sometimes it is useful e.g. for migration 


## Showcase
Pairing with GameFlow package it is very powerful system to manager game flow and services  
[FlexyTT Barley-Break](../../GameTemplates/Barley-Breaks/Readme.md) shows many project organisation concepts and showcase recommended way to use GameContexts

<br/>

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / [Flexy.Core](Readme.md) / GameContext