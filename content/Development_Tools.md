# Development Tools

This article lists various free software tools which help in development of Luanti and mods for Luanti.

Luanti development
------------------

* [Development Test](https://wiki.minetest.net/Games/Development_Test): A testing game for testing various engine features
* [/minetest/util](https://github.com/minetest/minetest/tree/master/util): Various maintenance utilities

Mod development
---------------

### Standalone software

* [NodeBoxEditor](https://forum.minetest.net/viewtopic.php?f=14&t=2840): Build [node boxes](/index.php?title=Node_boxes&action=edit&redlink=1 "Node boxes (page does not exist)") by dragging their edges.
* [MTS Editor](https://forum.minetest.net/viewtopic.php?f=14&t=23724): A program to create, view and edit Luanti schematics, but it supports other file formats (e.g. Minecraft schematics) as well
* [Schematic Creator](https://forum.minetest.net/viewtopic.php?f=14&t=18992): A Java program to create schematics
* [Model Creator](https://forum.minetest.net/viewtopic.php?f=14&t=18780&): A Java program to create meshes
* [RocketLib Toolkit](https://forum.minetest.net/viewtopic.php?t=23891): Lua-based SQLite3 map reader
* [luacheck](https://github.com/mpeterv/luacheck/): Lua linter and static code analyser (see also [the chapter rubenwardy's modding book](https://rubenwardy.com/minetest_modding_book/en/quality/luacheck.html))
* [busted](https://olivinelabs.com/busted/): Lua unit testing framework (see also [the chapter rubenwardy's modding book](https://rubenwardy.com/minetest_modding_book/en/quality/unit_testing.html))

### Web applications

* [Luanti Biome Point Visualizer](https://wuzzy.codeberg.page/LiBPoV/): Edit and visualize biome heat/humidity points in a Voronoi diagram ([source code](https://codeberg.org/Wuzzy/LiBPoV))
* [Minetest Formspec Editor](https://luk3yx.gitlab.io/minetest-formspec-editor/): Visual formspec editor

### Luanti games and mods

See the [Developer Tools](https://content.minetest.net/packages/?tag=developer_tools) tag in ContentDB.

Scripts
-------

### Formspecs

* [Minetest Formspec Editor](https://luk3yx.gitlab.io/minetest-formspec-editor/): A great online tool with drag and drop that allows you to import and export formspecs in different versions
* [Perlin noise tuner](https://codepen.io/treer/pen/gOPZyov?editors=0010) Visualizes 2D Perlin noise that Luanti will generate with different noiseparams. (Emulation of Luanti Perlin noise can be wrong in extremes/edge-cases due to precision of JavaScript number type)

### Translation

* [Luanti Translation Tools](https://codeberg.org/Wuzzy/Luanti_Translation_Tools): Collection of Python scripts to manage mod translation files (\*.tr)

#### Legacy

* [update\_translations](https://github.com/FaceDeer/update_translations): Older version of the translation updater script included in Luanti Translation Tools
* [findtext.lua](https://notabug.org/pgimeno/minetest/src/translation-toolchain/util/findtext.lua): Create mod translation template (buggy!) ([see also](https://forum.minetest.net/viewtopic.php?f=47&t=23330))
* [updatetext.lua](https://notabug.org/pgimeno/minetest/src/translation-toolchain/util/updatetext.lua): Update mod translation template (buggy!) ([see also](https://forum.minetest.net/viewtopic.php?f=47&t=23330))

Syntax highlighting
-------------------

* [Vim syntax highlighting for \*.tr files](https://codeberg.org/Wuzzy/luanti_tr_vim_syntax)
