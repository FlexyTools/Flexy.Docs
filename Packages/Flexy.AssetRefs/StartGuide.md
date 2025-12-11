**Flexy.AssetRefs Start Guide**
==================== 

[Index](README.md) | [Extension Points](ExtensionPoints.md) | [Pipeline](Pipeline.md) | [FAQ](FAQ.md)

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

```csharp
await SceneRef.LoadDummySceneAsync();

// or

var dummySceneLoadTask = SceneRef.LoadDummySceneAsync();
```

[Index](README.md) | [Extension Points](ExtensionPoints.md) | [Pipeline](Pipeline.md) | [FAQ](FAQ.md)
