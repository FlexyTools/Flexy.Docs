![Img](https://github.com/user-attachments/assets/ebb66e52-7b73-46fd-95ab-3585a9a1180e)

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / [How To](Readme.md) / Add State To Game


# How To: Add State To Game

## from Imported Package

### Simple fast way

- Go to your Flow library  
- If it works in any grab mode
  - Clone it
  - Make it no grab
  - Clear states  
  - Add new library as dependency to cloned one
- Add new **state/window** from package to library with no grab mode
- Duplicate some button in existing ui Window 
- Remove ButtonClickBinder if it was there
- Add `ButtonClickOpenWibdow` component and set `WindowToOpen` to new imported **state/window** 
  
![Img](Src/CloneLibrary_01.png)  
![Img](Src/CloneLibrary_02.png)
![Img](Src/AddButtonClickOpenWindow.png)

- You are **DONE** enter play mode and open added **state/window** :)


<br/>

### Have Fun

<br/>

[Flexy.Tools](../../Readme.md) / [Framework](../Readme.md) / [How To](Readme.md) / Add State To Game