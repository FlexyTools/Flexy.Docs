**Flexy.AssetRefs Extension Points**
==================== 

[Index](README.md) | [Start Guide](StartGuide.md) | [Pipeline](Pipeline.md) | [FAQ](FAQ.md)

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

## AssetLoader

**AssetLoader** is class responsible for loading assets/scenes in Editor / PlayMode / Build  
In Editor AssetLoader loads assets using AssetDatabase  
In PlayMode with RuntimeBehavior enabled or in Build it uses runtime implementation that you **can override!**  
To enable RuntimeBehavior go **Tools/Flexy/AssetRefs/AssetLoader/Enable Runtime Behavior** 

**Default** AssetLoader is AssetLoader_Resources that loads Assets using Resources Api  
But you **do not** need to place your assets into Resources folder! Thanks to [**Pipeline**](Pipeline.md)  

## One more thing

Async methods of asset loader return specific Task structure that have few useful properties

```csharp
var loadBossTask = _bossPrefab.LoadAssetAsync();

// You can access loading progress, check IsDone and IsSuccess
while (!loadBossTask.IsDone)
{
    progressLabel.text = loadBossTask.Progress.ToString();
    await UniTask.NextFrame();
}

if (loadBossTask.IsSuccess)
    SpawnBoss( loadBossTask.GetResult() );
```

Same with Scene Loading but scene specific

```csharp
var loadBossRoomTask = _bossRoom.LoadSceneAsync(this.gameObject, new LoadSceneTask.Parameters { ActivateOnLoad = false });

// You can access loading progress, check IsDone, get scene struct, WaitForSceneLoadStart and AllowSceneActivation

await loadBossRoomTask.WaitForSceneLoadStart();

// after scene started loading scene struct is available and we can use any scene related api before scne loading finishes
var scene = loadBossRoomTask.Scene;

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

**Warning**  
You can not **store** LoadTasks! They rented from pool and will be returned to pool after 10 frames once loading done 

[Index](README.md) | [Start Guide](StartGuide.md) | [Pipeline](Pipeline.md) | [FAQ](FAQ.md)