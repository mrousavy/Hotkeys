# Hotkeys
A small C# Library which allows binding (and unbinding) of global Hotkeys, even when application is not Focused/Activated or in Background (using P/Invokes)

# How to use:
HotKey constructor:
```
HotKey(ModifierKeys modifierKeys, Key key, Window window, Action<HotKey> OnHotKeyPressed);
```

Example _(C#, in a WPF Application)_:
```
var key = new HotKey(
    ModifierKeys.Control, 
    Key.S, 
    this, 
    delegate {
        MessageBox.Show("Ctrl + S was pressed!");
});
```
