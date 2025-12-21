![Img](Src/Binder.webp)

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.Core](../Readme.md) / [Scripting Api](Readme.md) / Binder

# Binder

## Description

Inherits from: MonoBehaviour

Abstract class to implement Binders  

## Methods

| Method                  | Description                                                                                          |  
|-------------------------|------------------------------------------------------------------------------------------------------|
| Rebind                  | Mark component as Bind ready and rebind all currently awaiting binders                               |
| Bind `abstract`         | Mark component as bind unready to delay Bind operation on binders until component will be ready      |
|                         |                                                                                                      |
| Init                    | Bind and save Delegate to `action` or `func` field with `require` target memeber of ignore is absent |
| ReportMissedTargetError | Convenient method to report Warning on missing target                                                |


<br/>

[Flexy.Tools](../../../Readme.md) / [Framework](../../Readme.md) / [Flexy.Core](../Readme.md) / [Scripting Api](Readme.md) / Binder

