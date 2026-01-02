**Flexy.AssetRefs Extension Points**
==================== 

[Index](Readme.md) | [Start Guide](StartGuide.md) | [Pipeline](Pipeline.md) | [FAQ](FAQ.md)

## LoadExtensions

They are **C# Extension methods** that can load assets by refs.  
You can write your own for your project needs (e.g. load using Addressables assetRef.ToString() fit addressables expectations)

```csharp
using Flexy.AssetRefs.LoadExtensions;

...

private void PopulateIcon ( )
{
    _image.sprite = _icon.LoadAssetSync();
}

private async UniTask PopulateIconAsync ( )
{
    _image.sprite = await _icon.LoadAssetAsync();
}

private async UniTask LoadSceneAsync ( )
{
    await _map_01.LoadSceneAsync();
}
```    
  
Default implementation directly uses AssetLoader Api to load assets  

## AssetLoader / SceneLoader

**AssetLoader and SceneLoader** is classes responsible for loading assets/scenes in Editor / PlayMode / Build  
In Editor they load assets using AssetDatabase  
In PlayMode with RuntimeBehavior enabled or in Build using runtime implementation that you **can override!**  
To enable RuntimeBehavior go **Tools/Flexy/AssetRefs/Enable Runtime Behavior** 

**Default** AssetLoader/SceneLoader is AssetLoader_Resources and SceneLoader_Resources. They load using Resources Api  
But you **do not** need to place your assets into Resources folder or add Scenes to BuildSettings! Thanks to [**Pipeline**](Pipeline.md)  

## One more thing

Async methods of SceneLoader return specific Task class that have few useful properties

```csharp
var loadBossRoomTask = _bossRoom.LoadSceneAsync(this.gameObject, new LoadSceneTask.Parameters { AllowActivation = false });

// You can access loading progress, check IsDone, get scene struct, WaitForSceneLoadStart and AllowSceneActivation

await loadBossRoomTask.WaitForSceneLoadStart();

// after scene started loading scene struct is available and we can use any scene related api before scne loading finishes
var scene = loadBossRoomTask.Scene;

// Also you can add LoadSteps to so some sort of initilisation after scene loading

loadBossRoomTask.AddLoadStep(async (task) =>
{
    await UniTask.Delay(100);
	// do some initilisation here may be generate dynamic scene content, bake meshes or imposters etc.
});
// All steps happens before LoadTask return Done

while (!loadBossRoomTask.IsDone)
{
    progressLabel.text = loadBossTask.Progress.ToString();
    await UniTask.NextFrame();
}

await UniTask.Delay(10_000); 

loadBossTask.AllowSceneActivation();

await loadBossTask; // wait for activation

// Scene fully loaded and activated
```

 You can add LoadSteps globally to not add on call side every time
```csharp
LoadSceneTask.NewLoadSceneTaskStarted += (task) =>
{
    task.AddLoadStep(async (task) =>
    {
        await UniTask.Delay(100);
        // do some initilisation here may be generate dynamic scene content, bake meshes or imposters etc.
    }
}
```

[Index](Readme.md) | [Start Guide](StartGuide.md) | [Pipeline](Pipeline.md) | [FAQ](FAQ.md)