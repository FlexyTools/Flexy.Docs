![Img](https://github.com/user-attachments/assets/ebb66e52-7b73-46fd-95ab-3585a9a1180e)

# Flexy.GameSettings

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.GameSettings

<!--
[Unity Forum](https://discussions.unity.com/t/flexy-assetrefs-v5-0-0-released/1605799)
| [Asset Store](https://u3d.as/3u78)
| 
-->

Easily store game settings for settings window or any other needs with just one line per setting.  
By default it uses PlayerPrefs to store settings, but you can provide your own storage.  
Easy extensible by defining settings tab classes.

[Github](https://github.com/FlexyTools/Flexy.GameSettings) 
| [Unity Forum](https://discussions.unity.com/t/flexy-gamesettings-free-easily-store-game-settings-with-just-one-line-per-setting/1700923)
| [AssetStore](https://u3d.as/3LKx)

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

### Note: 
Each setting implemented as struct so dont cache setting itself, cache SettingTab_Class  
Service_GameSettings is MonoBehaviour so GameSettings static acees dont exists. If you need it in singleton form, you need to create it like this:
```csharp
public class GameSettings : Service_GameSettings
{
	private static	GameSettings	_ref = null!;
	private void	Awake	( ) =>	_ref = this;
	
	public static T Get<T>	( ) where T:GameSettingsTab, new() => ((Service_GameSettings)_ref).Get<T>();
}
``` 
And place on some GlobalManagers GameObject in your project 

## One more thing

PlayerPrefs can not be read from MonoBehaviour constructor  
So if you use Setting struct directly on MonoBehaviour you need to readLater: true
```csharp
private BooleanSetting _eulaAccepted = new("Boot_EulaAccepted", false, readLater:true);
```
and later in Enable, Awake or something call Read() to read and cache it for the first time
```csharp
_eulaAccepted.Read();
```

## Fully featured usage sample

Flexy Template [Barley-Break](../../GameTemplates/Barley-Breaks/Readme.md)  

## Install

Open Unity Package Manager   
Add package from git URL: https://github.com/FlexyTools/Flexy.GameSettings

### Have Fun

<br/>

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / Flexy.GameSettings