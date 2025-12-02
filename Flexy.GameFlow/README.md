![Image Sequence_038_0002](https://github.com/user-attachments/assets/792efb83-33db-4c8c-8e92-2c8e5a363522)
[Docs and Use Cases](Documentation.md)
| [FAQ](FAQ.md)

<!-- 
| [Unity Forum](https://discussions.unity.com/t/flexy-assetrefs-v5-0-0-released/1605799) 
| [Asset Store](https://u3d.as/3u78)
-->
# **Flexy.GameFlow**

Core package of **Flexy Framework** that every other package depends on  


## **Content**

### [Bindings](Bindings.md)
Core of Flexy.Binding system  
This is one of basis parts of **Flexy.Bricks** **MC-VMV** pattern for binding View to ViewModel   
It is here because it can be used not only in UI but in coregame too

### [Actions](Actions.md)
Universal and composable system to do action in response to event:  
play sfx, show vfx, play animation, enable object, change color... actually any action.  

### [Common Utilities](CommonUtilities.md)
Small set of very often and common used utilities

### [GameContext](GameContext.md)
Flexy way to think about game dependencies and their composition. **Context based**


## **Key Strengths**

- It is Open Source :)
- Customisable: 
  - mostly consists of small types that dont need customization 
  - GameContext have customization points
- Production-Proven: used in released games since 2019

See [Docs and Use Cases](Documentation.md) for usage samples   


## **Technical details**

- Ref is struct with 2 fields: Hash128 & Int64
- C# Extensions based load methods
- AssetLoader interface is 5 virtual methods
- Sync loading 
- UniTask based async loading 
- Native C# Nullability annotations
- C# 10
- Fast Enter Play Mode support


This package uses cropped version of UniTask package under MIT License  
See [Third-Party Notices.md](ThirdPartyNotices.md) file in package for details  
Full and latest version can be installed alongside this package without issues  