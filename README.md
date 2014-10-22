This module for Awesome WM provides a simple way to manage windows rules.

### Dependencies

* [awesome](http://awesome.naquadah.org/) v3.5.0 (works with latest git version)
* [LuaDBI](https://code.google.com/p/luadbi/) - A database interface library for Lua

### Installation

First you need to download this module:

```bash
git clone https://github.com/mindeunix/clientdb.git ~/.config/awesome/clientdb
```

Next step is adding require at the top of your rc.lua:
```lua
local clientdb = require("clientdb")
```

Then you can add keybinding <kbd>modkey</kbd> + <kbd>s</kbd>:
```lua
clientkeys = awful.util.table.join(
    awful.key({ modkey,           }, "s",      function (c) clientdb.save(c)                 end),  -- ADD THIS LINE HERE
    awful.key({ modkey,           }, "f",      function (c) c.fullscreen = not c.fullscreen  end),
    awful.key({ modkey, "Shift"   }, "c",      function (c) c:kill()                         end),
```

The last thing you need to do is add function clientdb.load():

```lua
    -- Set Firefox to always map on tags number 2 of screen 1.
    -- { rule = { class = "Firefox" },
    --   properties = { tag = tags[1][2] } },
}
-- }}}

-- Initializes the windows rules system
clientdb.load() -- ADD THIS LINE HERE
```

Now, tell Awesome WM to reload your configuration and start saving windows rules <kbd>modkey</kbd> + <kbd>s</kbd>
If you still need to modify these rules you can use [SQLiteStudio](http://sqlitestudio.pl) or any other [SQLite3](http://www.sqlite.org/cvstrac/wiki?p=ManagementTools) client.

![db](http://i.imgur.com/GVnNqNY.png)

### Functions

| Name   | Description                           | Arguments         |
| ------ | ------------------------------------- | ----------------- |
| save   | Save the client.                      | The client object |
| load   | Load windows rules from the database. | --                |


### TODO

* Gtk dialogs ?

