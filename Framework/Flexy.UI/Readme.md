![Img](Src/Cover.webp)

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.UI


# Flexy.UI

**A production-proven UI architecture framework for Unity**


Stop hardcoding UI control logic into MonoBehaviours

[GitHub](https://github.com/FlexyTools/Flexy.UI)<!-- | [Unity Forum](https://discussions.unity.com/t/a/1700923)
| [AssetStore](https://u3d.as/3LKx) -->

[Start Guide](StartGuide.md) | [Binders](Binders.md) | [Extra](Extra.md) | [Misc](Misc.md) | [Showcase(Template project)](../../GameTemplates/Readme.md)

Flexy.UI allows you to build UI Windows, Loaders, and Popups with clean, minimal code using a refined MC-VMV architecture  
It is scales from short-lived prototypes to long-term projects where UI complexity grows over time

The architecture has been refined in real production projects since 2012


## Why Flexy.UI

As projects grow, UI code often becomes tightly coupled, difficult to test, and expensive to change      
Flexy.UI addresses this by providing a clear architectural foundation that keeps UI logic readable, modular, and maintainable as complexity increases

Flexy.UI focuses on:
- Clear separation of responsibilities
- Explicit UI intent in code
- Safe UI initialization inside a valid runtime context


## Is This for You?

**Flexy.UI is a good fit if:**
- Your project has grown beyond a simple prototype
- You reuse UI panels across multiple windows
- UI artists and UI developers work separately
- You care about clean architecture, testability, and long-term maintainability

Flexy.UI is an architectural foundation and is intended to be adopted early in a project

**This asset may not be a good fit if:**
- You prefer to hardcode every UI control directly into scripts


## Key Features

- Clear separation between MonoBehaviour and UIView
- UI intent clearly expressed in code
- Two-way communication between Binder and MonoBehaviour
- Easy binding of collections with custom UI items
- Simple creation of reusable UI modules
- Develop and test UI Windows in isolation
- Near-instant window opening when Domain Reload is disabled (even in mid-size projects)
- UI is initialized in a fully valid runtime context, allowing correct execution from `Awake`

When a window is opened, the entire game context is already initialized.  
This ensures that even `Awake` calls execute inside the correct runtime environment.

See:
- [Flexy.Core](../Flexy.Core/Readme.md) for Game Contexts
- [Flexy.GameFlow](../Flexy.GameFlow/Readme.md) for Game Stages and lifecycle control


[Start Guide](StartGuide.md) | [Binders](Binders.md) | [Extra](Extra.md) | [Misc](Misc.md) | [Showcase(Template project)](../../GameTemplates/Readme.md)  
The Showcase is provided as a **template project**, not isolated demo scenes    
You can open it, build it, and install a working application for real-world testing  


## Technical Details

- Modern C# (C# 10)
- Designed to work with Domain Reload disabled
- Tested with Unity 2022.3 up to Unity 6.3
- Depends on Flexy.GameFlow and Unity uGUI
- Render pipeline agnostic
- Platform agnostic (shipped on Windows, macOS, Linux, Android, iOS)

<br/>

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.UI
