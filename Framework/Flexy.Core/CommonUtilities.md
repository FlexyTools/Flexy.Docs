# Flexy.Core Common Utilities 

[Home](Readme.md) | [Actions](Actions.md) | [Bindings](Bindings.md) | [Game Contexts](GameContexts.md)


## Extensions

**Object.OrNull()** - Make C# null check operators work on Unity objects  
**Object.IsAlive()** - Check object alive in better way than cast to bool  
**Object.Destroy()** - Call destroy as member function  

**GameObject.ClearDirty()** - Helper for Prefab deactivating and spawning deactivated then clear dirty on prefab

## Services

**Setup_InvariantCulture** - Setup invariant culture for all threads so Single.Parse works on all devices the same way
**Setup_TaskExceptionsLogger** - Wire unobserved task exceptions to unity exception logger  
**Service_UGSIntegration** - Initialize UnityServices in Ordered way (basement for other unity service packages)

## Misc

**Rng** - Squirrel Random Number Generator implementation. State free noise based generator  
**LocString** - core ValueObject struct for string localisation  

**PoymorphicAttribute** - draw serializable reference field as polymorphic class  
**RoDict, RoList** - True Read only struct wrapper for readonly access without ability to cast back and without lost of perfomance  
**RuntimeInspector** - draw object runtime state in inspector by decorating method with attribute  
**SpanList, TempList** - temp lists for temporary collection in algorithms without GC allocation  


[Home](Readme.md) | [Actions](Actions.md) | [Bindings](Bindings.md) | [Game Contexts](GameContexts.md)