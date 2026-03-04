![Img](../Cover.webp)

[Flexy.Tools](../../Readme.md) / [Flexy.Bricks\ToYs](../Readme.md) / [Project Structure](Readme.md) / !Code

# !Code

!Code have similar structure to !Game  
but structured closer to how player approach the game

| Folder           | Description                                                                    |
|------------------|--------------------------------------------------------------------------------|
| !Code/Boot       | game boot Stage and All boot states                                            |
| !Code/Menu       | game menu Stage and All menu states and services most of metagame code is here |
| !Game/Play       | game play Stage and All play states and services most od coregame code is here |
| !Game/Overlays   | overlay UI, Error popups, debug info, ingame console, etc.                     | 
|                  |                                                                                |
| !Game/Common     | Common Services and game utils                                                 |
| !Game/Settings   | All code related to Game settings. UI, services, etc                           |
| !Game/Build      | All game build scripts and connection to CI                                    |

Every game State try hard to be implemented inside only one .cs file with corresponding name
This way game is easy to develop, support, and reason about

## Globals

Project uses Globals.cs 
here you will find global C# usings
and global name conflict resolutions

also it is possible to replace Static class in project with Custom one
like make all Debug.* actually access your custom class instead of Unity one 


## Facades and Extensions

One of the most important class in project is Facades.cs
It define game Facade that allow almost in any part of a game to  
access game services of that part with simple line of code starting from `Game.` 

    public struct	Facade_Coregame : ICachedContext
    {
        public  GameContext         Ctx         { get; set; }
        public  Component           CallSource  { get; set; }
    
        public  GameMode            Mode        => Ctx.GetService<GameMode>();
        public  MapContext          Map         => Ctx.GetService<MapContext>();
        public  Facade_Flow         Flow        => new(Ctx.GetService<Stage_Play>());
        public  Facade_CoreStates   UI          => new(CallSource.GetComponentInParent<State>());
        public  Service_Audio       Audio       => Ctx.GetService<Service_Audio>();
        public  Facade_GameSettings Settings;
    
        public void Recache()
        {
            Settings = new( Ctx.GetService<Service_GameSettings>() );
        }
    }

You can see in every game state lines like `Game.UI.Settings.Open();` or `Game.Flow.PlayMap(_mapDocks, _gameMode_Roam);`

Project have 2 facades one for Menu Stage and one for Play Stage
When you type Game. in menu class you access Menu facade and when you type Game. in play class you access Play facade

In facade you can find all services of GameStage and Ide will help you find what you need and what actually available in game what game consists of

Game property and Correct Facade available because of Exs.cs. Here you will find classes that extend common Base Types used in Game and add Game Property to it.  

    public abstract class	MonoBehEx: MonoBehaviour				
    {
        public	Facade_Coregame	        _game; 
        public	ref Facade_Coregame     Game       => ref _game.GetCached( this );
        public	Stage_Play              GameStage  => (Stage_Play)gameObject.GetService<GameStage>(); 
    }

By default Facade cache only call Source and GameContext but for optimisation purposes there is easy to cache more services
like cache GameSettings so acessing Game.Settings.Input.MouseSensitivity will be cheap operation 

<br>

[Flexy.Tools](../../Readme.md) / [Flexy.Bricks\ToYs](../Readme.md) / [Project Structure](Readme.md) / !Code