# Log Filter

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.Log](../Readme.md) / [Scripting Api](Readme.md) / Log Filter


## Description


Additional filtering of Enabled Logs. Per file or member.  
Filtering applied only to log that is enabled in ProjectSettings or in `Debug.unityLogger.filterLogType`

## Properties

| Property      | Description                                                                                                     |  
|---------------|-----------------------------------------------------------------------------------------------------------------|
| FilterFrom    | Topmost LogType to start filtering from. Default in editor is dont filter, in build is filter warnings and logs |


## Methods

| Method               | Description                                                   |  
|----------------------|---------------------------------------------------------------|
| IsAllowed            | Override to implement filtering logic (allow or disallow log) |
|                      |                                                               |  
| AllowLogOnPath       | Override to add path to allowed                               |
| DisallowLogOnPath    | Override to remove path from allowed                          |


## Examples

```CSharp
Debug.Filter?.AllowLogOnPath    ("./PathToFile.cs", "MethodName");
Debug.Filter?.DisallowLogOnPath ("./PathToFile.cs", "MethodName");

Debug.Filter?.AllowLogOnPath    ("./Assets/!Game/!Code/Settings/Window_GameSettings.cs", "FixedUpdate");
Debug.Filter?.DisallowLogOnPath ("./Assets/!Game/!Code/Settings/Window_GameSettings.cs", "FixedUpdate");
Debug.Filter?.AllowLogOnPath    ("./Assets/!Game/!Code/Settings/Window_GameSettings.cs", "Update");
Debug.Filter?.DisallowLogOnPath ("./Assets/!Game/!Code/Settings/Window_GameSettings.cs", "Update");
		
Debug.Filter?.AllowLogOnPath    ("./Assets/!Game/!Code/Settings/Window_GameSettings.cs");
Debug.Filter?.DisallowLogOnPath ("./Assets/!Game/!Code/Settings/Window_GameSettings.cs");

Debug.Filter?.AllowLogOnPath    ("./Packages/fun.flexy.core/Runtime/GameContexts/GameContext.cs");
Debug.Filter?.AllowLogOnPath    ("./Packages/fun.flexy.gameflow/Runtime/GameFlowBootstrap.cs");
```

<br/>

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.Log](../Readme.md) / [Scripting Api](Readme.md) / Log Filter