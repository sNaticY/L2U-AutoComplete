Description
===========

L2U-AutoComplete is a package for [Sublime Text 2/3](http://www.sublimetext.com) with support for the L2U API for HRG-LME. It is based on [SublimeLove](https://github.com/szensk/subllualove)

Installation
============

You can install this package through [Package Control](https://sublime.wbond.net/installation), simply use Command Palette: Package Control Install Package -> L2U-AutoComplete.

Alternatively, you can install this package by running the following command in your Packages directory:

    git clone git://github.com/sNaticY/L2U-AutoComplete

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

in Lua Love > User Settings.

Snippets
--------
There are snippets for most built-in Lua functions, some LuaJIT functions, and LuaDoc tags are available in comments. For example. "@param" expands to "-- @param type name desc".

Auto completion
---------------
Pressing Ctrl+Space in an open Lua file will show the autocompletions for the L2U & gameObject-utils API as well as Lua function snippets.

Those L2U & gameObject-utils functions which are not overloaded (only one possible argument combination), will fill in the argument names for you.
