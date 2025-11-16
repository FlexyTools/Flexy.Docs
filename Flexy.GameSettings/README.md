![Image Sequence_038_0002](https://github.com/user-attachments/assets/792efb83-33db-4c8c-8e92-2c8e5a363522)

# **Flexy.GameSettings**

[Unity Forum](https://discussions.unity.com/t/flexy-assetrefs-v5-0-0-released/1605799)
| [Asset Store](https://u3d.as/3u78)
| [Github](https://github.com/FlexyTools/Flexy.GameSettings)

Easily store game settings for settings window or any other needs with just one line per setting.  
By default it uses PlayerPrefs to store settings, but you can provide your own storage.  
Easy extensible by defining settings tab classes.

Supports:
- String setting
- Single setting
- Int32 setting
- Bool setting
- Enum32 setting
- Color setting

You can create your own setting type by using Enum32Setting as a template    

No need any additional initialisation it is initialized on first access.  
Super simple and elegant code

Define settings like this:
```csharp
public class SettingsTab_Audio : GameSettingsTab
{
    public SingleSetting    SoundVolume    = new( "AudioSettingsTab_SoundVolume", 1 );
    public SingleSetting    SfxVolume      = new( "AudioSettingsTab_SfxVolume", 1 );
}
```
and use like this:
```csharp
var volume = GameSettings.Get<SettingsTab_Audio>().SfxVolume;
GameSettings.Get<SettingsTab_Audio>().SfxVolume.Set(0.5f);
```
or like this:
```csharp
var audioSettings   = GameSettings.Get<SettingsTab_Audio>();
var volume          = audioSettings.SfxVolume;
audioSettings.SfxVolume.Set(0.5f);
```

or this:
```csharp
var audioSettings = GameSettings.Get<SettingsTab_Audio>();
audioSettings.SoundVolume.Changed += UpdateVolume;
```

Note: Each setting implemented as struct so dont cache setting itself, cache SettingTab_Class 

## One more thing

PlayerPrefs can not be read from MonoBehavior constructor  
So if you use it directly you need to readLater: true
```csharp
private BooleanSetting _eulaAccepted = new("Boot_EulaAccepted", false, readLater:true);
```
and later in Enable, Awake or something call Read() to read and cache it for the first time
```csharp
_eulaAccepted.Read();
```

## Fully featured usage sample

Flexy-Template [Barley-Break](https://github.com/FlexyTools/Flexy-Templates.BarleyBreak)  

## Install

From Unity Package Manager   
Add package from git URL: https://github.com/FlexyTools/Flexy.GameSettings

### Have Fun