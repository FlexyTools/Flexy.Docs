**Flexy.AssetRefs Start Guide**
==================== 

[Index](Readme.md) | [Extension Points](ExtensionPoints.md) | [Pipeline](Pipeline.md) | [FAQ](FAQ.md)

Ref Types
--------

- AssetRef
- SceneRef

They both are simple ids of assets. [Someone](ExtensionPoints.md) need to be able to load actual assets from this ids
Internally they store asset GUID and InternalId same way as UnityEditor do it

You define **AssetRefs** and **SceneRefs** anywhere you want and they show up in inspector as regular unity object references    

```csharp
[SerializeField]    AssetRef<Sprite>        _icon;
[SerializeField]    AssetRef<GameObject>    _prefab;
[SerializeField]    SceneRef                _map_01;
```

Then you load those using provided [LoadingMethods](ExtensionPoints.md) or using your own

Additionally SceneRef has static Method to load DummyScene - it will create new scene with Camera and AudioListener in it
Additional DummyScene URP will init correct scene for URP render pipeline

Note: By default SceneRef load Scenes Additively so loading scene dont mean unload everything else  
To load single and unload everything else you must pass parameter explicitly  
To read more about additive vs single scene loading in Unity read [Unity Docs](https://docs.unity3d.com/6000.0/Documentation/ScriptReference/SceneManagement.LoadSceneMode.Additive.html)  

```csharp
await SceneRef.LoadDummySceneAsync();

// or

var dummySceneLoadTask = SceneRef.LoadDummySceneAsync();
```

[Index](Readme.md) | [Extension Points](ExtensionPoints.md) | [Pipeline](Pipeline.md) | [FAQ](FAQ.md)
