![Img](Src/GamePreview.webp)

[Flexy.Tools](../../README.md) / [Game Templates](../Readme.md) / [Barley-Breaks](Readme.md) / Project Structure And Assets 

# Project Structure And Assets

## !Game  

All game assets placed under !Game folder because of few factors:

3rd party assets often need to be placed in Aseets and can not be moved so as project grows Assets become more and more trashed  
To separate 3rd party assets from game I have moved it into folder !Game. '!' to make it clear that it is most important part and it is sorted up :)

Game project consist of many high level parts so structure of !Game folder resemble it as close as possible  
Names of inner folder are self explanatory but created in a way that you need to read it with path:

| Folder             | Description                                                                                                     |
|--------------------|-----------------------------------------------------------------------------------------------------------------|
| !Game/!Code        | all game code see [Code Structure](CodeStructureAndFlexyProjectTemplate.md)                                     |
| !Game/Audio        | all global audio assets, mixers, libraries and Service_Audio prefab                                             |
| !Game/Flow         | all assets that define GameFlow (Game States and transitions) based on Flexy.GameFlow package                   | 
| !Game/Maps         | all GameMaps. Scenes with game levels. May be divided by Biomes                                                 |
| !Game/Play         | all assets ToYs that define Core GamePlay (PlayerCamera, PlayerMob, Enemies, Weapons, GameModes, etc.)          |
| !Game/Publish      | all build and publish related assets, build scripts, icons, etc.                                                |
| !Game/Settings     | all GameSettings . URP setting, Input settings, Graphic Tiers Settings, etc.                                    |
| !Game/UIKit        | all UIKit assets and ready to use UI Controls and Widget prefabs. Fonts, UI Sprite Atlases.                     |
| !Game/Boot.scene   | scene game start from. Here actually only Bootstrapper prefab and camera so Unity not complain in the beginning |
| !Game/Asset.refs   | asset pipeline that will collect all assets and put to build for onDemand loading using AssetRefs package       |


## Prefabs and Sources

All folders with assets have Prefabs in it for use in game  
Sources from wich Prefabs are created are placed in Src Subfolder in every folder with prefabs    
This project very light weight so there is no Src folders. You can see this in this Docs repo. **Idea** looks like this:
- !Game/Characters
  - Enemies
    - Swordsmen.prefab
    - Archer.prefab
    - Mortar.prefab
    - Test_Enemies.scene - scene where all enemies placed. Test polygon for use in enemy development, tuning and testing
    - Src
      - Swordsmen folder
      - Archer folder
      - Mortar folder

This way when you open an Enemies folder, you can see exactly what the game uses, but not sources of it  
Something like when you open Garage, you see cars but not wires, and other internals they build from 


## !Game/Flow      

This is the core part of the game. Here is Bootstrapper prefab that launches the game    
It must be placed in every scene you want to start from like Test scenes GameMaps   
Also here is GameFlow prefab that defines Root of Game Flow. Bootstrapper will spawn it first  
And Library stores refs to all States possible of the game  

- Common
- Stage_Boot
- Stage_Meta
- Stage_Core 


## !Game/Publish

Here you can see pipelines to build Release and dev builds  
They consists of Tasks that do anything you want. 
Here you can find only builtin ones and one sample Task for setting collected maps to scene list before build 

To build game select BuildPlayer SO and press run :)  
Or you can Build from Build Settings but then version info will not be updated because only Asset.refs SO has Run On Build Preprocess Task 

<br/>

[Flexy.Tools](../../README.md) / [Game Templates](../Readme.md) / [Barley-Breaks](Readme.md) / Project Structure And Assets