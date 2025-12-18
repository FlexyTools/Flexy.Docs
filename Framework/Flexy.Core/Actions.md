# **Flexy.Core Actions**

[Home](Readme.md) | [Bindings](Bindings.md) | [Game Contexts](GameContexts.md) | [Common Utilities](CommonUtilities.md)


**Flexy Actions** is universal and composable system to do action in response to event.  
Fo example, play sfx, show vfx, play animation, enable object, change color... actually any action.  
Developer define simple actions and then can compose any chains from them to define simple or complex reactions to events.   

```csharp
[SerializeField] FlexyEvent _jump;
```

Then set any actions to it in inspector or subscribe to Raised event from code

Serve as glue for many packages in **Flexy Framework**

### Available actions in core package

**Delay** - Delays time before next action execution  
**SetEnabled** - Enable/Disable MonoBehavior  
**SetActive** - Activate/Deactivate GameObject    
**PlayAnimClip** - Play anim clip on Animation  
**PlayAnimState** - Play anim state on Animator layer  
**ActionSet** - Compose many actions into one and play them one after another of all at once  

Also, those actions serve as samples for implementing actions specific for your game 

### Default Events

**EventBox_FixedUpdate** - Component that raise event every fixed update  
**EventBox_Update** - Component that raise event every update  
**EventBox_LateUpdate** - Component that raise event every late update  
**EventBox_Lifecycle** - Component that raise events on default unity callbacks Awake, Start, OnEnable, OnDisable, OnDestroy  

[Home](Readme.md) | [Bindings](Bindings.md) | [Game Contexts](GameContexts.md) | [Common Utilities](CommonUtilities.md)