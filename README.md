Description
===========

L2U-AutoComplete is a package for [Sublime Text 2/3](http://www.sublimetext.com) with support for the L2U API for HRG-LME. It is based on [SublimeLove](https://github.com/szensk/subllualove)

Installation
============

You can install this package through [Package Control](https://sublime.wbond.net/installation), simply use Command Palette: Package Control Install Package -> L2U-AutoComplete.

Alternatively, you can install this package by running the following command in your Packages directory:

    git clone git://github.com/sNaticY/L2U-AutoComplete

Auto completion
------------------------------------------------------------
AssetLoader，L2U 以及 game_object_utils **常用函数**的自动补全

> 常用函数是指在项目的lua代码中经常被调用的一些函数，去除如 L2U.SetGameObjectLocalPosition() 之类的已经在 game_object_utils 中重新封装的函数，避免大家越过 game_object_utils 直接调用，以及去除应用场景较为狭窄的函数，如 ConnectToHost 等普通业务逻辑无需用到的函数，以保持函数列表的整洁，从此以后输入一些关键词即可自动出现列表提供选择

输入 ```find```</br>
L2U.**Find**GameObject</br>
L2U.**Find**GameObjectAsComponent</br>

提供可选参数特殊标识功能，如此处选择第一个则自动补全以下字符

```lua
L2U.FindGameObject( goName, parentGO:1, mustExist:2 )
```

通过TAB键可自动选中下一个参数直接修改即可，齐王上次提到的多态问题，通过可选参数后的数字来标识，如以上示例，parentGO和mustExist都为可选参数，对应以下三种实现

```csharp
public static GameObject FindGameObject( string goName )
public static GameObject FindGameObject( string goName, GameObject parentGO )
public static GameObject FindGameObject( string goName, GameObject parentGO, bool mustExist ) 
```

每个函数只在函数列表中出现一次，大幅度提高在不知道函数名的情况下仅靠关键词来筛选的效率。

Snippets
--------
There are snippets for most built-in Lua functions, some LuaJIT functions, and LuaDoc tags are available in comments. For example. "@param" expands to "-- @param type name desc".

原代码风格已修改至符合LME内部代码风格，修改前：
```lua
for i,v in ipairs(table_name) do
    print(i,v)
end
```

修改后：

```lua
for i, v in ipairs( table_name ) do
    print( i, v )
end
```

Error checking
--------------
By default any Lua file will be run through luac -p and the first encountered error is outlined. The error is displayed in the status bar.

To disable or change this behavior

```json
{
   	"live_parser": true,
   	"live_parser_style": "{dot|circle|outline}",
   	"live_parser_persistent:" false,
   	"luac_path": "luac"
}
```

Auto completion
---------------
Pressing Ctrl+Space in an open Lua file will show the autocompletions for the L2U & gameObject-utils API as well as Lua function snippets.

Those L2U & gameObject-utils functions which are not overloaded (only one possible argument combination), will fill in the argument names for you.
