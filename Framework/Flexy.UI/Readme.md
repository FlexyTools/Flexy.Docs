![Img](Src/Cover.webp)

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.UI

# Flexy.UI

**A production-proven UI manager for clean and scalable Unity UI**

Stop hardcoding UI logic into MonoBehaviours  
Build UI Windows, Loaders, and Popups with clear structure and minimal code

[GitHub](https://github.com/FlexyTools/Flexy.UI)

[Start Guide](StartGuide.md) | [Binders](Binders.md) | [Extra](Extra.md) | [Misc](Misc.md) | [Showcase (Template project)](../../GameTemplates/Readme.md)


## What Is Flexy.UI

Flexy.UI is a UI architecture framework for Unity  
It helps you build and maintain complex UI without turning your codebase into tightly coupled MonoBehaviours

Flexy.UI separates UI logic, presentation, and lifecycle responsibilities so your UI remains readable, testable, and easy to extend as the project grows

It scales from small prototypes to long-term production projects where UI complexity increases over time

The architecture has been refined in real production projects since 2012


## Why Use Flexy.UI

As Unity projects grow, UI code often becomes:
- Hard to reason about
- Difficult to test in isolation
- Risky to refactor
- Expensive to extend with new features

Flexy.UI solves this by providing:
- A clear separation between UI logic and Unity components
- Explicit UI intent expressed directly in code
- Predictable UI initialization inside a valid runtime context

This allows you to change, reuse, and extend UI without breaking unrelated systems


## Is This for You?

**Flexy.UI is a good fit if:**
- Your project has grown beyond a simple prototype
- You want UI logic that stays readable over time
- You reuse UI panels across multiple screens
- UI artists and UI developers work independently
- You care about architecture, testability, and long-term maintainability


**This asset may not be a good fit if:**
- You prefer to hardcode all UI control logic directly in MonoBehaviours
- You want a visual UI builder without coding


## Key Features

- Every UIWindow or Popup is a separate state
- Clear separation between MonoBehaviour and UIView
- UI intent explicitly expressed in code
- Two-way communication with Binders
- Easy binding of collections with custom UI items
- Simple creation of reusable UI modules
- Develop and test UI Windows in isolation
- Near-instant window opening when Domain Reload is disabled
- UI initialization always happens inside a valid runtime context
- Created for Unity uGui but can be adopted to any UI Framework 

When entering PlayMode from UIWindow, the runtime environment is already initialized  
This ensures correct execution even inside `Awake`


## How It Fits Into Your Project

Flexy.UI is built on top of Flexy.GameFlow and Flexy.Core  
These provide:
- Game contexts
- Controlled lifecycle stages
- Safe initialization order

This guarantees that UI logic always runs after 

See:
- [Flexy.Core](../Flexy.Core/Readme.md) for game contexts
- [Flexy.GameFlow](../Flexy.GameFlow/Readme.md) for lifecycle and stages


[Start Guide](StartGuide.md) | [Binders](Binders.md) | [Extra](Extra.md) | [Misc](Misc.md) | [Showcase(Template project)](../../GameTemplates/Readme.md)
The Showcase is provided as a **template project**, not isolated demo scenes  
You can open it, build it, and install a fully working application  
This allows real-world testing instead of artificial examples


## Technical Details

- Modern C# (C# 10)
- Designed to work with Domain Reload disabled
- Tested with Unity 2022.3 up to Unity 6.3
- Depends on Flexy.GameFlow and Unity uGUI
- Render pipeline agnostic
- Platform agnostic  

<br/>

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.UI
