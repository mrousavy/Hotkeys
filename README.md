# <img src="https://github.com/mrousavy/Hotkeys/blob/master/Images/Logo.png?raw=true" width="42"> Hotkeys
A small C# Library which allows binding (and unbinding) of global Hotkeys, even when application is not Focused/Activated or in Background (using P/Invokes)

[Download the Library (.dll)](https://raw.githubusercontent.com/mrousavy/Hotkeys/master/Downloads/Hotkeys.dll)

# How to use:
Add the `.dll` to your .NET Project's `References` Tree in the Solution View.

HotKey constructor:
```C#
HotKey(ModifierKeys modifierKeys, Key key, Window window, Action<HotKey> OnHotKeyPressed);
```

Example _(C#, in a WPF Application)_:
```C#
var key = new HotKey(
    (ModifierKeys.Control | ModifierKeys.Alt), 
    Key.S, 
    this, 
    delegate {
        MessageBox.Show("Ctrl + Alt + S was pressed!");
    }
);
```
