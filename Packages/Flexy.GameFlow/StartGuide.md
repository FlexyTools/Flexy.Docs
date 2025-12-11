![Image Sequence_038_0002](https://github.com/user-attachments/assets/792efb83-33db-4c8c-8e92-2c8e5a363522)
[Flexy.Tools](../README.md) / [Flexy.GameFlow](README.md) / Start Guide

<!-- 
| [Unity Forum](https://discussions.unity.com/t/flexy-assetrefs-v5-0-0-released/1605799) 
| [Asset Store](https://u3d.as/3u78)
-->
# Start Guide

get **Flexy.Template Barley-Breaks** repo and clone it to see sample of state usages
Here is very breaf explanation of work with GameFlow, but better look at Barley-Breaks

## Structure
- Create Entry point - Bootstrapper prefab that will bootstrap Service_GameFlow  
![Img](Src/Guide_Bootstrap.png)
![Img](Src/Guide_Service_GameFlow.png)
- Create FlowLibrary that hold references to all possible states of a game through AssetRefs and set link to library in Service_GameFlow
- Create folder per GameStage like one for Metagame amd one for Coregame
- Add Stage Prefabs to them and states prefabs like MainMenu, Settings, ChooseMap, State_Play, State_Pause, etc.
- Optional Add Test_Scenes for every state to launch right from it with enabled test cases (see Barley-Breaks)  
![Img](Src/Guide_Library.png)
- Set up UI or game logic for every state that will switch it to a new one using Graph.Open()  	
   ```csharp
   public class Window_MainMenu : UIWindowEx
   {
       [Callable]	void	OpenPlayFields		( )		
       {
           this.GetService<Service_GameFlow>().Open<Window_PlayFields>(this); // Possible
       }
       [Callable]	void	OpenSettings		( )		
       {
           Game.UI.Settings.Open(); // But this is way better
       }
   }
   ```
- Drop Bootstrap prefab to a scene and press Play  
![Img](Src/Guide_Scene_Boot.png)
- In Playmode you will see state of GameFlow and your GameContexts  
![Img](Src/Guide_PlayModeState.png)

[Flexy.Tools](../README.md) / [Flexy.GameFlow](README.md) / Start Guide