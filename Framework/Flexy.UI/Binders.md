![Img](Src/Cover.webp)

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / [Flexy.UI](Readme.md) / Binders

# Binders 

Ready to use binders for UI elements 
Every binder is small MonoBeh with very small and specific bind code
You will easily create our oun for specific needs of your project

| Class                          | Description                                                                        |  
|:-------------------------------|:-----------------------------------------------------------------------------------|
| Binder_Text                    | Bind String property to TMP_Text.text UGui                                         |
| Binder_Image                   | Bind Sprite property to Image.sprite                                               |  
| Binder_RawImage                | Bind Texture2D property to RawImage.texture                                        |
| Binder_GraphicColor            | Bind color property to Graphic.color                                               |
| Binder_Slider                  | Bind Single property to Slider.value                                               |
| Binder_ButtonEnabled           | Bind Boolean property to Button.interactable                                       |
| Binder_BehaviourEnabledBoolean | Bind Boolean property to `true` and `false` behaviour.enabled                      |
| Rebinder_Periodic              | Rebind all binders on GameObject with period                                       |


Special Collections binding solution to bind collection of items with ease (see any [GameTemplate](../../GameTemplates/Readme.md	) for usage sample) 

| Class                          | Description                                                                        |  
|:-------------------------------|:-----------------------------------------------------------------------------------|
| Binder_Collection              | Bind special Collection struct to UI list of items (spawn Prefab per item)         |
| BindMedium                     | Special middle layer behaviour to bind to dynamically created typed objects        |
| Collection                     | Collection struct for Binder_Collection that carry IEnumrable and useful callbacks |


<br>

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / [Flexy.UI](Readme.md) / Binders