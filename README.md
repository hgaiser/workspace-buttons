# Workspace Buttons

This is a GNOME shell extension for switching workspaces on the panel, based off of my fork of [WorkspaceBar](https://gitlab.com/carmanaught/workspacebar), which itself was forked from [mbokil/workspacebar](https://github.com/mbokil/workspacebar). I generally update the extension to work with the most recent GNOME version and try to follow changes to official GNOME extensions (e.g.  `registerClass` or `_init`/`constructor` changes) and I don't guarantee backwards compatibility.

The primary difference with this extension is that it uses PanelMenu.Button objects for each workspace button. Each of these buttons has a menu which contains a list of the windows on the workspace, allowing you to activate the application (credit to [lyonell/all-windows](https://github.com/lyonel/all-windows) for some of the code and ideas). The buttons also allow switching to a given workspace if the option to do so has been toggled on (with a choice between Primary and Secondary button, depending on preference).

While most of the functionality from the WorkspaceBar extension has been kept, some things have been removed. See further below for details. One new addition is the ability to adjust the colors used for the workspace labels across various states (urgent / hover / active / inactive / empty) from the preferences.

This is how the Workspace Buttons look like in action with the current choice of styling (using a slightly tweaked Adwaita gnome-shell theme).

![Workspace Buttons in action](./screenshots/workspace-buttons-names.png?raw=true)
- The active/current workspace defaults to bright white text
- The urgent workspace with a window which is urgent or demands attention defaults to red text to draw attention to it
- The inactive worspaces which have a window/application in them default to a light grey text
- The empty workspaces with no window/application in them default to a dark grey text
- Hovering over a workspace defaults to bright white text

This is how the Workspace Buttons look using the Activity Indicator option and with some indicators in use. The indicators are  (U+F10C),  (U+F192),  (U+F111) for those interested. If you can't see the characters, you'll likely need [Font Awesome](http://fontawesome.io/icons/) (version 4, not 5) for them to be visible (check your distribution repositories).

![Workspace Buttons in action with activity indicators](./screenshots/workspace-buttons-indicators.png?raw=true)

This is how the menu looks when opened.

![Workspace Buttons with the menu open](./screenshots/workspace-buttons-menus.png?raw=true)

These are the General Settings on the Settings page.

![Workspace Buttons - General Settings](./screenshots/settings-general.png?raw=true)

**Note:** For the "Disable the workspace switcher popup" setting, as noted, the disabling of the workspace switcher popup will not work if another workspace switcher popup extension is installed, regardless of whether it's enabled or not (avoid installing another extension that does workspace switcher stuff with this setting enabled). This includes things that modify the workspace switcher or override it in some way.

This is the Workspace Label Format settings page which is used to change the settings for how the workspace labels appear. The format settings are somewhat more extensive and allow a greater degree of customization.

![Workspace Buttons - Workspace Label Format](./screenshots/settings-workspace-label-format.png?raw=true)

This is the Workspace Label Color settings page which allows the changing the workspace label colors, without needing to modify a stylesheet.css file.

![Workspace Buttons - Workspace Label Colors](./screenshots/settings-workspace-label-colors.png?raw=true)

**Note:** The 'Workspace Names' settings page has been removed so as not to need to keep the code updated in-line with changes to the official GNOME Workspace Indicator extension. To modify the workspace names, use something like `dconf-editor` and modify the value stored under:

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

The visual appearance is generally similar, but the bottom borders have been removed and will not be implemented as they can clash with gnome-shell themes that may already display an underline under a button when a menu is open. Due to removing the bottom borders, the workspace label colors have been adjusted slightly to provide more contrast.

## Credits
Thanks to these people for code of theirs that I've used.
- mbokil (for the original WorkspaceBar extension)
- fmuellner
- gcampax
- null4bl3
- lyonell
- hackedbellini
- windsorschmidt
