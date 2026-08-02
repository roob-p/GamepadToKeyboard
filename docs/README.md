[![🔙 Back](https://img.shields.io/badge/🔙-Back-white?style=flat-square&logoColor=blue&color=blue)](https://roob-p.github.io)  
# 🕹️ Joynix   
<!--![GitHub Downloads](https://img.shields.io/github/downloads/roob-p/Joynix/total)-->  
 
🕹️ *Flexible gamepad input mapping for keyboard and mouse, built to be quick to set up, easy to use and highly customizable.*   

- This tool lets you send mouse and keyboard input using your XInput controller with a great level of customization.
- It's designed to make controller configuration fast and simple: just open a config `.ini` and edit assignments, modifiers and variables.
- Config files can be edited and reloaded on-the-fly using a hotkey, without restarting the application.
- **It provides fine control over several controller aspects**: deadzone types (square/rectangular, circular with and without rescale), deadzone values (per stick, axis, or direction), axis inversion, modifiers (`[Toggle],[Turbo],[TurboToggle],[Execute],[Combo],[Sequence]` and others) and more.
- Supports switchable key assignment groups: `Layer` (with fallback support) and `Set` (without fallback).
- Includes a customizable rumble system with per-button vibration effects.
- Planned features will include: a tray-resident profile switcher, chord mode and a more advanced `[MACRO]` modifier.



##### ⚠️ `Joynix` requires an Xinput controller (native or emulated via tools like DS4Windows, DualSenseX, x360ce, etc.).  


## 📝 Controller configuration
- The program includes several modifiers, which change the button behaviour.  
  **Just add one of these modifiers before the assigned keys:**
 - `[Toggle], [Turbo], [TurboToggle]`
 - `[Combo]`: send multiple keys at once
 - `[Execute]`: run programs (e.g. `notepad`, `calc.exe`, `c:\yourfolder\yourprogram.exe`)
 - `[ComboAsync]`: send multiple keys with a delay between each key (defined with `ComboKeysDelay`)
 - `[ToggleCombo], [TurboCombo], [TurboToggleCombo]`
 - `[Sequence]`: send keys in sequence. Similar to `[ComboAsync]`, but ComboAsync sends and holds the keys, `[Sequence]` sends simple presses.
 - `[Text]`: send up to 200 characters (e.g. `[TEXT]this is a string`). Not intended for games.
 - `[Hold]`: perform different actions depending on how long the button is held. Short press sends the 1st key, medium press sends the 2nd key, long press sends the 3rd key. (e.g. `[Hold] a, b, c`)
 - `[FastPress]`: repeatedly press the button to cycle through the keys to send (define the keys after the modifier, e.g. `[FastPress] a, b, c`).
 - `[Shift]`: add a set of keys (up to 5, e.g. `[Shift] a, b, c, d, e`) and switch between them using the ShiftMode modifiers:
   - `[ShiftMode]`: press and hold to change the active Shift key (define the target key number after the modifier, e.g. `[ShiftMode] 3`).
   - `[ShiftModeToggle]`: same as above, but the button acts as a toggle.
   - `[ShiftModeCycle-], [ShiftModeCyle+]` or `[ShiftModeCyle]`: cycle through the available Shift keys. These modifiers do not require a value (e.g. `LT = [ShiftModeCyle+]`).
   - These modifiers can also be activated via configurable keyboard hotkeys.
 - **`Layer modifiers`**:
   - `[LayerMode]`, `[SetMode]`, `[LayerModeToggle]`, `[SetModeToggle]`: switch to a specific Layer or Set assignment (e.g `[LayerMode] menuinventory`).
   - `[LayerCycle-]`, `[LayerCycle]`, `[LayerCycle+]`: cycle through the Layers/Sets defined in `LayerToCycle` under the `[Other]` section. These modifiers do not require a Layer/Set name (e.g. `LT = [LayerCycle-]`, `LT = [LayerCycle+]`).
- Set `AnalogToMouse = 1` (enabled by default) to move the mouse with the analog stick defined in `Stick` (default: `Stick = RS` ).
- Mouse wheel input is digital when assigned to buttons, and analog/progressive when assigned to sticks or triggers.
#### Config loading
- Configs can be loaded through `ConfigToLoad` in `Joynix.config`, via command line, or by drag and drop.  

### 🔄 Live config reload

- Configuration files can be edited while the game is running.
- Just press the Hotkey (`Shift`+`Ctrl`+`5` by default) to instantly reload the current `.ini`, without restarting the application.
- The Hotkey can be customized in `GamepadToKeyboard.config`. 


## 🕹️ Button assignments
Values you can assign to the buttons: 
- `A..Z`, `0..9`, `F1..F12`
- common buttons: `Enter`, `Space`, `Esc`, `Lalt`, `Lshift`, `Lctrl`, `Lwin`
- mouse buttons: `LBmouse`, `RBmouse`, `MBmouse`, `WheelUp`, `WheelDown`  
##### Additional assignable keys are listed at the bottom of this page.

### 📘 Syntax
- Just add one modifier to button assignments, placing it before the keys (e.g `A = [Turbo]c`).
- Each key must be separated with `,`. Extra spaces are ignored (e.g `A = [COMBO] c,S, L,Lbmouse`).
- Modifiers are case-insensitive (`[Turbo]`, `[TURBO]` and `[turbo]` are equivalent).
- Spaces after modifiers are optional (`[Turbo]k` and `[Turbo] k` are both valid).
- Combo-based modifiers support up to 10 buttons, while `[Sequence]` supports up to 15. Any additional keys are ignored.


**Example syntax:**

|Button   |Assignment              |      |‎Button   | Assignment          |‎     |Button   |Assignment  |‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎ ‎   
|---------|------------------------|------|---------|---------|-----------|-----|---------|------------|
|`A`      |Enter                   |      |`Back`   | F1                  |     |`LSup`   | Up         |           
|`B`      |[Turbo] Space           |      |`Start`  | Esc                 |     |`LSdown` | Down       |
|`X`      |[ComboAsync] S, Space,r |      |`LS`     | [Toggle]LShift      |     |`LSleft` | Left       |                    
|`Y`      |[COMBO]A,x,F,LBmouse    |      |`RS`     | [execute] calc.exe  |     |`LSright`| Right      |
|`LB`     |RBmouse                 |      |`Dup`    | Up                  |     |`RSup`   |            |
|`RB`     |LBmouse                 |      |`Ddown`  | Down                |     |`RSdown` |            |
|`LT`     |Wheelup                 |      |`Dleft`  | Left                |     |`RSleft` |            |
|`RT`     |WheelDown               |      |`Dright` | Right               |     |`RSright`|            |
|`Home`   |Lwin                    |


## ⚙️ Common controller options  

| Section                         | Option                         | Values / Description                                                                                                       |
|---------------------------------|--------------------------------|------------------------------------------------------------------------------------------------------------
|                                 |                                |                                                                                                                            |
|Mouse                            |AnalogToMouse                   |`1/0`    : Turn On/Off the mouse movement via analog sticks.                                                                |
|                                 |Stick 	                         |`RS/LS`  : Analog to use. Button assignments ignored.         
|                                 |Deadzoneshape                   |`1/2/3`  : `Square/Rectangular`,`Circular`,`Circular (with rescale)`.     |
|                                 |DeadzoneType                    |`1/2/4`  : Both axis/ per axis/ per direction.                                                                              |
|                                 |(Stick)AxisInverted             |`1/0`    : Turn On/off axis inversion. 4 options available.                                             | 
|                                 |Sensitivity                     |`Value`  : Mouse movement speed.                                                                                            |
|Analogs                          |DeadzoneType                    |`1/2/4/8`: Both sticks/ per stick/ per axis/ per direction.                                                                |    
|                                 |(Stick)AxisInverted             |`1/0`    : Turn On/off axis inversion. 4 options available.                               
|Other                            |SendKeysTypes                   |`1`: Game mode; `2`: Desktop (with windows-style keypress delay + repeat)     

<br>  
  
 ### ⌨️ Hotkeys                                                
The program supports several configurable hotkeys. They can be set in `Joynix.config` and disabled if needed.
- **Configuration reload**: `Shift + Ctrl + 5` (enabled by default). 
- **Stats system**: `Shift + Ctrl + 6` (enabled by default).
- **ShiftMode controls**: `ShiftModeCycle-` *(Shift + Ctrl + 7)*, `ShiftModeCycle+` *(Shift + Ctrl + 8)*, `ShiftModeToggle` *(Shift + Ctrl + 9)*, disabled by default.
- **Layer controls**: `LayerCycle-` *(Shift + Ctrl + 1)*, `LayerCycle+` *(Shift + Ctrl + 2)*, `LayerToggle` *(Shift + Ctrl + 3)*, disabled by default.
- To enable/disable a hotkey, use the corresponding boolean flag in `Joynix.config`:
  e.g. `KeyboardShiftEnabled = False`.  

<br>

## 🖼️ Layers
- Joynix supports multiple switchable slots of key assignments through Layer and Set.
- `Layer` supports fallback (if a key doens't have an assignment, the correspondent value is taken from the Button section), while `Set` does not. 
- You can define a Layer adding a section in the .INI file using square brackets (e.g. `[inventorymenu]`).
- Adding the prefix `layer:` or `set:` to the name section set its initial type (Layer or Set) (e.g. `[set:inventorymenu], [layer:inventorymenu]`). Types can be overridden using the Layer/Set modifiers. If no prefix is added the default type is layer.
- Use `[LayerMode]`, `[SetMode]`, `[LayerModeToggle]`, `[SetModeToggle]` followed by the Layer/Set name in button assignments to load that Layer/Set.
- You can also define up to 5 Layers/Sets using `LayerToCycle` in `Other` section and switch between them using `[LayerCycle+]` and `[LayerCycle-]`. These can reference existing Layers/Sets already used by the mode modifiers, or completely different ones.
- Each Layer/Set assignment uses one available slot, even if it references an already existing Layer/Set.
- The maximum number of active Layer/Set assignments is 15.
- When you assign a Layer/Set modifier to a button, that "activator" key will have the same function in the called layer/set (even if you try to reassign it to a new value). 
- **Please use Layer/Set modifiers only in the Buttons section.**
- Check the `LayerExample.ini` to see how layers/set work.

<br>

## 〰️ Vibration feature
- Joynix lets you create customizable vibration effects for every button.
- Three different vibration modes are available:
   - `Hold`: vibration continues while the button is held down.
   - `Single`: send a single vibration each time the button is pressed (duration can be configured in ms using `SingleDuration` variable).
   - `Repeat`: vibration is repeated while the button is held down with an interval time (RepeatDuration and RepeatInterval are available).
- You can define the buttons to vibrate with VibrateButtonN in the `[Vibration]` section (e.g. `VibrateButton1 = X`, `$VibrateButton2= LB` etc.) and specify the properties adding a dot and the variable to the name:  
 >   
 > - VibrateButton2                   = Y
 > - VibrateButton2.Style             = 1
 > - VibrateButton2.LeftMotorStrength = 50
 > - VibrateButton2.SingleDuration    = 300
- If a property is not set, the corresponding global value is used.
- You can also define `Modifier` buttons: the vibration only starts when this button is pressed together with a VibrateButton, e.g.:
 >   
 > - VibrateButton3                   = X
 > - VibrateButton3.Modifier          = LB 
- Common properties available:
 >   
 > - VibrateButtonN.Style: (0, 1, 2) 
 > - VibrateButtonN.Motor: (Left, Right, Both)
 > - VibrateButtonN.LeftMotorStrength, VibrateButtonN.RightMotorStrength
 > - VibrateButtonN.SingleDuration, VibrateButtonN.RepeatDuration, VibrateButtonN.RepeatInterval  
- If `VibrateButtonN.LeftMotorStrength` or `VibrateButtonN.RightMotorStrength` are not available, Joynix looks up the global variables `LeftMotorStrength` and `RightMotorStrength`. If `UseSameStrengthVal = 1` then the `Strength` global variable is used.
- You can enable progressive vibration strength with `ProgressiveTrigger = 1` (in this mode, Style is ignored for analog triggers).
- Joynix supports simultaneous vibration effects from multiple buttons by automatically combining the left and right motor strengths.
- **By combining styles, durations, intervals and motor strengths, you can create a wide variety of vibration effects.**

<br>
                                                                   

### 🧪 Technical Notes
- **Add only one modifier per assignment (e.g `[Turbo][Combo]` NOT supported).**
- Please don't assign `[Turbo]` and other Turbo-based modifiers to Wheel, since it has dedicated repetition variables.
- When multiple `[Shift]` assignments are used together with ShiftModeCycle modifiers, it is recommended to use the same number of keys in each assignment. Different lengths are supported (e.g. `LT = [Shift] a,b,c,d,e` and `RT = [Shift] j,k,l`), but may produce less predictable results.
- Timing-related modifiers can be customized through their dedicated variables:
  * `[ComboAsync]` and `[Sequence]`: configurable delays through `ComboAsyncTime` and `SequenceTime` (ms).
  * `[FastPress]`: configurable time window through `FastPressTime`.
  * `[Hold]`: configurable hold duration thresholds through `HoldTime`.
- **The Windows key may not behave exactly like a physical key due to Windows focus-handling limitations.**
- Please don't use `CTRLDOWN`, `ALTDOWN`, `SHIFTDOWN`, `LWINDOWN`, `RWINDOWN` in the assignments. These special keys are handled through `LAlt`, `LCtrl`, `RAlt`, `RCtrl`, `LWin`, and `RWin`.


### ⚠️ Notes
- The exe that comes with the extension is 64bit. The reason is that the x64 version of Autoit programs receive minor flags from AV engines. If you need the x86 one you can download it from the main in the repo, or from the attached files in the releases.  
- The program does not contain any malicious behaviour. If your AV engine flags it as malware it's a false positive. If so, please send `Joynix.exe` (or any associated flagged file) to your AV vendor asking for a false positive review request.


<br>  

**If you enjoy Joynix, you can buy me a coffee. It will be very appreciated ;)**  

[![ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/E1E214R1KB)  


<br>

- Github repo: 🐙 [roop-p/Joynix](https://github.com/roob-p/Joynix/)
- Download last version:
  [Joynix v1.2.4](https://github.com/roob-p/GamepadToKeyboard/releases/download/v1.2.4/Joynix.exe)
  <br>
  <br>

## ⌨️ List of assignable keys
`SPACE`, `ENTER`, `ALT`, `BACKSPACE`, `BS`, `DELETE`, `DEL`, `UP`, `DOWN`, `LEFT`, `RIGHT`, `HOME`, `END`, `ESCAPE`, `ESC`, `INSERT`, `INS`, `PGUP`, `PGDN`, `F1`, `F2`, `F3`, `F4`, `F5`, `F6`, `F7`, `F8`, `F9`, `F10`, `F11`, `F12`, `TAB`, `PRINTSCREEN`, `LWIN`, `RWIN`, `NUMLOCK on`, `CAPSLOCK off`, `SCROLLLOCK toggle`, `BREAK`, `PAUSE`, `NUMPAD0`, `NUMPAD1`, `NUMPAD2`, `NUMPAD3`, `NUMPAD4`, `NUMPAD5`, `NUMPAD6`, `NUMPAD7`, `NUMPAD8`, `NUMPAD9`, `NUMPADMULT`, `NUMPADADD`, `NUMPADSUB`, `NUMPADDIV`, `NUMPADDOT`, `NUMPADENTER`, `APPSKEY`, `LALT`, `RALT`, `LCTRL`, `RCTRL`, `LSHIFT`, `RSHIFT`, `SLEEP`, `ASC nnnn`, `BROWSER_BACK`, `BROWSER_FORWARD`, `BROWSER_REFRESH`, `BROWSER_STOP`, `BROWSER_SEARCH`, `BROWSER_FAVORITES`, `BROWSER_HOME`, `VOLUME_MUTE`, `VOLUME_DOWN`, `VOLUME_UP`, `MEDIA_NEXT`, `MEDIA_PREV`, `MEDIA_STOP`, `MEDIA_PLAY_PAUSE`, `LAUNCH_MAIL`, `LAUNCH_MEDIA`, `LAUNCH_APP1`, `LAUNCH_APP2`, `OEM_102`  

<br>



### 🎖️ Credits
This gamepad script was written in AutoIt.  
The program makes use of a remodified version of the XInput UDF by Oxin8 (xoninx@gmail.com) to read Xinput states.





 
