![Img](Src/Cover.webp)

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.Log

# Flexy.Log

**Structured, Customizable and Allocation free   
drop in replacement logging for Unity**  

Exted logs in your projects  
Easy replace logs in entire project with one line of code  
And make them Reach, Filterable and Allocation free on string interpolation


[Forum](https://discussions.unity.com/t/flexy/1715000) | [AssetStore](https://u3d.as/3R6j) | [Scripting Api](ScriptingApi/Readme.md)


## Key Benefits

- Almost free on disabled logs
- Very low perf impact on enabled log filtering
- Enable/Disable logs in files on demand without rebuild/redeploy
- Customizable log formatting


## How It Works

- Reroute all calls to `Debug.Log` with `Flexy.Log.Debug` and handle logging in Allocation Free way


## How To use

- Enable C#10 support in project settings (add `-langversion:10` to additional compiler arguments)
- Add line `global using Debug = Flexy.Log.Debug;` in one cs file in project to reroute calls  
- Set log level as usual: `Debug.unityLogger.filterLogType = LogType.Warning;`
- Set log filtering level by: `Debug.Filter!.FilterFrom = LogType.Warning;`
- Allow logs from file for filter by
  - `Debug.Filter?.AllowLogOnPath ("./PathToFile.cs", "MethodName");`
  - `Debug.Filter?.AllowLogOnPath ("./Assets/!Game/!Code/Settings/Window_GameSettings.cs", "Update");`
  - `Debug.Filter?.AllowLogOnPath ("./Packages/fun.flexy.core/Runtime/GameContexts/GameContext.cs");` 

## Additional

UnityEngine.LogFormat always allocates!  
To prohibit this, you can remove log format methods by adding define FLEXY_LOG__DISABLE_LOG_FORMAT to project settings  
Then fix errors in all places where you use Debug.LogFormat


## Technical Details

- Uses modern C# features (C# 10)
- Tested with Unity 2022.3 through Unity 6.3

<br/>

### Have Fun :)

<br/>

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.Log
