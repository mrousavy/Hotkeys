# <img src="https://github.com/mrousavy/Hotkeys/blob/master/Images/Logo.png?raw=true" width="42"> Hotkeys
A small C# (.NET) Library which allows binding of global HotKeys to any Application's Windows (including Windows Apps such as `explorer.exe`), even in Background. (using P/Invokes)


# Install

Install from [NuGet](https://www.nuget.org/packages/GlobalHotkeys)

```
Install-Package GlobalHotkeys
```
[![NuGet](https://img.shields.io/nuget/dt/GlobalHotkeys.svg)](https://www.nuget.org/packages/GlobalHotkeys/) 

> _(or [download the Library (.dll)](https://raw.githubusercontent.com/mrousavy/Hotkeys/master/Downloads/Hotkeys.dll) manually)_


<a href='https://ko-fi.com/F1F8CLXG' target='_blank'><img height='36' style='border:0px;height:36px;' src='https://az743702.vo.msecnd.net/cdn/kofi2.png?v=0' border='0' alt='Buy Me a Coffee at ko-fi.com' /></a>

# Usage

Example _(C#, in a WPF Application)_:
```cs
using mrousavy;
// ...
var key = new HotKey(
    (ModifierKeys.Control | ModifierKeys.Alt), 
    Key.S, 
    this, 
    (hotkey) => {
        MessageBox.Show("Ctrl + Alt + S was pressed!");
    }
);
// ...
key.Dispose();
```

> Note #1: Since `HotKey` implements the [`IDisposable` interface](https://docs.microsoft.com/en-us/dotnet/api/system.idisposable?view=netcore-3.1), you must call `Dispose()` to unregister the Hotkey, e.g. when your Window closes. Keep in mind that when you're using `using(...) { ... }`, the HotKey gets unregistered and disposed once you exit the using-statement's scope.

> Note #2: Use the binary **or** operator (`|`) to combine key combinations for the constructor.

> Note #3: Use a Window Reference as the third Argument. This may be a [WPF `Window`](https://docs.microsoft.com/en-us/dotnet/api/system.windows.window?view=netcore-3.1), a [`WindowInteropHelper`](https://docs.microsoft.com/en-us/dotnet/api/system.windows.interop.windowinterophelper?view=netcore-3.1), or a Window Handle ([`IntPtr`](https://stackoverflow.com/questions/1953582/how-to-i-get-the-window-handle-by-giving-the-process-name-that-is-running)). So you can use your own WPF/WinForms Window, as well as another process's Window using it's Handle. Keep in mind that this is sketchy behaviour and not the intention of this library.
