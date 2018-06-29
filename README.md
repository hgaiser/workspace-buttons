# Workspace Buttons

This is a GNOME shell extension for switching workspaces on the panel, based off of my fork of [WorkspaceBar](https://gitlab.com/carmanaught/workspacebar), which itself was forked from [mbokil/workspacebar](https://github.com/mbokil/workspacebar). The extension requires at least GNOME 3.26, as it uses ES6 class syntax.

The primary difference with this extension is that it uses PanelMenu.Button objects for each workspace button. Each of these buttons has a menu which contains a list of the windows on the workspace, allowing you to activate the application (credit to [lyonell/all-windows](https://github.com/lyonel/all-windows) for some of the code and ideas). The buttons also allow switching to a given workspace if the option to do so has been toggled on (with a choice between Primary and Secondary button, depending on preference).

While most of the functionality from the WorkspaceBar extension has been kept, some things have been removed. See further below for details. One new addition is the ability to adjust the colors used for the workspace labels across various states (urgent / hover / active / inactive / empty) from the preferences.

This is how the Workspace Buttons look like in action with the current choice of styling. For reference the hover/active style for the buttons themselves (not the labels) is from the gnome-shell theme in use when taking these screenshots, specifically [Vertex Theme](https://github.com/horst3180/vertex-theme).

![Workspace Buttons in action](http://i.imgur.com/TvGCzvE.png)
- The active/current workspace defaults to bright white text
- The urgent workspace with a window which is urgent or demands attention defaults to red text to draw attention to it
- The inactive worspaces which have a window/application in them default to a light grey text
- The empty workspaces with no window/application in them default to a dark grey text
- Hovering over a workspace defaults to bright white text

This is how the Workspace Buttons look using the Activity Indicator option and with some indicators in use. The indicators are  (U+F10C),  (U+F192),  (U+F111) for those interested. If you can't see the characters, you'll likely need [Font Awesome](http://fontawesome.io/icons/) (version 4, not 5) for them to be visible (check your distribution repositories). 

![Workspace Buttons in action with activity indicators](http://i.imgur.com/VJZdxd9.png)

This is how the menu looks when opened. The left is the appearance with the panel at the top and the right is the appearance with the panel at the bottom (using BottomPanel - [Gnome Extensions Page](https://extensions.gnome.org/extension/949/bottompanel/) - [GitHub](https://github.com/Thoma5/gnome-shell-extension-bottompanel)).

![Workspace Buttons with the menu open](http://i.imgur.com/R1WpVXv.png)

These are the General Settings on the Settings page.

![Workspace Buttons - General Settings](https://i.imgur.com/AGpEZWu.png)

This is the Workspace Label Format settings page which is used to change the settings for how the workspace labels appear. The format settings are somewhat more extensive and allow a greater degree of customization.

![Workspace Buttons - Workspace Label Format](http://i.imgur.com/I8SZnR9.png)

This is the Workspace Label Color settings page which allows the changing the workspace label colors, without needing to modify a stylesheet.css file.

![Workspace Buttons - Workspace Label Colors](http://i.imgur.com/MJOc61O.png)

**Note:** The Workspace Names setting page has been removed so as not to need to keep the code updated in-line with changes to the official GNOME Workspace Indicator extension. To modify the workspace names, use something like `dconf-editor` and modify the value stored under:

```
/org/gnome/desktop/wm/preferences/workspace-names
```

The value for the list should be a series of values for each workspace in order, inside single quotes, separated by commas and bounded by square brackets, like so:

```
['Workspace 1', 'Workspace 2', 'Etc.']
```

## Changes from the WorkspaceBar extension

The following features of the [WorkspaceBar](https://gitlab.com/carmanaught/workspacebar) extension have not been included and there is no intention to re-implement them.

The **show overview** functionality is no longer provided as this used an enclosing button to trigger an enter/exit event and was also not something I used when there are various other methods available (the activities button itself or the hot-corner). It also seems to defeat the point of having buttons that you might want to use, if mousing over them activates the overview.

The **mouse button to open preferences** has not been implemented, as this defaulted to a mouse right-click which can now open a menu. There is now a menu item to access the settings/preferences.

The **option for hiding empty workspaces** is no longer available, as it doesn't work properly with the ability to traverse left/right between workspaces and gets skipped over. While it could be made visual when scrolling workspaces (as is done in the WorkspaceBar extension), it loses a degree of accessibility.

The visual appearance is generally similar, but the bottom borders have been removed and will not be implemented as they can clash with gnome-shell themes that may already display an underline under a button when a menu is open. Due to removing the bottom borders, the workspace label colors have been adjusted slightly to provide more contrast.

## Credits
Thanks to these people for code of theirs that I've used.
- mbokil (for the original WorkspaceBar extension)
- fmuellner
- gcampax
- null4bl3
- lyonell
- hackedbellini
