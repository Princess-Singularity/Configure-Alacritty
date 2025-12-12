# Configure-Alacritty
---
How to configure Alacritty Terminal for everyday usage. 


Alacritty is a modern temrinal emulator in beta, is provides flexability and performance. Alacritty is supported on BSD, Linux, macOS and on Windows. This
document will serve as a tutorial to walk you through configuring Alacritty with a basic configuration, and explain how this configuration works so you may utilize the Alacritty.org config instructions more effectively. 




Alacritty can be instlled by following their official github repository instruction located at : [Github](https://github.com/alacritty/alacritty/blob/master/INSTALL.md)



---

### Syntax & Config File Creation
  Alacritty uses the TOML format to configure it's functionality. The configuration file is not created automatically, and will have to be created manually.

  **Creating the file**
  *Command to create the file:*

` touch /etc/alacritty/alacritty.toml `

When creating this file it is very beneficial to considuer using the *XDG_CONFIG_HOME* nomenclature provided by the XDG Base Directory specification. 
More information regarding this specification can be found on the Arch Wiki at [XDG Base Directory](https://wiki.archlinux.org/title/XDG_Base_Directory)

*Command to create the file in XDG instead:*

` touch $XDG_CONFIG_HOME/alacritty/alacritty.toml`


Editing the file can be done safely using the Alacritty terminal prior to configuration. You can do this using your prefered text editor program such as vim, vi,nvim, or nano. 

*Command to edit file:*

` sudo nvim $XDG_CONFIG_HOME/alacritty/alacritty.toml `    

### File Configuration

**The config file is sperated into different sub sections dedicated to editing specific configuration arguments broken down into categories.**
**The sections / categories of the file are as follows:**
- general
- env
- window
- scrolling
- font
- colors
- bell
- selection
- cursor
- terminal
- mouse
- hints
- keyboard
- debug

Each of these sections are defined in the document using brackets, thus the general section starts with `[general]`

#### General Section
`
[general]
working_directory = "None"
live_config_reload = true
`
Working Directory defines the default directory alacritty will start in when launched. 

Live_config_reload allows us to change config options and see them reflected without having to restart the application. 

#### Env section
`
[env]
TERM = "xterm-256color"
`

This argument will allow Alacritty to use a larger colorspace for theming and customization. 

#### Window arguments
`
[window]
padding = {x = 2, y = 2}
dynamic_padding = true
decorations = "Full"
opacity = 0.75
blur = true
title = "❤︎ Terminal ❤︎"
level = "Normal" #other option = "AlwaysOnTop"`

Padding = determines a border around the edges of the terminal, providing default spacing for text. 
dynamic_padding = allows this to change when resizing or executing terminal programs that need to change it. 
decorations = determine window buttons available to the user, and name. 
title = changes the text at the top of the terminal window from the default "Alacritty"

#### Font arguments
** Please keep in mind these fonts will need to be installed on the system in order to be used by the alacritty temrinal**
`[font]
normal = {family="font family name",style="Regular"}
bold = {family="font family name",style="Bold"}
italic = {family="font family name" ,style="Italic"}
bold_italic = {family="font family name" ,style="Bold Italic"}
size = 12.00
offset = {x = 1,y = 1}
`

normal = default font 
bold = font when using bold text
italic = font when using italic text
bold_italic = font when using bold and italic simultaniously
size = font size
offset = spacing 

#### Color arguments
** This will determine the colors used for certain elements in the terminal, such as the cursor, highlighting text, etc. 
this section may have sub sections such as [color.primary] for logical sorting. **
`
cursor = {text = "hex value", cursor = "hex value"}
footer_bar = {foreground = "hex value,background = "hex value"}
selection = {text="hex value",background = "hex value"}
[colors.primary]
foreground = "hex value"
background = "hex value"
#vi_mode_cursor = "hex value`

cursor = Colors which should be used to draw the terminal cursor.
footer_bar = input, hyperlink URI preview, etc.
selection = highlight color when selecting text
foreground = determines forground color.
background = determines background color. 

#### Usability settings:
** You may need to specify which shell enviroment you are using, especially if it is not the default shipped with your distro **
`
[terminal]
shell = {"/bin/zsh",args=["-1]}
`

** You may also want to enable key bindings for copying and pasting in terminal **
`
{Key ="c",mods ="Control",mode = "AppCursor|Vi|Search",action = "Copy"},
{Key ="p",mods ="Control",mode = "AppCursor|Vi|Search",action = "Paste"},
{key = "N", mods = "Control|Shift", action = "CreateNewWindow" }`

Implementing these arguments will give you a basic working configuration for alacritty terminal that has some simple styling to make it your own. 


