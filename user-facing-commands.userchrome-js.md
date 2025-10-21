---
# weight: 999
title: User Facing Commands
icon: "article"
date: "2025-09-10T22:07:19-04:00"
lastmod: "2025-09-10T22:07:19-04:00"
draft: true
tags: ['userchrome']
---
## User facing commands
User facing commands are commands or functions which are meant to be used
by users

###  how are commands defined / used?
* Using keymaps to execute commands or Lua functions
* Auto Commands (`autocmd`) to trigger actions on events
* Filetype plugins (`ftplugin`) to set up buffer-specific behavior
* Within LSP `on_attach` functions for buffer-local LSP client setup
// command bar:
* Through user-defined commands (e.g., `:MyCustomCommand`)
* Sourcing Vim script or Lua files (`:source path/to/file.vim`, `:luafile path/to/file.lua`)
* Calling Vim functions (e.g., `:call MyFunction()`)
* Direct execution of Lua code from the command line (e.g., `:lua print("Hello from Lua")`)
* As part of a plugin's configuration, often in `init.lua` or `config` functions for plugin managers
* Executing shell commands (e.g., `:!ls`, `:term`)


In userchrome, we can define a command with a
<command> XULElement

and call that command's function with
```js
document.querySelector(#cmd_Element)
    .doCommand()
// <command> elements by strong convention
// register their code to be called with an
// event listener for the 'commmand' event.
// example : <https://searchfox.org/firefox-main/source/browser/base/content/browser-development-helpers.js#26-29>
//
// so we can alternatively do this:
document.querySelector(#cmd_Element)
    .dispatchEvent(new CustomEvent('command'))
```
