**Flexy.AssetRefs Pipeline**
==================== 

[Index](README.md) | [Extension Points](ExtensionPoints.md) | [Start Guide](StartGuide.md) | [FAQ](FAQ.md)


**Pipeline** is SciptableObject with list of **Tasks** that collects Refs and make sure they can be loaded in runtime  
this is where **magic** happens :) 

You need to add at least one pipeline asset to project through Create Menu > Flexy > AssetRefs > Pipeline   
Simple working pipeline must consist of Tasks (in order):

- **RunOnBuildPreprocess** - it will launch this pipeline as PreBuild step (only if it first task)
- Few Tasks that collects refs to objects
  - **AddRefsDirect** - add references to objects directly (how it useful - later in doc)  
  - **AddRefsFromDirectory** - will collect all assets of chosen type (sprite,prefab...) form directory with subdirectories
- **ResourcesPopulateRefs** - will make collected refs available for loading in runtime (without touching source assets) 

With **correct** pipeline your refs will work in editor and in build seamlessly!

What is Correct pipeline
--------

Correct pipeline is such pipeline that collects refs to all assets you want to load in runtime

**How to make One?**

One way is:

```
Add all sprite refs           using AddRefsFromDirectory
Add all map scene refs        using AddRefsFromDirectory
Add all Units Prefab refs     using AddRefsFromDirectory
Add all UIWindow Prefab refs  using AddRefsFromDirectory
Add specific assets           using AddRefsDirect

And you are ready to go
```

Another way is (for case you have Game Design Data as set of ScriptableObject's):

```
Place all references to assets/scenes into GdData as AssetRefs/SceneRefs
Implement IAssetRefsSource on RootGdData ScriptableObject 
Add ref to RootGdData using AddRefsDirect
Load OnDemand assets/scenes from GdData ojects refs

And you are ready to go
```

For bigger project second way is preferable because your GameDesigners will create new stuff, 
will set up new refs to sprites, prefabs, scenes, etc. and everything will work without any additional setup 
because pipeline will collect all refs from GdData on prebuild

To collect AssetRefs and SceneRefs from fields on GdData objects we provide ready to use method **RefsCollector.CollectRefsDeep**
that you can use in your implementation of IAssetRefsSource

From Experience - Big Production Projects often have pipeline structure like this:

```
AddRefsDirect - for few very specific objects
AddRefsDirect - for RootGdData          object that implements IAssetRefsSource
AddRefsDirect - for UIWindowsLibrary    object that implements IAssetRefsSource
```

Additionally you can write project specific PipelineTasks that collect Refs your way or do actually whatever you want  
You can use Pipelines to do various automation tasks. Collecting AssetRefs is just specific use case.

Pipeline Task **ResourcesPopulateRefs** will create specific assets in path Assets/Resources/Fun.Flexy/AssetRefs/  
they need to wire up loading of collected assets from Unity Resources Api and this path can be ignored in Source Control 


[Index](README.md) | [Extension Points](ExtensionPoints.md) | [Start Guide](StartGuide.md) | [FAQ](FAQ.md)