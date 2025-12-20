![Cover](Src/Cover.webp)

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.GameFlow


# Flexy.Core

Core package of **Flexy Framework** that every other package depends on  

[Github](https://github.com/FlexyTools/Flexy.Core)
<!--| [Unity Forum](https://discussions.unity.com/t/flexy-gamesettings-free-easily-store-game-settings-with-just-one-line-per-setting/1700923)
| [AssetStore](https://u3d.as/3LKx)  
[Scripting Api](ScriptingApi/Readme.md)
| [Showcase(Template project)](../../GameTemplates/Barley-Breaks/Readme.md) -->

## **Content**


### [GameContext](GameContext.md)
Flexy way to think about game dependencies and their composition. **Context based**  
You can think like DI Container but more clear and tied to scenes and GameObjects instead of live in thin air

### [Bindings](Bindings.md)
Core of Flexy.Binding system  
This is one of basis parts of **Flexy.Bricks** **MC-VMV** pattern for binding View to ViewModel   
It is here because it can be used not only in UI but in coregame too

### [Actions](Actions.md)
Universal and composable system to do action in response to event:  
play sfx, show vfx, play animation, enable object, change color... actually any action.  

### [Common Utilities](CommonUtilities.md)
Small set of very often and common used utilities


## **Key Strengths**

- It is Open Source :)
- Customisable: 
  - mostly consists of small types that dont need customization 
  - GameContext have customization points
- Production-Proven: used in released games since 2019


## **Technical details**

- UniTask based async init 
- Native C# Nullability annotations
- C# 10
- Fast Enter Play Mode support
