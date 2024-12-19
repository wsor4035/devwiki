---
title: Changelog (OLD)
aliases:
- /OldChangelog
---

# Old Changelog
This is the old changelog for outdated Minetest versions (later renamed to “Luanti”) and posterity.

For the latest versions, see [Changelog](/Changelog "Changelog").

0.4.17.1 → 0.4.17.2 (Android Only)
----------------------------------

Patched 0.4.17.1 to fix some Android crashes, released on June 28, 2018.

* Android: Use correct temporary path (_stujones11_)
* Fix MurmurHash implementation to really be unaligned (_sfan5_)
* Fix crash caused by Lua error during startup (_red-001_)
* Fix buffer overrun in SRP (_red-001_)
* Android: use c++\_shared library instead of c++\_static (_nerzhul_)
* Android: Fix android tools version used to build MT (_nerzhul_)

0.4.17 → 0.4.17.1
-----------------

Patched 0.4.17 to fix a crash, released on June 10, 2018.

* Correct character encoding for chat\_send\_player and chat\_send\_all
* Fix crash caused by log\_deprecated and the use of deprecated functions
* Fix crash on pause menu when pressing up/down keys
* Android build system fixes

0.4.16 → 0.4.17
---------------

Backported release containing only bug fixes and small features. 0.4.17 was released on June 3, 2018.

### Feature
* Builtin auth handler: Speed up file writing
* LBM lookup performance improvement on mapblock loading
* Minetest ASCII art: Move from actionstream to rawstream
* CollisionMoveSimple: Collide with 'ignore' nodes
* Allow objects to exist outside of 'mapgen limit' (mapblocks may exist)
* Find nodes in area (under air): Raise volume limit
* Allow dumping userdata using dump()
* Add minetest.is\_player API function
* Refine movement anticheat (again)
* Apply physics overrides correctly during anticheat calculations
* Shut down mapgen threads before other shutdown tasks
* Show script source of deprecated function calls
* Inventory: Restrict access from too far away (anticheat)
* Improve Settings tab button alignments
* Add minetest.sha1 util API function
* Avoid filtering low-res textures for animated meshes
* Add setting for near plane distance to improve performance
* Footstep sounds: Reduce gain to balance volume
* Positional sound: Limit volume when closer than 1 node
* Leveled nodebox: Change levels from 1/63rds to 1/64ths
* ClientInterface: user limit checking function
* Make dropped items colorable
* Trigger on\_rightclick regardless on the formspec meta field
* Clarify "Full viewing range" key message
* Rework new sneak code, minimize
* Tile material: Opaque textures by default to prevent xray effect
* Automatic item and node colorization
* find\_nodes\_in\_area: Extend maximal count to U32\_MAX
* Add server option to remove color codes from chat messages

### Bug fixes and Improvements

* Various build fixes (LuaJIT not found, OpenBSD)
* Dungeons: Mostly fix missing stair nodes
* Cavegen: Fix variable typo that broke mgvalleys large cave distribution
* Prevent translating empty strings
* upright\_sprite: Fix texture position for players
* core.rotate\_node: Do not trigger after\_place\_node for mod compatibility
* macOS: don't require X11 libraries during compilation
* Generate Notifier: Clear events once after all 'on generated' functions
* Fix liquid post effect colour behaviour in third person view
* Delete world dialog: Move buttons to avoid double click deletion
* Fix /shutdown countdown parameter
* Check argument types inside MetaDataRef Lua API
* Fix "Ignoring CONTENT\_IGNORE redefinition" warning
* dropped items and falling nodes: Delete in 'ignore' nodes
* Move setlocale from Lua to C++
* Fix off-by-one in log output line length
* Fix buffer parameter not working in getMapSlice()
* Fix rounding error in g/set\_node caused by truncation to float
* Fix dancing text in text input fields
* Fix undefined behaviour on getting pointer to data in empty vector
* Fix wrong scrolling in text areas
* Builtin: Fix handle\_node\_drops crash with nil digger
* Damage: Remove damage ignore timer due to abuse potential
* Ensure no item stack is being held before crafting
* Several documentation additions, improvements
* core.rotate\_node: Run callbacks like with any regular placed node
* Biome dust node: Only place on 'walkable' cubic non-liquid drawtypes
* Make use of safe file writing in auth handler
* Add minetest.safe\_write\_file() API function
* Fix issue Minetest crash when custom font path is not exist
* Fix Settings tab formspec alignment
* Do not scale texture unless necessary
* httpfetch: Enable gzip support
* Fix day\_night\_ratio\_do\_override not being initialised server-side
* Fix default item callbacks to work with nil users
* Prevent from crafting non-existent, unknown items
* Profiler: Fix var args not being passed to callback register function
* Unkown nodes: Provide position on interact
* Fix attached particle spawners far from spawn
* Localplayer: Fix disable\_jump effect and standing node position
* Fix blocks written by vmanip not being marked as modified
* Set placer to nil instead of a non-functional one in item\_OnPlace
* Fix Rotate Node Placement
* ServerEnv: Clean up object lifecycle handling (item deletion)
* Fix the core.wrap\_text function
* Fix empty legacy meta being persisted
* Statbars: fix incorrect half-images in non-standard orientations
* Android stepheight: Only increase if 'touching ground'
* Fix Android node selection distance
* serialize: use a temporary for SerializeException
* Fix player coordinate rounding in collisionMoveSimple()
* Various crash and error fixes
* Fix for empty key/value when reading item string with wear but no metadata
* Fix render order of overlays
* Fix console resize issue when maximising game window
* Fix console not being properly resized after window size changed
* Verify HudSetParams input when hotbar textures are set
* (Re)spawn players within 'mapgen\_limit'
* Fix sending color codes to clients that don't support them

0.4.15 → 0.4.16
---------------

0.4.16 was released on June 3, 2017.

* Minimum version supported is now 0.4.11

### Features

* Add 2D sheet animations for nodes _(sfan5)_
* Drop client side chat prediction. No more messages shown to chat when you talk and you are disconnected. _(red-001)_
* Add particle animation, glow _(sfan5)_
* Server list: add ping indicators _(kilbith)_
* Server side occlusion culling _(lhofhansl)_
* New custom progress bar (you can customize it with texture packs) _(kilbith)_
* Implement delayed shutdown for server owners: /shutdown 60 => shutdowns in 1 min /shutdown -1 cancels it _(nerzhul)_
* Add support for requesting a reconnect and changing the shutdown message to /shutdown _(red-001)_
* Add a mapblock cache in MeshUpdateQueue to improve client rendering performance _(celeron55)_
* Player data can now be into database. This is an important change, players to files are always supported for this release but deprecated. Files backend for players will be removed in a future release. See [http://wiki.minetest.net/Database\_backends](http://wiki.minetest.net/Database_backends) for compat matrix and migration steps. _(nerzhul)_
* Sounds: add fading sounds _(Bremaweb, krock)_
* Save automatically window size when modified. This behaviour can be disabled in client settings _(nerzhul)_
* Add cancel button to password change formspec _(red-001)_
* Improve pause menu with more user friendly informations and update keys dynamicly depending on your configuration _(red-001)_
* Merge singleplayer & server tab on desktop clients _(octacian)_
* Add /clearinv chat command _(octacian)_
* Add keyword-based search to server-list and advance settings _(red-001, rubenwardy)_
* Add hardware-based itemstacks and node coloring _(juhdanad)_
* Undersampling which should make minetest run better on low end devices _(numberZero)_

### Cheat fixes

* Breath cheat is now definitively fixed. Hacked clients cannot ignore breath anymore. _(nerzhul)_
* Fix node damage cheat. They are now calculated server side. Hacked clients cannot ignore node damages anymore (fire, lava, cactus...). _(nerzhul)_
* Disallow dropping items while dead. _(sfan5)_
* Calculate maximum interact distance from wielded tool. _(sfan5)_

### Bug fixes and Improvements

* Little antispam fix _(nerzhul)_
* Fix a little bit fog calculations _(lhofhansl)_
* Fix player deletion problem when too many objects are in a mapblock _(nerzhul)_
* Better block sending priorities to send map to players _(???)_
* Sneaking changes _(krock, paramat, sfan5)_
* Huge ABM handling code performance improvement _(nerzhul)_
* Smooth lighting for all nodes _(numberZero)_
* Added mesh generation delay _(numberZero)_
* PostgreSQL bugfix on blocks deletion _(nerzhul)_
* Windows integration enhancements _(???)_
* Wieldmesh natural orientation _(kilbith)_
* Memleak fix on client disconnection _(nerzhul)_
* Various performance fixes _(???)_
* Fix Windows icon _(adrido)_
* Fix various minor memleaks _(nerzhul?)_
* Recent LuaJIT fixes _(nerzhul)_
* Reduce network packet reading/writing memory usage _(???)_
* Binding tab now doesn't exit game when used _(sofar)_
* Light update for mapblocks _(juhdanad)_
* Client: reduce fake object reactions in client event queue _(nerzhul)_
* Crashfix when reading schematic calls from API in some cases _(nerzhul)_
* Limit sound volume when incorrect value was set into config _(???)_
* Fix Cursor lock problem when window is inactive _(krock)_
* Particles are now sent to client regarding distance (huge performance improvement on particle servers) _(paramat)_
* Really disable minimap when disabled in configuration _(nerzhul)_
* Fix a damage bug when falling from a very high height _(red-001)_
* Various documentation fixes _(???)_
* Expose singlenode mapgen to menu _(nerzhul)_
* Dropdown menu selection fix _(red-001)_
* Tooltip display unification between tooltip\[\] and list\[\] _(krock)_
* ServerActiveObjects are now removed when overtaking map limits _(nerzhul, paramat)_
* Chat console height can now be set by the player. _(Shara RedCat)_
* Additional option added to node highlighting drop-down. _(Shara RedCat)_

### Client Modding

* Introducing Client-Side modding (CSM for the initiated). You can now have local mods to read various client data and handle different client events. This new modding step is very secure, you don't have access to all standard Lua API, just a subset, to protect your computers. Mods should be installed in @user\_path@/clientmods.
* You will also have access to Client side commands, starting with a dot.
* If you want to know more about CSM API, please look at [Client Side Modding documentation](https://github.com/minetest/minetest/blob/master/doc/client_lua_api.md)
* Added by nerzhul, red-001, bigfoot547, Dumbeldor and paly2.

### Server Modding

* Enable mod\_security by default
* Add minetest.player\_exists() _(rubenwardy)_
* Add player attributes backend. This permits modders to store misc player related data to core and retrieve it after player loading. The attribute save is done by core. _(nerzhul)_
* Add mod metadata API permitting mods to have a standard way to write their own data. We recommend you to use this instead of your custom files backend. _(nerzhul)_
* Add position & anchor attributes for formspecs _(adelcoding1)_
* Add minetest.spawn\_falling\_node call _(zaoqi)_
* Remove core.cause\_crash Lua call _(nerzhul)_
* Add on\_flood server Lua callback _sofar)_
* Add clouds API _(bendeutsch)_
* Add private node meta to prevent some informations to be leaked to client (example: chest contents) _(sfan5)_

### Other / Misc

* Redis backend authentication support _(sfan5)_
* PostgreSQL < 9.5 support _(???)_
* Code refactoring (Game, Environments) _(???)_
* Introduce clang-format on repository to check and reformat C++ code with our rules (~15% source code managed) _(nerzhul)_
* Move external libs outside of src/ to lib/ _(nerzhul)_
* Update jsoncpp embedded lib to last C++03 version (0.10.6) _(nerzhul)_
* Disable leveldb on Android _(Ekdohibs)_
* Implement daily gitlab package build for Debian/Ubuntu/Fedora _(nerzhul)_
* Translations updates _(Multiple people)_

### Minetest Game changes

0.4.14 → 0.4.15
---------------

0.4.15 was released on Dec 22, 2016.

No official changelog exists yet, however you can find an unofficial one here: [https://forum.luanti.org/viewtopic.php?p=243949#p243949](https://forum.luanti.org/viewtopic.php?p=243949#p243949)

0.4.13 → 0.4.14
---------------

0.4.14 was released on May 15, 2016.

### Features

* Add viewing range GUI setting (kilbith)
* New settings tab contain all possible settings (PilzAdam)
* WoW-style Autorun (Duane Robertson)
* Add server side ncurses terminal (est31)
* Add support for audio feedback if placing node failed (BlockMen)
* New 3D Mode: Pageflip (Dalai Felinto)
* Add Valleys mapgen (Duane Robertson)
* Add /admin command which says who the server admin is (Splizard)
* Add '/clearobjects quick' (kahrl)
* Minimap: show player markers (RealBadAngel)
* Add support for non-ASCII characters to chat console (ShadowNinja)
* Nodebox: Allow nodeboxes to "connect" (Auke Kok)
* Add option to disable entity selectionboxes (TriBlade9)
* Add option to change screenshot file format (kaeza)

### Bug fixes and Improvements

* Fix object position border checking (est31)
* Fix falling through nodes on world load (Christof Kaufmann)
* Add environment variable MINETEST\_WORLD\_PATH (SmallJoker)
* Fix crash regression when invsize formspec gets used (est31)
* Fix GUITable selection issues with trees (kahrl)
* Speed up and make more accurate relief mapping (RealBadAngel)
* Add option to give every object a nametag (BlockMen)
* Add support for limiting rotation of automatic face movement dir entities (sapier)
* Fix wield item glitch (RealBadAngel)
* Allow per-tiles culling (Auke Kok)
* Mapblock mesh: Eliminate meshgen lags (RealBadAngel)
* Fix jumping at node edge (gregorycu)
* Restore simple settings tab and add advanced settings as dialog (BlockMen)
* Mapblock mesh: Allow to use VBO (RealBadAngel)
* Update menu header image (Jean-Patrick Guerrero)
* Fix player dying on login (Ekdohibs)
* Mainmenu: Refactor tab UI code (Rui419)
* Fix hotbar placement on displays with low screen density (PilzAdam)
* Mainmenu: Unify favorite servers with main serverlist (kilbith)
* Builtin: Add basic\_privs setting (rubenwardy)
* Optimize default settings for Android build (Maksim Gamarnik)
* Fix locked hardware buttons on Android (Maksim Gamarnik)
* Disallow stacking items with different meta (hunterdelyx1)

### Modding

* Add /emergeblocks command and core.emerge\_area() Lua API (kwolekr)
* Add get\_biome\_id(biome\_name) callback (Duane Robertson)
* Added minetest.wallmounted\_to\_dir (Fernando Carmona Varo)
* Allow setting chunksize in core.set\_mapgen\_params (kwolekr)
* ABMs: Make catch-up behaviour optional (paramat)
* Decoration API: Add flag for placement on liquid surface (paramat)
* Add more ways to pass data to check\_player\_privs (Robert Zenz)
* Add option to disable backface culling for models (BlockMen)
* Schematics: Add core.place\_schematic\_on\_vmanip API (kwolekr)
* Add LuaSecureRandom (est31)
* Allow craft replacements to use groups (TeTpaAka)
* Add Lua interface to HTTPFetchRequest (Jeija)
* Implement AreaStore serialization (ShadowNinja)
* Add AreaStore custom ID API (ShadowNinja)
* Add an option to colorize to respect the destination alpha (Samuel Sieb)
* Lua\_api.txt: Add warnings of l-system lighting bug (paramat)
* Add \[resize texture modifier (SmallJoker)
* Make the inventory bar HUD take offset into account (rubenwardy)

### Mapgen

* Dungeongen: Remove floating frames (paramat)
* Blob ore: Fix partial blobs (paramat)
* Mapgen: Add 4D fractal mapgen (paramat)
* Mgfractal: Independent offset/slice params for mandelbrot and julia (paramat)
* Mapgen: Add global 'decorations' flag (paramat)
* Mgv5/v7/flat/fractal: More large pseudorandom caves (paramat)
* Mgfractal: Add 3D and 4D fractals (paramat)
* Mgvalleys: Add Dry Riverbeds (Duane Robertson)
* Mapgen: Spread both night and day light banks in spreadLight (kwolekr)
* Mgv7: Decrease cliff steepness (paramat)

### Other / Misc

* Clean up threading (ShadowNinja)
* Improve locale directory detection (est31)
* Add new ContentParamType2 "CPT2\_DEGROTATE" (est31)
* Refactor logging (ShadowNinja)
* Improve rollback database indexing (cheapie)
* Mgfractal: Add documentation to conf.example and settingtypes (paramat)
* Add the player name to dropped items (Robert Zenz)
* Implement OSX Travis builds (Pavel Puchkin)
* Simplify custom games packaging (Pavel Puchkin)
* New timer design (Auke Kok)
* Add option to not send pre v25 init packet (est31)
* Clean up Strfnd (ShadowNinja)
* Add CONTRIBUTING.md (Craig Davison)
* Mainmenu: Standardize the menu button order and sizes (SmallJoker)
* Android: Increase player\_stepheight for thicker snow nodebox (Maksim Gamarnik)

### Minetest Game changes

#### API changes

* A modding API was added to TNT, which allows mods to easily create explosion effects (red-001)
* A modding API was added to doors, which allows mods to create new doors that are feature-rich (sofar)
* A fence, wall, and fence gate API was added (sofar)
* A give\_initial\_items API was added (rubenwardy)

#### Interface changes

* Creative inventory now allows searching for nodes by name and description (kilbith)

#### Visual/Effect/Audio changes

* Several new textures were added by many different contributors (paramat, kilbith, sofar, kevdoy, Craig Davison, Wouters)
* Water texture alpha and water post effect color were changed (paramat)
* Steel door sounds were added (sofar)
* Flowers will wave when the waving plant shader is enabled (paramat)
* Doors are now made out of a single mesh and not two half nodes (sofar)

#### Mapgen/Landscape changes

* Grass can grow on sandy beaches and dunes (paramat)
* More flowers will grow in many biomes (paramat)
* Almost all biomes are now richer and more varied (paramat)
* Aspen trees were added to forests (sofar)
* Fallen logs were added (mgv5, mgv7), and mushrooms can grow on them (sofar)
* Dirt and sand blobs may appear in sandstone (paramat)

#### Gameplay changes

* Book interface was entirely rewritten to allow for proper pages and wrapping (kilbith, tenplus1, mt-modder)
* A metal sign was added, as well as a steel ladder (kilbith)
* mushroom spores were removed (sofar)
* a metal (locked) trapdoor was added (sofar)
* books can be copied in the craft grid (sofar)
* A new permanent flame node was added, as well as "flint and steel" (paramat, kilbith)
* Moss can grow on cobblestone if it gets wet (paramat)
* TNT was largely rewritten and has many new effects and behaviors (red-001, sofar)
* Stone walls were added for all cobble stone types (sofar)
* A simple Fence gate was added (sofar)
* The boat is now slightly faster (paramat)

0.4.12 → 0.4.13
---------------

0.4.13 was released on August 20, 2015.

### Features

* Add camera smoothing and cinematic mode (F8) (rubenwardy)
* Radius parameter for /deleteblocks here (SmallJoker)
* Save creative\_mode and enable\_damage setting for each world in world.mt (fz72)
* Configurable automatic texture scaling and filtering at load time. (Aaron Suen)
* Connect rails with connect\_to\_raillike and shorten the codes (SmallJoker)
* Clouds: Make cloud area radius settable in .conf (paramat)
* Added hour:minute format to time command (LeMagnesium)
* Add mod security (ShadowNinja)
* Add texture overriding (rubenwardy)
* Improved parallax mapping. Generate heightmaps on the fly. (RealBadAngel)
* Make attached objects visible in 3rd person view (est31)
* Remove textures vertical offset. Fix for area enabling parallax. (RealBadAngel)
* Add minimap feature (RealBadAngel, hmmmm, est31, paramat)
* Add new leaves style - simple (glasslike drawtype) (RealBadAngel)
* Add ability to specify coordinates for /spawnentity (Marcin)
* Add antialiasing UI setting (Mark Schreiber)
* Add wielded (and CAOs) shader (RealBadAngel)
* Add map limit config option (rubenwardy)

### Bug fixes and Improvements

* Add count based unload limit for mapblocks (est31)
* Kick players when shutting down server or on Lua crash (nerzhul)
* Fix relief mapping issues (RealBadAngel)
* Improve group-based connection between raillike nodes (BlockMen)
* Use skin font for usernames (fixes #2363) (BlockMen)
* Fix some memory leaks on packet sending. (nerzhul)
* Fix android build (nerzhul)
* Fix serialization of floating point numbers (ShadowNinja)
* Disallow object:remove() if the object is a player (Kahrl)
* Fix wrapDegrees family of functions (Zeno)
* Optimise MapBlockMesh related functions (gregorycu)
* Fix minor memory leak (Android) (Zeno)
* Fix occlusion (Miguel Almeida)
* ClientInterface::getClientIDs doesn't need a std::list. Use a std::vector for better perfs (nerzhul)
* Fix some rendering glitches (BlockMen)
* Fix mapgen using unitialised height map values (Zeno)
* Fix Android text bug (no text displaying) (Zeno)
* Improve Clouds::render mathematics (nerzhul)
* For usages of assert() that are meant to persist in Release builds (when NDEBUG is defined), replace those usages with persistent alternatives (Zeno)
* Fix RUN\_IN\_PLACE broken due to invalid usage of assert (sapier)
* Respect game mapgen flags and save world noise params (ngosang)
* Don't use luaL\_checkstring to read node names, it's only for arguments (ShadowNinja)
* Heightmaps: Fix uninitialised values in mgv5/mgv6. findGroundLevel: Return -MAP\_GENERATION\_LIMIT if surface not found (paramat)
* Make the dummy backend only look up blocks once (ShadowNinja)
* Fix unitialized data when creating TOSERVER\_INIT packet (nerzhul)
* Fix memleak pointed by issue #2439. Also change bzero to memset. bzero doesn't work on windows (nerzhul)
* Stop formspecs closing with double-click in empty area (Zeno)
* Ensure that heightmap is initialized before use (Zeno)
* lua\_api/l\_mapgen: Fix overlapping areas of minetest.generate\_ores/decorations (paramat)
* Mgv6: Fix uninitialised heightmap used by cavegen (paramat)
* Disable double-click -> ESC translation for main menu (Zeno)
* If player is dead, permit it to respawn, even if damages are not enabled (nerzhul)
* Android: Fix auto-entry of server address and port in mainmenu (est31)
* Fix various damage related bugs (client-side) (Zeno)
* Minor bug fix (lag between damage flash and hearts updating) (Zeno)
* Fix game minetest.conf default settings (est31)
* Optimize minetest.get\_(all)\_craft\_recipe(s) (gregorycu)
* Fix composite textures with texture\_min\_size (Aaron Suen)
* Protect Player::hud from concurrent modifications (nerzhul)
* Fix minetest.get\_craft\_recipe function (est31)
* Fix set\_bits (kwolekr)
* Fix usage of destroyed mutex (kwolekr)
* Fix crash caused by null texture in GUI formspec/HUD. (Aaron Suen)
* Fix players spawned at (0,0,0) in some rare cases instead of static\_spawnpoint (nerzhul)
* Crafting speedup (est31)
* Fix uninitialized variabled in ConnectionEvent (nerzhul)
* Fix a rare crash case un SendPlayerHP (nerzhul)
* Schematics: Fix core.schematic\_create() (kwolekr)
* fix infinite spawners (obneq)
* Disable connection timeout for singleplayer and server tabs (est31)
* Fix mod store rating (ShadowNinja)
* Fix sign-compare compiler warnings in mg\_ore.cpp (ShadowNinja)
* Fix player pitch and yaw not being set properly (Kevin Ott)
* Fix fast leaves with texture\_clean\_transparent enabled. (Aaron Suen)
* Fix minetest.clear\_\* creating new LOCAL table instead of clearing the existing one. (Tomas Brod)
* Noise: Fix PcgRandom::randNormalDist() when range contains negative numbers (kwolekr)
* Add a check for animation when getting an extruded mesh (Kevin Ott)
* Stop NetworkPacket methods from producing bloated packets (Jay Arndt)
* Replace Wieldmesh::setItem assertion that could be triggered by the server with an error (kwolekr)
* Ensure that Map::findNodesWithMetadata() reports nodes strictly within the node-granular area (kwolekr)
* Fix typo in WieldMesh::setItem() (kwolekr)
* Don't crash if an item gets dropped into unloaded space (tenplus1)
* ANDROID: Do not limit situations where fast is enabled (Zeno)
* Fix current mod name change missed during rebase (ShadowNinja)
* Noise: Fix interpolation at negative coordinates (kwolekr)
* (Android) Only simulate holding down fast key if fast\_move is toggled to true (Zeno)
* dofile error reporting for syntax errors (est31)
* Don't crash when saplings try to grow on unknown nodes (y.st, ShadowNinja)
* Remove unneccessary space for tab completion (Nathaniel Olsen)
* Fix some issues with animations, and allow non-looped animations to be defined (MirceaKitsune)
* Fix bug when craft input isn't replaced (TeTpaAka)
* Fix string conversion error message (est31)
* Fix bugs in mainmenu (kilbith, jp)
* Fix single click world select (est31)
* Shaders fixes and cleanup relief mapping code. (RealBadAngel)
* Fix missing check for 0 in craft replacements (TeTpaAka)
* Craftdef: Use numbers instead of iterators (est31)
* Fix attempt to start a world when no world is selected/created (kilbith)
* Fix endless loop since grandparent commit (est31)
* Fix damage flash when damage disabled (kwolekr)
* Add more robust error checking to deSerialize\*String routines (kwolekr)
* Fix minetest.get\_(all)\_craft\_recipe(s) regression (est31)
* Fix FSAA dropdown option reset after changing another dropdown option (kilbith)
* Fix MSVC number conversion warning (SmallJoker)
* Fix srp.cpp:815 leak (est31)
* Fixed minimap memory leak (Břetislav Štec)
* Android: Fix minor makefile bugs (est31)
* src/network/connection.h: Fix race condition (Břetislav Štec)
* src/environment.cpp: Fix NULL pointer dereference (Břetislav Štec)
* Improve accuracy and safety of float serialization (kwolekr)
* src/client.cpp: Fix mapper memory leak (Břetislav Štec)
* src/wieldmesh.cpp: Fix mesh extrusion memory leak (Břetislav Štec)
* Android: fix sound issue, and gitignore (est31)
* src/client/tile.cpp: Fix reference counting (Břetislav Štec)
* Fix "bouncy" blocks (Miner59)
* src/util/numeric.{cpp,h}: Fix FacePositionCache data race (Břetislav Štec)
* Fix tiling issues for PLANTLIKE and FIRELIKE with FSAA (RealBadAngel)
* connection: Make assertions non-fatal for received data (kwolekr)
* Fix critical vulnerabilities and bugs with NetworkPacket (kwolekr)
* Fix BufferedPacket race condition (fixes #2983) (kwolekr)
* Fix detection of sneaking node This fixes bug 1551 (gregorycu)
* Fix camera updates being toggled by N key in release mode (#2762) (Kahrl)
* Fix segfaults caused by the Environment not being initialized yet (rubenwardy)
* Display Lua memory usage at the time of Out-of-Memory error (kwolekr)
* Make NetworkPacket respect serialized string size limits (kwolekr)
* Fix intlGUIEditBox leak and uninitialized value in Mapper (reported by valgrind) (Kahrl)
* Fix Lua PcgRandom (est31)
* Fix segfault caused by a8e238ed06ee8285ed4459e9deda3117419837f6 (Perttu Ahola)
* Fix sneaking (fixes #665 and #3045) (BlockMen)
* Rollback: Fail on bad precondition instead of causing assertion error (kwolekr)
* Fix inventory replace bug (est31)
* Fix indianred and indigo of color-string (Rui)
* Optimizations (multiple)

### Modding

* Add mod.conf file support - allows mods to specify a mod name for now (kaeza)
* Add find\_nodes\_in\_area\_under\_air (nerzhul, Zeno)
* Add core.register\_schematic() and cache schematics on use (kwolekr)
* Schematics: Reorganize (de)serialization and add Lua serialization API (kwolekr)
* Add minetest.global\_exists() (ShadowNinja)
* Fix pathfinder to produce more useful paths (obneq)
* Add core.find\_nodes\_with\_meta() script API (kwolekr)
* Schematics: Add per-node force placement option (kwolekr)
* is\_player() is no player-only function (est31)
* Add code to support raillike group names (Novatux)
* Add get and set functions for the nametag color (TeTpaAka)
* Add minetest.register\_on\_punchplayer (Brandon)
* Schematics: Fix probability values for .mts version 1 (kwolekr)
* Add core.mkdir (ShadowNinja)
* Add core.request\_insecure\_environment() (ShadowNinja)
* Add core.get\_dir\_list (ShadowNinja)
* SAPI: Accept either ARGB8 table or ColorString to specify colors (kwolekr)
* Add some missing getter functions to the lua API (TeTpaAka)
* Decrease minetest.after globalstep lag (HybridDog)
* Add return list of individual counts to find\_node\_in\_area (TeTpaAka)
* Add minetest.register\_on\_player\_hpchange (TeTpaAka)
* Add list-rings (est31)
* Add Lua errors to error dialog (rubenwardy)
* Biome API decorations: 'spawnby' searches a 3D neighbourhood (paramat)
* Make acc and vel deprecated in add\_particle and search for acceleration and velocity instead (TeTpaAka)
* Added get\_player\_velocity() method. Fixes #1176 (Elia Argentieri)
* Allow random menu images for games (sfan5)
* Document game main menu image system (est31)
* Add AreaStore data structure (est31)
* Actually document what minetest.is\_protected should do (est31)
* SAPI: Track last executed mod and include in error messages (kwolekr)

### Mapgen

* Mgv5: Remove blobgen. Remove crumble and wetness noises (paramat)
* Biome API: Re-calculate biome at every surface in a mapchunk column (paramat)
* Mgv6: Add heightmap. Do not make large caves that are entirely above ground (paramat)
* Cavegen, mgv5: Cleanup code (paramat)
* Fix memory leak in MapgenV6 (Zeno)
* Biome API: Enable decorations
* Mgv5/mgv7: Add desert temples if desert stone detected in mapchunk (paramat)
* mg\_decoration: Raise highest allowed deco top to max edge of voxelmanip (paramat)placed on water (paramat)
* Mgv6: Remove addDirtGravelBlobs, replaced by blob ore in Minetest Game (paramat)
* Mgv5/mgv7: Sprinkle dust from full\_node\_max.Y if chunk above is generated (paramat)
* Mgv7: 1 up , 1 down overgeneration for chunk border continuity (paramat)
* lua\_api/l\_mapgen: generate\_ores/decorations: make p1, p2 optional (paramat)
* ObjDefManager, Mapgen SAPI: Huge refactoring (kwolekr)
* Treegen: Add pine tree. Force place trunks (paramat)
* Mgv6: Add optional snow biomes (paramat)
* Mgv6: Fix taiga, allow pine tree spawning on snowblocks (paramat)
* Mgv5/v7: Add check for water for deciding biome node stability (paramat)
* Mgv5: Fix above/below ground spawn when water level is altered (paramat)
* Biome API: Add biome-specific river water (paramat)
* Noise: Correct noise objects created with invalid dimensions (kwolekr)
* Ore: Add biomes parameter (kwolekr)
* Noise: Add noise unittests (kwolekr)
* Mapgen v5/6/7: Cleanup node resolver and aliases (paramat)
* Noise: Make buffer size parameters unsigned (kwolekr)
* Mapgen v5/v7: Detect sandstone, enable sandstone brick dungeons (paramat)
* SAPI/Noise: Add PerlinNoiseMap:getMapSlice() function (kwolekr)
* Mgv5/v7: Fix generateBiomes biome recalculation logic Biomegen down to y = -192 for mgv5 deep oceans. Improve code (paramat)
* Biome API, mgv7: Increase heat/humidity spreads. Improve mgv7 noise parameters (paramat)
* Mgv6: Enable snowbiomes by default. Double biome noise spread. 3 octaves, 0.5 persistence for humidity (paramat)
* Mgv5/mgv7: Trigger biome recalculation at underwater surfaces (paramat)
* Minimal: Edit mapgen aliases. Use blob ore for clay, update other ores. Update simple biomes. Cleanup code (paramat)
* Minimal: Add snow biome and jungleleaves nodes. Add mapgen aliases (paramat)
* Biome API: Enable biome generation to lower world limit (paramat)
* Mgv6: Don't create air gap in tundra at y = 48 in custom high terrain (paramat)
* Biome API: Add noise defined biome blend (paramat)
* Mapgen objects: Enable heatmap and humidmap for all biome api mapgens (paramat)
* Mgv7: Edit noise parameters. Fewer octaves, larger spreads. (paramat)
* Mgv5/mgv7 caves: Remove sand found in underground tunnels (paramat)
* Biome API: Increase heat and humidity noise spreads to 1000 (paramat)
* Cavegen: Cleanup code. Define constant for MGV7\_LAVA\_DEPTH (paramat)
* Mgv7: Lower base of mountain generation to -112 and define constant (paramat)
* Mgv7: Auto-set lowest mountain generation level (paramat)
* Cavegen: Mgv6: No small caves entirely above ground (paramat)
* Mgv7: Use density noise + density gradient for mountain terrain (paramat)
* Treegen: Rename pine tree mapgen alias (paramat)
* Biome API: Make fallback biome stone and water, disable filler (paramat)
* Cavegen V6: Make all caves consistent with 0.4.12 stable (paramat)

### Other / Misc

* Start adding utf-8 support (est31, Ilya Zhuravlev)
* Unit tests must be done at integration process. (nerzhul)
* Improve FindIrrlicht.cmake module (Markus Koschany)
* Rename --do-unittests to --run-unittests as @Zeno- and @sfan5 requested (nerzhul)
* Clean up database API and save the local map on an interval (ShadowNinja)
* Don't start a server for map migration (ShadowNinja)
* Dungeongen: Optionally set ignore to be untouchable to disable floating dungeons (paramat)
* Finer progress bar updates when initializing nodes (est31)
* Minor cleanup: game.cpp (Zeno)
* Add support for the PCG32 PRNG algo (and associated script APIs) (kwolekr)
* Change filename of screenshots to something more human readable (Zeno)
* Clean scaling pre-filter for formspec/HUD. (Aaron Suen)
* Remove errorstream logging on password change (est31)
* Add reason to kicked log message and use present tense (est31)
* RotateAlongYAxis: For facedir case, return if param2 >= 4 (paramat)
* Change lower limit of display\_gamma to 1.0 (linear light) (Zeno)
* More reliable serverlist behaviour (HybridDog)
* Close keybind settings menu with esc (est31)
* Disable mesh cache by default (est31)
* Set server\_announce to world.mt and respect modes when changing game (Sokomine)
* Use minetest logging facilities for irrlicht log output (ShadowNinja)
* Display an access denied message when client detects a server timeout (Kahrl)
* Change texture pack description file name (ExcaliburZero)
* Refactor particle code to remove the while loops (TeTpaAka)
* MoveItemSomewhere double bugfix (est31)
* Remove profiler.h include where it's not needed. Remove some unreachable and very old code (nerzhul)
* Ask auth handler to create auth when a default password is set (est31)
* Optional reconnect functionality (est31)
* Fix documentation of dedicated\_server\_loop (est31)
* Remove drivers dropdown in the settings tab (kilbith)
* Cleanup server addparticle(spawner) by merge two identical functions. (nerzhul)
* Precalculate mapblock relative size. This permit to remove many s16 calculs on runtime (nerzhul)
* Android: Add githash header to spare rebuilds after new commits (est31)
* Prepend "Lua: " before lua exceptions src/server.cpp src/emerge.cpp (Břetislav Štec)
* Improve Script CPP API diagnostics (kwolekr)
* Initialize random for verification key generation too (est31)
* game.cpp: Update cached settings (est31)
* SAPI: Disable unlockable time profiling (kwolekr)
* Client: disable mmdb modstore (est31)

0.4.11 → 0.4.12
---------------

0.4.12 was released on February 18, 2015.

### New features

* Add player direction to debug text (_yamanq_)
* Reorganized client and server tabs (_kilbith_)
* Implemented DPI automatic detection on X11 (_sapier_)

### Map generation

**v5:**

* Caves check for biome nodes, only excavate stone under water level (_paramat_)
* Unease caves noises, use 0.3.x parameters (_paramat_)
* Blobgen after cavegen (_paramat_)
* Biomegen: remove “is replaceable content” bool (_paramat_)

### Tweaks

* Increased step height on Android (_sapier_)
* Increased default `font_size` (_BlockMen_)
* Improved minetest.desktop, added German and French text to minetest.desktop (_nerzhul_)
* More consistent progress bar (_sapier_)

### Bug fixes

* Fixed font\_size under Windows (_BlockMen_)
* Ignored old entities from 0.3 (_Novatux_)
* Fixed FTBFS on GNU/Hurd platform (_apoleon_)
* Modified Y positioning of health/breath statbars to prevent overlapping with hotbar (_kwolekr_)
* Fixed memory leaks related to gettext (_ShadowNinja_)
* Give full breath after death (_SmallJoker_)
* Fix `NDT_GLASSLIKE` normals (_kahrl_)
* Water flowing fixes (_gregorycu_)
* Compiler tweaks and warning fixes (_ShadowNinja_, _kwolekr_)
* Fix imprecise serialization of large numbers (_ShadowNinja_)
* Fix performance regression (_Zeno-_)
* Fix getCraftRecipe returning wrong recipes (_sapier_)
* Fix unused (and so, broken) enable\_rollback\_recording. (_nerzhul_)
* Fix .zip extraction (mod store) (_ngosang_)
* Fix translation memory leak (_ShadowNinja_)
* Fix F7 crash (_nerzhul_)
* Fixes to default screenshots in mainmenu (_Rui914_)
* Fix map\_seed not changed when creating a new world after login to another (_fz72_)
* Add modname convention checking, fixes issues with mod enabling (_est31_, _Novatux_)
* Fix problems related to still receiving damage after dying (_SmallJoker_, _gregorycu_)

* Add `vein` and `blob` ore type (_kwolekr_)
* Change assignment to global in a function to warning (_rubenwardy_)

### Vanilla game changes (minetest\_game)

#### Gameplay

* Mossy cobblestone can now be smelted to stone (_MT-Modder_)
* Added straw, crafted with 9 wheat (_kilbith_)
* Added obsidian and obsidian brick stairs and slabs (_CraigyDavi_)

#### Visuals

* Many new textures renewed (_kilbith_)
* Changed furnace fire icons (_Kalabasa_)
* Added fancy inventory for bones (_CraigyDavi_)

### Master server (server list)

* Announce MIN/MAX protocol version to server list (_est31_)

0.4.10 → 0.4.11
---------------

0.4.11 was released on December 24, 2014.

### New features

**Big gameplay changes**

* Added mapgen v5 _(paramat)_
* Added enable\_build\_where\_you\_stand option _(Sokomine)_

**Smaller gameplay tweaks**

* Added inventory right click drag and drop _(sruz25, Zeno)_
* Remove buildable\_to nodes without dropping item when replaced by a falling node _(Casimir)_

**Visual changes**

* Reduced time of red screen when damaged _(SmallJoker)_
* Added video driver selection to settings menu _(sapier, webdesigner97)_
* Removed alpha channel from screenshots _(BlockMen)_
* Added node highlighting _(RealBadAngel)_
* Added configurable selection box width. Min width = 1, max = 5 _(TriBlade9)_
* Changed default halo.png for better visibility _(RealBadAngel)_
* Added in-game key change menu _(Mushiden)_
* Improved lighting of the wielded item _(kahrl, RealBadAngel)_
* Increased step smoothing to fit 1:1 stairs _(Calinou)_
* Scale form elements consistently using new font engine by sapier _(Zefram)_
* Made dropped items larger and rotate faster _(Calinou)_
* Increase third person view distance _(Calinou)_
* Made directional fog colors respect tonemap _(Taoki)_
* Display serverlist flags as icons _(kahrl, kilbith, VanessaE et al.)_

**Build system changes**

* Added ZLIBWAPI\_DLL and LEVELDB\_DLL CMake options _(sfan5)_
* Removed legacy MINGWM10\_DLL CMake option _(sfan5)_
* Changed build directory for build bots to '\_build' to prevent removal of Android build files _(sfan5)_
* Updated 32-bit build bot (OpenAL updated, zlib updated) _(sfan5)_
* Added -win64 suffix to build bots for 64-bit Windows builds _(sfan5)_
* Updated the cURL the buildbot uses to 7.38.0 _(sfan5)_
* Added Android Makefile support for builds without LevelDB _(sapier)_
* Improved Travis CI configuration _(Mikaela Suomalainen)_
* Added gettext to Travis build _(ShadowNinja)_
* Build for win32 & win64 on Travis too _(sfan5)_
* Update MinGW toolchain downloads used by Travis _(sfan5)_
* Fixed various build issues on Windows/MSVC _(SmallJoker)_, Android _(sapier, Kodexky)_, Mac OS X _(Pavel Puchkin)_

**Logistical changes**

* Don't unload blocks if save failed _(kwolekr)_
* Don't copy back already generated blocks on map generation _(kwolekr)_
* Moved MapBlock (de)serializing code out of Database class _(sfan5)_
* Don't include cmake\_config\_githash.h into files that don't need it _(sfan5)_
* Moved #includes from version.h to version.cpp _(kahrl)_
* Improved timeout calculation when packets are lost _(sapier)_
* Refactored a section of ban.cpp _(Selat)_
* Allowed use all 6 faces for special tiles _(RealBadAngel)_
* Saved previously generated blocks on Mapgen blitback _(kwolekr)_
* Refactored Settings _(ShadowNinja, Zeno, kwolekr)_
* Added setting groups (used for NoiseParams) and multiline entries _(kwolekr)_
* Added NodeResolver and cleaned up node name -> content ID resolution system _(kwolekr)_
* Added support for eased 3d noise _(kwolekr)_
* Added notice when only minimal is installed _(rubenwardy)_
* Split up mapgen.cpp _(kwolekr)_
* Refactored the\_game _(Zeno)_
* Added Generator Element Management framework _(kwolekr)_
* Cleaned up rollback _(ShadowNinja)_
* Refactored main.cpp _(Zeno)_
* Rewrote generate notification mechanism _(kwolekr)_
* Rewrote fs::GetDirListing(file), fixing a potential buffer overflow _(kahrl)_

**Other changes**

* Removed math mapgen _(proller)_
* Removed indev mapgen _(proller)_
* Removed proller from credits _(proller)_
* Updated default control documentation _(BlockMen)_
* Made lighting CPU-only by removing finalColorBlend implementation from shaders _(RealBadAngel)_
* Added `/dummyball <count>` command to the minimal game _(kahrl)_
* Made the LuaJIT exception wrapper handle more exceptions _(kahrl)_
* Added missing doc for minetest.get\_us\_time() _(sapier)_
* Made HTTPFetch use the configured bind\_address _(ShadowNinja)_
* Made config compatible with C++ 2011 _(donat\_b)_
* Added a .mailmap file _(Stefan Beller)_
* Search for games using $MINETEST\_SUBGAME\_PATH _(David Thompson)_
* Added Indonesian language _(srifqi)_
* Updated translations _(kilbith, ShadowNinja)_
* Replaced setting unlimited\_player\_transfer\_distance with player\_transfer\_distance _(SmallJoker)_
* Added last\_login field to auth.txt _(Ryan Newell)_
* Added tooltips to main menu games button bar _(Wuzzy)_
* Added option 'eased' to NoiseParams _(SmallJoker)_
* Added (optional) client-side saving of server map to disk _(sfan)_
* Added name of node 'pointed at' to debug _(rubenwardy, Zeno)_
* Added space between client names in status text _(Muhammad Rifqi Priyo Susanto)_
* Disabled loading .mtl files _(RealBadAngel)_
* Made biome heat and humidity noise parameters user-configurable _(kwolekr)_
* Added paste command (Ctrl-V) in chat console _(kahrl)_
* Responsive tooltip offset for Android _(Kodexky)_
* Allowed footstep sounds to play for liquid and ladder nodes _(Taoki)_
* Added basic support for generating API documentation using Doxygen _(Jürgen Doser)_
* Set WM\_CLASS window hint for Xorg _(kwolekr)_

### Performance

* Disabled preload\_item\_visuals by default _(ShadowNinja)_
* Sped up mapblock\_mesh _(RealBadAngel, Zeno)_
* Implemented caching of facedir rotated meshes (controlled by enable\_mesh\_cache setting) _(RealBadAngel)_
* Removed most exceptions from getNode() (and variants) _(Zeno)_
* Sped up removing a node (less block mesh updates) _(RealBadAngel)_
* Reduced number of extrusion meshes to (usually) 5 instead of one per item _(kahrl)_
* Improved VoxelArea variable locality _(Wouters Dorian)_
* Optimised functions from CNodeDefManager and VoxelManipulator _(Zeno)_
* Optimised serialization, for example by using machine native byte swapping if available _(Rafael Reilova)_
* Optimised main client loop _(Zeno)_
* Optimised noise implementations _(kwolekr)_
* Optimized getLight() by 2x _(Zeno)_
* Stopped liquid queue from eating up more and more RAM; also liquid\_loop\_max now defaults to 100000 _(Zeno, celeron55)_
* Changed TileSpec::frames to be std::vector not std::map _(unknown, Zeno)_

### Bug fixes

* Fixed face shading issues _(RealBadAngel)_
* Fixed crash reported here: [https://forum.luanti.org/viewtopic.php?f=6&t=9726](https://forum.luanti.org/viewtopic.php?f=6&t=9726) _(Novatux)_
* Fixed flipped textures for drawtype "glasslike" _(sapier)_
* Fixed indexing error in timer processing _(Zefram)_
* Made tooltip\_show\_delay=0 work _(Zefram)_
* Fixed error handling on inconsistent client ready message _(sapier)_
* Fixed texture hack in fences _(RealBadAngel)_
* Fixed texture glitches for plants with visual scale > 1.0 (jungle grass) _(RealBadAngel)_
* Fixed makeCuboid to apply rotations to all faces when 1 tile is given _(RealBadAngel)_
* Fixed display of interior of glasslike\_framed node when its not defined _(RealBadAngel)_
* Fixed LuaVoxelManipulator memory leak _(Zeno-)_
* Fixed seeds corrupting world creation menu formspec _(ShadowNinja)_
* Made face shading correct for all possible lighting modes _(RealBadAngel)_
* Fixed liquid sources and flowing surfaces having different brightness _(RealBadAngel)_
* Fixed main menu game initialization _(BlockMen)_
* Made safeWriteToFile() remove empty file if there is an error _(Selat)_
* Don't call player events without having player to do a event for _(sapier)_
* Fixed "ghost" blocks if block update is "on wire" while player digs nodes _(sapier)_
* Added player name length checks _(sapier)_
* Fixed chat messages capturing mouse interactions for menu/formspecs _(sapier)_
* Fixed segmentation fault if popping from empty stack (L-system trees) _(Zeno)_
* Fixed interlaced 3D mode second image being flipped when compiling with Irrlicht 1.8+ _(sapier)_
* Fixed only one texture being updated on window resize, breaking side-by-side and top-bottom 3D modes _(sapier)_
* Fixed access to invalid data when receiving empty packets _(sapier)_
* Fixed some locking bugs _(kahrl, ShadowNinja)_
* Use round if falling node is misplaced _(SmallJoker)_
* Fixed and simplified player modification checks _(ShadowNinja)_
* Fixed unit tests failing if IPv6 not available _(Zeno)_
* Fixed wield mesh getting clipped by camera far value _(kahrl)_
* Fixed raillike rendering bug on Android _(Kodexky)_
* Don't corrupt stepheight when setting other properties _(Ciaran Gultnieks)_
* Fixed mouse events getting passed from a table's scrollbar to its parent _(kahrl)_
* Fixed minetest.place\_schematic() when defined by a Lua table _(kwolekr)_
* Ignore .name directories and files in main menu _(SmallJoker)_
* Fixed some typos _(sapier, rubenwardy, William Teder, ShadowNinja, kahrl, Zeno)_

* New drawtypes: mesh _(RealBadAngel)_, firelike _(TriBlade9)_, glasslike\_framed\_optional _(BlockMen)_
* New texture modifiers: ^\[mask _(sfan5)_, ^\[colorize _(BlockMen)_
* New formspec element: scrollbar _(sapier)_
* Allowed non-integer sizes for item\_image\[\] _(Zefram)_
* Added texture grouping via ( ... ) _(sfan5)_
* Added mod profiling support _(sapier)_
* Added compression API _(ShadowNinja)_
* Added update of the Mapgen VoxelManipulator on buffer invalidation _(kwolekr)_
* Added LuaVoxelManip methods: get\_node\_at() and set\_node\_at() _(kwolekr)_
* Simplified and optimized schematic replacements _(ShadowNinja)_
* Made dump's output prettier _(ShadowNinja)_
* Added collision\_box node property _(RealBadAngel)_
* Added warning when creating a global variable (unless it has the same name as the current mod) _(ShadowNinja)_
* Added minetest.copy\_table(table), vector.apply(v, func) and math.sign(x, tolerance) _(SmallJoker)_
* Improved documentation for remove\_item, string\_to\_pos, dig\_node, on\_step, get\_meta _(Ciaran Gultnieks)_
* Added minetest.clear\_registered\_biomes() _(kwolekr)_
* Added new noise parameters: flags and lacunarity _(kwolekr)_
* Added support for NoiseParams in minetest.get\_perlin() _(kwolekr)_
* Exposed mapgen chunksize in on\_mapgen\_init callbacks _(kwolekr)_

### Vanilla game changes (minetest\_game)

#### Gameplay

* Made opened trapdoor climbable _(Zefram)_
* Made doors form double-doors with other doors of any kind _(Zefram)_
* Added filled buckets to creative inventory _(Zefram)_
* Enabled dungeon generation by default _(Amaz1)_
* Improved handling of boats _(paramat)_
* Added pine trees, with needles, tree, wood and saplings _(paramat, PilzAdam)_
* Made player-placed leaves not decay _(PilzAdam)_
* Reworked infotext of furnace _(PilzAdam)_
* Added Obsidian Bricks _(HybridDog)_
* Changed controls of screwdriver _(tenplus1, PilzAdam)_

#### Visuals

* Changed ingot textures _(Nore)_
* Made TNT smoke round _(ShadowNinja)_
* Made fire use new fire drawtype _(BlockMen)_
* Added new textures for cobble and furnace _(Neuromancer56, BlockMen)_
* Added new textures for grass _(BlockMen, Philipbenr)_
* Made glass use new, optional framed drawtype _(BlockMen)_
* Added new textures for apples, chests, dirt, desert stone bricks, HP bar, snowballs _(BlockMen)_
* Added new textures for ores, vessels, grass (plant), leaves and ladders _(kilbith)_
* Added new textures for flowers _(RHRhino)_
* Added new textures for doors _(Amaz1)_
* Changed soil textures to use an overlay over default\_dirt.png _(PilzAdam)_
* Added new textures for soil _(PilzAdam)_
* Added a bit white to crack texture _(ShadowNinja)_
* Made signs a 3D box, instead of just a 2D plane _(Calinou)_

#### Bug fixes

* Fixed crafting recipe for iron bars _(BlockMen)_
* Added protection support to TNT _(BlockMen)_
* Retain sign text when editing is aborted via Esc _(Zefram)_
* Fixed Desert Sand Soil dropping itself _(Amaz1)_
* Consistently use group:stick in tool recipes _(Zefram)_
* Fixed boats flying upwards _(paramat)_
* Fixed hoes wearing out in creative mode _(BlockMen)_
* Fixed brown dye being in yellow color group _(BlockMen)_
* Fixed player staying attached when removing boat _(BlockMen)_
* Removed “leaked” global variables _(PenguinDad, kaeza, CraigyDavi, PilzAdam)_
* Fixed various bugs with fire sounds _(PilzAdam)_
* Fixed possible stacking of books in bookshelf _(MT-Modder)_
* Fixed soil drying out if nearby water is unloaded _(PilzAdam)_
* Fixed rotating of locked doors to bypass them _(PilzAdam)_
* Fixed screwdriver overriding bits in param2 that are not used for rotation _(PilzAdam)_

#### Miscellaneous

* Added enable\_tnt setting _(ShadowNinja, Yepoleb)_
* Optimized TNT explosion _(ShadowNinja)_
* Added option for custom opening and closing sound for doors _(Jat15, Zefram)_
* Removed generation of flowers, papyrus, cactus and grass (plant) generation from other mapgenerators than v6 _(paramat)_
* Removed ore definitions for indev mapgen _(paramat)_
* Added all saplings to group sapling _(PilzAdam)_
* Allowed the group book to be placed in bookshelf _(PilzAdam)_
* Added a minetest.conf.example with all settings from minetest\_game, that can be changed in mintest.conf _(PilzAdam)_
* Removed remains of weather and finite liquids _(PilzAdam)_
* Restructured and moved furnace code to furnace.lua _(PilzAdam)_

### Master server (server list)

* Announce mg\_name from map\_meta.txt instead of minetest.conf _(kahrl)_

0.4.9 → 0.4.10
--------------

0.4.10 was released on July 6, 2014.

### New features

**Big gameplay changes**

* Added third person view _(BlockMen)_
* Removed finite liquid and weather _(proller)_

**Smaller gameplay tweaks**

* Create bones only when the player's inventory is not empty & remove the bones when emptied _(arsdragonfly)_
* Made pause menu actually pause singleplayer game and use lower maximum FPS in it _(celeron55)_
* Prevented placing node when player would be inside new node _(BlockMen)_
* Drop an item instead a stack while sneaking _(Lord89James)_
* Added support for exiting formspecs by doubleclicking outside _(sapier)_

**Logistic changes**

* Made build prefer pkg-config for freetype2 detection _(hasufell)_
* Added function to deregister a profiler from profiler list _(sapier)_
* Made MutexQueue use jsemaphore for signaling _(sapier)_
* Added maximum recursion depth to read\_json\_value _(ShadowNinja)_
* Made default User-agent follow RFC 2616 _(ShadowNinja)_
* Include system info in the HTTP user agent on Windows _(sfan5)_
* Added proper client initialization _(sapier)_
* Settings: Add no-exception variants of each get method _(kwolekr)_
* Huge overhaul of the entire MapgenParams system _(kwolekr)_
* ServerEnvironment: Remove direct dependency on EmergeManager _(kwolekr)_
* Replace pause, message, and death menus by formspec ones _(sapier)_
* Pass arguments by reference, reducing data copies _(Selat)_
* Cleaned up client init states by bumping protocol version _(sapier)_
* Added support for named threads on Linux, BSD, and Windows (MSVC-only) _(sapier, ShadowNinja)_
* Infered ipv6\_server from bind\_address; fixed client connect to IN(6)ADDR\_ANY _(kahrl)_
* Fixed all warnings reported by clang _(sfan5)_
* Removed locks that aren't absolutely required from JThread _(sapier)_
* Use narrow\_to\_wide in gettext instead of operating system dependent conversion function _(sapier)_
* Organized builtin into subdirectories _(ShadowNinja)_
* Switched to "core" namespace internally _(ShadowNinja)_
* Mapped Irrlicht log level to Minetest's and allowed writing Irrlicht logs to debug file _(RelaBadAngel)_
* Made print() NUL-safe _(ShadowNinja)_
* Added formspec toolkit and re-factored main-menu to use it _(sapier)_
* Reworked dumping functions _(ShadowNinja)_
* Improved performance by removing some temporary objects _(sapier)_
* Added an AppData file _(David Gumberg)_
* United node shaders and improved shader performance _(RealBadAngel)_
* Made players only stay loaded while they're connected _(ShadowNinja)_
* Added formspec API versioning _(sapier)_
* Added support for multipart/form-data to HTTPFetch _(ShadowNinja)_
* Improved error reporting of LevelDB backend _(sfan5)_

**Visual changes**

* Added waypoint HUD element _(RealBadAngel)_
* Added on-the-fly normal map generation _(RealBadAngel)_
* Made sun and moon textureable _(RealBadAngel)_
* Made formspec text-area word-wrap _(RealBadAngel)_
* Added support for DPI based HUD scaling _(sapier)_
* Made debug text adjust it's border to the screensize _(ShadowNinja)_
* Added download rate to non-HTTP media progress bar _(sapier)_
* Added support for interlaced-polarized, top-bottom, and side-by-side 3D screens _(sapier)_
* Made pause menu hide before "Shutting down..." message is drawn _(sapier)_
* Sorted commands and privileges alphabetically in '/help' _(kaeza)_
* Improved face shading with and without shaders _(RealBadAngel)_
* Added support for scalable font and GUI elements _(sapier)_
* Made GUITable mouse wheel scrolling faster _(kahrl)_

**Other changes**

* Added the option to bind to a specific address _(ShadowNinja)_
* Made flag strings clear specified flag with 'no' prefix _(kwolekr)_
* Added check to avoid usage of broken LuaJIT < 2.0.0-beta-8 _(sapier)_
* Lots of new and updated translations _(many contributors)_
* Improved performance of ABMs by only calcuating object counts once _(CiaranG)_
* Improved win32 file version information _(sapier)_
* Documented CMake options in README _(sfan5)_
* Corrected misleading detached inventory error message _(CiaranG)_
* Added more informative error messages for inventory and item method errors _(ShadowNinja)_
* Added redis database backend _(sfan5)_
* Moved the old stuff to doc _(BlockMen)_
* Removed dependency on marshal and many other async changes _(ShadowNinja)_
* Made item entity stacks merge on the ground and add TTL to item entities _(RealBadAngel)_
* Updated buildbot scripts and added 64-bit buildbot _(sfan5)_
* Added support for directly starting a world by name from command line _(sapier)_
* Many performance improvements and memory usage reductions _(sapier)_
* Added support for Android 2.3 and later _(sapier)_

### Bug fixes

* Fixed objects being selected behind a node _(Novatux)_
* Fixed absence of images when compiled with RUN\_IN\_PLACE=0 _(xyz)_
* Added option to link to OpenGL ES _(sfan5)_
* Fixed CMake list parsing in build _(hasufell)_
* Fixed cutting of multi-line error messages at half of second line in main menu dialog _(celeron55)_
* Created new instance of mesh every time it's required _(celeron55)_
* Escaped error messages in error dialog _(PilzAdam)_
* Added operating system to user agent _(proller)_
* Prevented auto-rotated nodes from replacing the nodes they were placed on _(ShadowNinja)_
* Added protection support to auto-rotated nodes _(ShadowNinja)_
* Prevented looking up node texts in a endless recursion loop _(sapier)_
* Set locale properly when built without gettext support _(celeron55)_
* Fixed Minetest's reliable UDP implementation _(sapier)_
* Compare values instead of pointers in Inventory::operator== _(kahrl)_
* Fixed some errors reported by clang static analyzer _(xyz)_
* Fixed win32 reading semaphore count not working (broke all queues) _(sapier)_
* Prevented player from jumping into nodes from below _(BlockMen)_
* Fixed cURL DLL not getting installed when sound was disabled _(sfan5)_
* Fixed error on mod download failure _(ShadowNinja)_
* Fixed use of previously deallocated EmergeManager _(kwolekr)_
* Fixed only half of unreliable queue being handled per step in worst case _(sapier)_
* Fixed player textures by adding '-' to list of allowed characters in media filenames _(sapier)_
* Fixed texture pack names corrupting mainmenu _(ShadowNinja)_
* Fixed crash when a error occurred in a globalstep callback _(ShadowNinja)_
* Fixed a heap-use-after-free in pause menu _(xyz)_
* Added checks for invalid user input for important settings _(kwolekr)_
* Fixed memory leak in database migration _(Selat)_
* Fixed invalid check for fread error on extracting zip _(sapier)_
* Fixed a unloaded but active block problem _(CiaranG)_
* Fixed rendering glitches when far from the center of the map _(Novatux)_
* Fixed race condition on exit to menu _(sapier)_
* Fixed generating winresource.o with build dir != source dir _(sfan5)_
* Fixed special characters in pause and message menu _(BlockMen)_
* Fixed game pause in singleplayer _(BlockMen)_
* Fixed "ghost stacks" created when a player clicks an item on the ground _(Novatux)_
* Fixed double sending of chat messages _(sapier)_
* Fixed bug in RemoteClient::GetNextBlocks _(celeron55)_
* Fixed crash when teleporting near unknown node _(BlockMen)_
* Fixed broken IPv4 serialization on win32 _(sapier)_
* Fixed invalid liquid lighting _(RealBadAngel)_
* Fixed wrong node texture rotation for facedirs 5 and 7 _(MetaDucky)_
* Fixed crash when trying to draw too many items from inventory in HUD _(celeron55, RealBadAngel)_
* Fixed a text border update bug _(ShadowNinja)_
* Added a hack to avoid a 2 second startup delay on local games _(sapier)_
* Fixed player:set\_animation() in third person view _(BlockMen)_
* Fixed numeric underflow on calculating window size adjustment _(sapier)_
* Fixed heart + bubble bar size on different texture packs _(sapier)_
* Added a limit to node meta data resolving recursion _(ShadowNinja)_
* Fixed typo (std::encl) in src/gettext.cpp _(JakubVanek)_
* Fixed wielded index being greater than inventory size _(RealBadAngel)_
* Fixed chat overlaying full screen _(sapier)_
* Fixed build on big endian architectures _(mat8913)_
* Made lack of IPv6 non-fatal to unit tests _(sapier)_
* Fixed the Map and Rollback databases not closing _(sapier)_
* Fixed day/night passing at the wrong speed on some architectures _(sapier)_
* Handle missing tablecolumns\[\] _(kahrl)_
* Fixed wrong status text rectangle _(sapier)_
* Fixed GenericCAO not grabing member objects, causing them to be deleted early _(sapier)_
* Fixed support for Max OSX _(mdoege)_
* Fixed regression in light calculation _(sapier)_

* Passed pointed\_thing to after\_place\_node _(ShadowNinja)_
* Documented "wielditem" visual _(ShadowNinja)_
* Passed pointed\_thing to on\_rightclick _(Novatux)_
* Added forceloading _(Novatux)_
* Added InvRef::get/set\_lists() _(ShadowNinja)_
* Mapgen V6: Added flag to stop mud flow _(kwolekr)_
* Allowed vertical axis particle rotation constraint _(khonkhortisan)_
* Used tables for adding particles, deprecated former way _(khonkhortisan)_
* Added formspec table _(kahrl)_
* Added minetest.override\_item _(ShadowNinja)_
* Added reading of slice probability table from schematic descriptors _(kwolekr)_
* LuaVoxelManip: Added get\_param2\_data and set\_param2\_data _(kwolekr)_
* Added pointed\_thing to minetest.register\_on\_placenode _(ShadowNinja)_
* Added pointed\_thing to minetest.register\_on\_punchnode and on\_punch callbacks _(ShadowNinja)_
* Added player:set\_sky() with simple skybox support _(celeron55)_
* Added player:override\_day\_night\_ratio() for arbitrarily controlling sunlight brightness _(celeron55)_
* Added minetest.kick\_player(name, reason) _(sapier)_
* Added capability to read table flag fields from Lua API _(kwolekr)_
* Added minetest.set\_noiseparam\_defaults() _(kwolekr)_
* Added force\_placement parameter to minetest.place\_structure _(kwolekr)_
* Removed "Server -!- " prefix from player messages _(ShadowNinja)_
* Updated set\_mapgen\_params and set\_gen\_notify to use new flag format _(kwolekr)_
* Added player:set\_local\_animations() _(BlockMen)_
* Added player:set\_eye\_offset() _(MirceaKitsune, BlockMen)_
* Added support for function serialization to minetest.serialize _(ShadowNinja)_
* Added proper Lua API deprecation handling _(sapier)_
* Made dump2() return the serialized string, like dump() _(ShadowNinja)_
* Added item eat callback _(rubenwardy)_
* Added success and output return values to chat commands _(ShadowNinja)_
* Allowed custom liquids to have drops _(sfan5)_
* Made dropdown formspec elements send their values the same way that buttons do _(sapier)_
* Reworked tooltips, adding a tooltip element _(RealBadAngel)_
* Reworked the glasslike\_framed drawtype _(RealBadAngel)_

### Vanilla game changes (minetest\_game)

* Added desert cobblestone, dropped by desert stone _(brunob.santos, sfan5)_
* Added desert stone brick and sandstone brick stairs/slabs _(Amaz1)_
* Added extended doors mod _(PenguinDad, BlockMen)_
* Added glass panes and iron bars _(BlockMen)_
* Added TNT _(BlockMen)_
* Reworked farming mod, added API _(webdesigner97)_
* Upwards digging for papyrus and cactus _(casimir)_
* Additional mirrored recipes for axes _(marvok)_
* Bookshelves have an inventory (for books) _(arsdragonfly)_
* Added furnace protection and progress visualization _(Krock)_
* Added /sethome and /home commands (with “home” privilege) _(sfan5)_
* Added Mese and diamond hoes _(BlockMen)_
* Enabled jungles by default on new worlds _(sfan5, BlockMen)_
* Increased crafting output for stairs (4 → 6) _(Jonathon Station)_
* Made punching bones pick up items _(Krock)_
* Made items drop if no space for bones _(Krock)_
* Don't create bones when inventory is empty _(arsdragonfly)_
* Added cuboid wieldhand _(paramat)_
* Many new textures, added inventory backgrounds _(BlockMen)_

### Master server (server list)

* Fixed null string escape in server list _(proller)_
* Made server announcing use multipart/form-data _(ShadowNinja)_
* Fixed boolean typing and alignment _(ShadowNinja)_
* Fixed code style, const-correctness, and types _(ShadowNinja)_
* Moved the master server to separate repository _(ShadowNinja)_
* Fixed seconds validity check _(ShadowNinja)_
* Made README more complete _(ShadowNinja, sfan5)_
* Made the hovered entry highlight in very light gray _(sfan5)_
* Switched to 'display' instead of 'visibility' to prevent the page from having white space at the bottom _(sfan5)_

0.4.8 → 0.4.9
-------------

0.4.9 was released on January 1, 2014.

### New features

**Logistic changes**

* Added SQLite rollback _(Mario Barrera & ShadowNinja)_
* Implemented HTTPFetch _(kahrl)_
* Replaced SimpleThread with JThread _(sapier)_
* Added handling for LuaErrors in Lua -> C++ calls on LuaJIT _(ShadowNinja)_
* Made SHA1::addBytes(..., 0) a no-op instead of an assertion failure _(kahrl)_

**Visual changes**

* Reworked shaders _(RealBadAngel)_
* Added configurable font shadow _(xyz)_
* Added Directional fog + horizon colors _(Taoki)_
* Removed FPS from window title (Doubles performance on some window managers) _(PilzAdam)_

**Other changes**

* Implemented modstore search tab and version picker _(sapier)_
* Added check for denied access in itemdef/nodedef/media fetch loop _(kahrl)_

### Bug fixes

* Fixed line\_of\_sight() _(sapier)_
* Fixed modstore/favourites hang by adding asynchronous Lua _(sapier)_
* Fixed LevelDB maps _(sfan5)_
* Fixed Lua mapgen override param handling _(kwolekr)_
* Fixed leak and possible segfault in minetest.set\_mapgen\_params _(kwolekr)_
* Fixed segfault in indev cave generation due to uninitialized variable _(kwolekr)_
* Added check for if width, height or start index of a list\[\] is negative _(PilzAdam)_
* Fixed single character formspec field labels _(BlockMen)_
* Added handling for Lua errors in on\_generate callbacks _(kwolekr)_
* Update mapgen params in ServerMap after Mapgen init _(kwolekr)_
* Fixed wrong names for parallax settings in config example. _(RealBadAngel)_
* Fixed particle code ignoring return value of std::vector::erase(). _(kahrl)_
* Fixed minetest.facedir\_to\_dir when param2 is 5 or 7. (Again) _(Novatux)_
* Fixed InventoryList reading order _(ShadowNinja)_
* Initialize world before creating BanManager and RollbackManager _(ShadowNinja)_
* Fixed exception caused by destroying sockets on Server shutdown _(kwolekr)_

* Added area parameters back to calc\_lighting() and set\_lighting() _(kwolekr)_
* Added get\_light\_data() and set\_light\_data() to LuaVoxelManip _(kwolekr)_
* Added minetest.swap\_node _(Novatux)_
* Assumed a selection box for fences _(0gb.us)_
* Decoration: Added schematic Y-slice probability support _(kwolekr)_
* Added sneak and sneak\_glitch in set\_physics\_override() _(PilzAdam)_
* Used a table in set\_physics\_override() _(PilzAdam)_
* Added 'on\_prejoinplayer' callback _(kaeza)_
* Made line\_of\_sight return blocking node position _(stujones11)_
* Removed support for optdepends.txt _(ShadowNinja)_
* Added map feature generation notify Lua API _(kwolekr)_
* Added 'minetest.write\_json' _(ShadowNinja)_
* Log guilty node name when allow\_metadata\_inventory\_move/put/take fails _(kahrl)_
* Fixed enum element name in Lua HUD code (position vs. pos) _(kaeza)_

0.4.7 → 0.4.8
-------------

0.4.8 was released on November 24, 2013.

### New features

**Big gameplay changes**

* Added drowning _(PilzAdam, RealBadAngel, BlockMen)_
* Added weather support _(proller)_

**Smaller gameplay tweaks**

* Added new sounds _(someone who can't decide if he wants to be called mitori or mito551)_
* Don't predict placing and removing nodes if interact privilege is missing _(PilzAdam)_

**Logistic changes**

* Clean up rendering code a bit (increases FPS by 5 to 10) _(Exio)_
* Added support for IPv6 _(matttpt)_
* Don't write player files all the time if they are not modified _(PilzAdam)_
* Made the main menu Lua based _(sapier, kahrl)_
* Change static ContentFeatures array into a vector _(rathgit, kahrl)_
* Allow multiple singleplayer games at the same time _(PilzAdam)_
* Added texture pack selection to main menu _(Novatux)_
* Don't write files directly but rather write to a temporary file that gets renamed after succesfully written; fixes many causes of corrupted files _(PilzAdam)_
* Adjust the Lua API structure and improve header inclusion to decrease compile time _(kahrl)_
* Database abstraction, LevelDB support _(sfan5, wieszak, xyz)_
* Use the Settings Lua interface to read world.mt _(PilzAdam)_
* Use engine.is\_yes() in mainmenu _(PilzAdam)_
* Always use builtin JThread library _(kwolekr)_
* Optimized minetest.get\_connected\_players() _(fairiestoy)_
* Removed mapgen\_air alias (#935) _(0gb.us)_
* Raise the maximum node limit to 0x7fff _(ShadowNinja)_
* Shortened lines in falling node code _(ShadowNinja)_
* Moved the sapling growing and grass adding/removing ABMs to Lua _(Novatux)_
* Portability fixes for OpenBSD (and possibly NetBSD and others) _(Warr1024)_
* Accept hexadecimal and string values for seeds _(kwolekr)_
* Pass a errfunc to `lua_pcall` to get a traceback _(ShadowNinja)_
* Replaced print()s with minetest.log() in builtin _(PilzAdam)_
* Updated parameter index of set\_lighting() _(kwolekr)_

**Visual changes**

* Added support for bumpmapping _(RealBadAngel)_
* Added diagonal liquid animation _(kahrl)_
* Damage updates and effects are now sent to other players _(PilzAdam)_
* Made fog depend on humidity _(proller)_
* Added git hash to version string in top left corner of window _(kahrl)_
* Added --version option _(kahrl)_
* Fixed liquid\_range, fixing graphical glitches on old servers _PilzAdam)_
* Added seed entry to world creation dialog _(kwolekr)_

**Other changes**

* Play `player_damage.ogg` when recieving damage and `player_falling_damage.ogg` on falling damage _(PilzAdam)_
* Added basic unicode support to the console in Linux _(Exio)_
* Added a setting for max loop count per step in liquid update _(PilzAdam)_
* Added math mapgen with fractal based worlds _(proller)_
* Disallow the name 'singleplayer' in a multiplayer server _(PilzAdam)_
* Added `max_objects_per_block` to minetest.conf to control the maximum number of static objects per block _(Novatux)_
* Removed broken farmesh _(kahrl)_
* Added `language` setting to `minetest.conf` which forces Minetest to use specified translation _(xyz)_
* Added configurable PRAGMA synchronous = _(proller)_
* Added curl, freetype and luaJIT to CMAKE\_BUILD\_INFO _(PilzAdam)_
* Lowered the default max\_users from 100 to 15 _(ShadowNinja)_
* Removed doc/gpl-2.0.txt, add doc/lgpl-2.1.txt _(kahrl)_
* Masterserver update _(proller)_
* Moved new core devs to the "Core Developpers" section of mainmenu _(Novatux)_
* Added ShadowNinja's email address to the main menu credits _(ShadowNinja)_
* Used a doT.js template for the serverlist _(ShadowNinja)_
* Added default\_privs to masterserver and JS autoload _(proller)_
* Added BlockMen to core dev list _(PilzAdam)_
* Added missing RequestQueue doc _(sapier)_
* Prevent enabling Shaders if Direct3D is used _(PilzAdam)_
* Fix my name (doesn't display correctly because of utf8 characters) _(Novatux)_

### Bug fixes

* Fixed `print(nil)` crashing the server _(kahrl)_
* Fixed output of profiler (F6) when using freetype _(kahrl)_
* Fixed bug where wrong item is selected when dropping something in the inventory on another stack _(kahrl)_
* Fixed lighting bug caused by disappearing lava _(PilzAdam)_
* Fixed /unban command crashing the server _(kahrl)_
* Fixed lighting bug with 6d facedir _(RealBadAngel)_
* Fixed and improved view range tuner _(celeron55)_
* Fixed and improved anticheat _(celeron55)_
* Fixed server getting completely choked up on even a little of DoS _(celeron55)_
* Fixed crack overlay for animated textures _(kahrl)_
* Added fallback font for Chinese, Japanese and Korean languages, the translations in those languages can now be displayed _(xyz)_
* Fixed most object duplication bugs _(celeron55)_
* Fixed hotbar padding at bottom _(BlockMen)_
* Fixed comments about length of server step _(ShadowNinja)_
* Fixed some warnings and other minor details _(kwolekr)_
* Re-fixed hud\_change stat argument retrieval _(kwolekr & ShadowNinja)_
* Fixed wrong error message on invalid use of the formspec element image\_button _(RealBadAngel)_
* Fixed object duplication bug _(celeron55)_
* Made unknown nodes stop falling nodes properly _(ShadowNinja)_
* Fixed ignoring of "diggable" property of nodes _(0gb.us)_
* Fixed invalid use of pointer to temporary object in JSON to Lua conversion _(sapier)_
* Fixed win32/msvc i18n _(sapier)_
* Fixed weather _(kwolekr)_
* Prevented shaders from being created when disabled _(kwolekr)_
* Fixed formspec background padding when clipped _(BlockMen)_
* Fixed array limit check when reading Lua specialtiles table _(MetaDucky)_
* Fixed invalid listname and listsize not handled correctly in set\_size _(sapier)_
* Handle blank blocks in database _(kwolekr)_
* Fixed multicaller support in RequestQueue _(sapier)_
* Fixed result of processed request being written to invalid (non-existent) ResultQueue if requesting thread timed out _(sapier)_
* Fixed gettext compile issues under win32 _(MetaDucky)_
* Made mapgen V6 respect water\_level setting _(kwolekr)_
* Fixed usage of 'minetest' where 'engine' was intended _(ShadowNinja)_
* Fixed crash when pressing Enter key in formspec menu _(kahrl)_
* Fixed rename modpack button not working, fixes #1019 _(PilzAdam)_
* Don't continue trying to deserialize blank block data _(kwolekr)_

* Added ingame modstore to download mods from mmdb _(sapier)_
* Added `minetest.register_decoration()` _(kwolekr)_
* Added schematic support; new functions `minetest.place_schematic()` and `minetest.create_schematic()` _(kwolekr)_
* Seperated formspecs of furnace and chests to provide override by mods _(BlockMen)_
* Added Lua VoxelManip _(kwolekr)_ [http://forum.luanti.org/viewtopic.php?id=6396](http://forum.luanti.org/viewtopic.php?id=6396)
* Added vector helpers _(ShadowNinja)_
* Added `range` to item definition _(PilzAdam)_
* Added `after_use` to item definition _(Novatux)_
* Added `liquid_range` to node definition _(PilzAdam)_
* Added `collide_with_objects` to entitiy definition, to disable object <-> object collision _(PilzAdam)_
* Added `minetest.facedir_to_dir()` and 6d facedir support for `minetest.dir_to_facedir()` _(hdastwb)_
* Added gettext for `image_button` _(BlockMen)_
* Added `stepheight` to entity definition _(sapier)_
* Added support for multiple `wherein` nodes in `minetest.register_ore()` _(PilzAdam)_
* Added `minetest.register_on_cheat()` _(celeron55)_
* Added `automatic_face_movement_dir` to entity definition _(sapier)_
* Added `player:hud_set_hotbar_image()` and `player:hud_set_hotbar_selected_image()` _(PilzAdam, BlockMen)_
* Added percent scaling for HUD images _(BlockMen, kahrl)_
* Added `minetest.get_gametime()` _(Novatux)_
* Allowed manually specifying param2 in minetest.item\_place() and return success _(PilzAdam)_
* Added set\_name(), set\_count(), set\_wear() and set\_metadata() to Lua ItemStack _(PilzAdam)_
* Added support for parameter 'visual\_scale' for drawtypes 'signlike' and 'torchlike' _(Sokomine)_
* Fixed minetest.facedir\_to\_dir when param2 is 5 or 7. _(Novatux)_
* Added 'after\_use' tool callback _(Novatux)_
* Added settings interface for Lua _(PilzAdam)_
* Moved tree growing and grass growing ABMs to Lua _(Novatux)_
* Added `minetest.register_on_craft()` and `minetest.register_craft_predict()` _(Novatux)_
* Added basic protection support to builtin _(ShadowNinja)_
* Added 6d facedir rotation prediction routine _(VanessaE)_
* Added wrapper for minetest.rotate\_and\_place _(Evergreen)_

**Formspec changes**

* `pwdfield`, `vertlabel`, `tabheader`, `dropdown` and `checkbox` _(sapier)_
* `<noclip>;<drawborder>;<pressed texture name>` options for image\_button _(sapier, BlockMen)_
* `textlist` and `box` with color support _(sapier, sfan5)_
* `listcolors` and `bgcolor` _(BlockMen, kahrl)_
* `<auto_clip>` option for background images _(BlockMen)_
* Added option to scale image to percentage values _(BlockMen)_
* Send a on\_receive\_fields event when formspec is closed, with fields.quit = "true" _(Novatux)_
* Reworked formspecs _(BlockMen)_

0.4.6 → 0.4.7
-------------

0.4.7 was released on June 6, 2013.

### New features

**Big gameplay changes**

* Added snow, snow block, ice and dirt with snow _(PilzAdam)_
* Added sandstone bricks and desert stone bricks _(PilzAdam & VanessaE)_
* Added coal block, crafted out of 9 coal lumps _(Zeg9)_
* Added flowers to craft dyes; flowers and grass grow now on dirt\_with\_grass _(0gb.us, PilzAdam, VanessaE, ironzorg)_
* Added farming mod; wheat can be used to bake bread and cotton can be used to craft wool _(PilzAdam)_ [http://forum.luanti.org/viewtopic.php?id=6067](http://forum.luanti.org/viewtopic.php?id=6067)

**Smaller gameplay tweaks**

* Added a little delay for falling nodes to update so that the objects don't spawn all at once _(PilzAdam)_
* Added private messaging with `/msg` _(ShadowNinja)_
* Added copper block _(RealBadAngel)_
* Swing the camera down when the player lands on the ground; disabled by default; `fall_bobbing_amount` in minetest.conf _(Taoki)_
* Node placement prediction now accounts for "wallmounted", "facedir" and "attached\_node" nodes and only replaces "buildable\_to" nodes _(kahrl, ShadowNinja & PilzAdam)_
* Added `disable_fire` setting to disable fire burning _(ShadowNinja)_
* Added damage to the hand in creative mode _(PilzAdam)_
* Added a little animation when changing the wielded item _(PilzAdam & blue42u)_
* Apples now fall when the tree decays _(PilzAdam & BlockMen)_

**Logistic changes**

* Added mapgen v7; not usable currently _(kwolekr)_
* Added support for LuaJIT, makes mod execution much faster _(RealBadAngel)_
* Move cave generation to cavegen.cpp and restructure it into a class _(kwolekr)_
* Added icons to select games in menu; `menu/menu_<background/overlay/header/footer>.png` of selected game is used in the main menu (TP can use `<gameid>_menu_<background/overlay/header/footer>.png`) _(celeron55)_
* Added `--videomodes` option to show available video modes _(kahrl)_
* Added ability to play `main_menu.ogg` (`main_menu.<1-9>.ogg` are supported too; they are choosen randomly if present) in main menu _(RealBadAngel)_
* Drop common mods system, _Survival_ and _Build_ game; minetest\_game includes all common mods and the bones mod from _Survival_ now _(PilzAdam)_ [http://forum.luanti.org/viewtopic.php?id=6034](http://forum.luanti.org/viewtopic.php?id=6034)
* Changed mod system a bit: All user mods are installed in `$path_user/mods/` now; they can be enabled per world in the configure world window or in `world.mt` with `load_mod_<modname>` _(PilzAdam)_ [http://forum.luanti.org/viewtopic.php?id=6066](http://forum.luanti.org/viewtopic.php?id=6066)
* Split `init.lua` of the default mod into several files _(PilzAdam)_
* Moved scriptapi to a subfolder _(sapier, celeron55 & kahrl)_

**Visual changes**

* Changed "unknown block" texture to "unknown node" _(khonkhortisan)_
* Changed textures of sand, desert sand and desert stone _(VanessaE)_
* `crosshair.png` is used instead of the normal crosshair if present _(dannydark & Exio4)_
* Added progress bar and clouds to loading screen _(Zeg9)_
* Added new textures for all metal and diamond blocks _(Zeg9)_
* Added new Minetest header _(BlockMen)_

**Other changes**

* Added `mouse_sensitivity` option _(Exio4)_

### Bug fixes

* Check if the address field is empty when hitting enter on the multiplayer tab _(ShadowNinja)_
* Limit speed in collisionMoveResult for avoiding hangs _(Exio4)_
* Fixed camera "jumping" when attached and the parent goes too fast _(Zeg9)_
* Fixed nick completion in chat console with the tab key _(PilzAdam)_
* Do not always move fast in water and ladders when aux1\_descend it true _(Taoki)_
* Fixed **a lot** memory leaks _(sapier, PilzAdam, kahrl, kwolekr)_
* Fixed import of older maps _(kwolekr)_
* Fixed black trees _(kwolekr)_
* Fixed small objects colliding with themselves _(sapier)_
* Fixed `get_craft_recipe()` and `get_all_craft_recipes()` _(RealBadAngel)_
* Fixed spawning too high above ground _(kwolekr)_
* Fixed object -> player collision _(sapier)_
* Fixed favorite server list in globally installed versions of Minetest (RUN\_IN\_PLACE=0) _(Zeg9)_
* Fixed favorite server list on windows _(sfan5)_
* Fixed handling of mods in games in the configure world GUI _(kahrl)_
* Fixed static data of objects not beeing stored correctly on deactivation _(sapier)_
* Removed _Meshbuffer ran out of indices_ limitation _(kahrl)_
* Fixed `isBlockInSight()` for higher FOV _(Warr1024)_
* Don't teleport back when a player is detached or turns free move off and holds shift _(PilzAdam)_
* Fixed bug where you need to move the mouse after closing a menu _(kahrl)_
* Reduced `/clearobjects` memory consumption; `max_clearobjects_extra_loaded_blocks` in minetest.conf _(kahrl)_
* Corrected segfault when registering new biomes _(sweetbomber)_
* Reduced video memory consumption by not generating unnecessary `[forcesingle` textures _(kahrl)_
* Close console when it loses focus but it is still on screen _(Exio4)_

* Added `player:set_physics_override()` to set per-player physics _(Taoki & PilzAdam)_
* Use `node_box` for `selection_box` if `drawtype = "nodebox"` and `selection_box = nil` _(kaeza)_
* Added `minetest.env:line_of_sight()` and `minetest.env:find_path()` _(sapier)_
* Added API functions to add elements to the HUD of players _(blue42u, kwolekr & kaeza)_
* Added option to not prepend "Server -!- " to messages sent with `minetest.chat_send_player()` _(ShadowNinja)_
* Added `minetest.get_player_ip()` _(ShadowNinja)_
* Added `use_texture_alpha` in node definition to use alpha channel of node texture _(kwolekr)_
* Added `glasslike_framed` node drawtype _(RealBadAngel)_
* Added optional dependencies and different [mod name conflict handling](/index.php?title=Mod_name_conflicts&action=edit&redlink=1 "Mod name conflicts (page does not exist)") _(kahrl)_
* Use group `soil` for nodes where saplings can grow on _(ShadowNinja)_
* Nodes with drawtype `raillike` connect to all other nodes with the same drawtype if they are in the `connect_to_raillike` group _(Jeija)_
* Env functions are now in the global minetest table; that means they are called via `minetest.<function>` instead of `minetest.env:<function>` _(sapier, celeron55 & kahrl)_
* Added `obj:set_hotbar_itemcount()` _(kahrl)_

0.4.5 → 0.4.6
-------------

0.4.6 was released on April 3, 2013.

### New features

**Big gameplay changes**

* Added lavacooling near water; lava source turns into obsidian, flowing lava turns into stone _(PilzAdam)_
* Added junglewood (with stairs and slabs), jungleleaves and junglesaplings _(PilzAdam)_
* Added obsidian, obsidian shards and obsidian glass _(PilzAdam & jojoa1997)_
* Added grass (5 different heights) _(PilzAdam)_
* Added growing for papyrus (on dirt and grass near water) and cactus (on sand) _(PilzAdam)_
* Added stonebricks crafted from 4 stones _(PilzAdam)_
* Added gold _(PilzAdam)_
* Added diamonds and diamond tools, wich are slightly faster and wear out slower than mese tools _(PilzAdam)_
* Added mese axe, shovel and sword; mese pick is not the ultimate tool anymore _(PilzAdam)_
* Added copper, bronze and bronze tools; bronze can be crafted with copper ingot and steel ingot; bronze tools have same digging times but more uses than steel tools _(PilzAdam)_

**Smaller gameplay tweaks**

* 3 nodes now give 6 slabs instead of 3 _(PilzAdam)_
* Wooden stairs and slabs are now flammable _(PilzAdam)_
* Lava is not renewable anymore _(PilzAdam)_
* It is not possible anymore to place non-fuel items in the fuel slot or any item in the output slots of the furnace _(PilzAdam)_
* Falling nodes now destroy solid buildable\_to nodes _(Splizard)_
* Added ability for buckets to pick up flowing water when liquid\_finite is enabled _(ShadowNinja)_
* Use right click to place liquids with buckets; added description for buckets _(PilzAdam & ShadowNinja)_
* Fixed furnace infotext saying "Furnace out of fuel" when placing a fuel but no item to cook into it _(PilzAdam)_
* Made Mese ores a bit more rare; made Mese blocks very rare _(PilzAdam)_
* Added object <-> object collision _(sapier)_

**Map generation changes**

* Readded dungeons (disabled by default, enable with "dungeons" flag in "mg\_flags" setting) _(kwolekr)_
* Speed up lighting a lot _(kwolekr)_
* Readded jungles (disabled by default, enable with "jungles" flag in "mg\_flags" setting) _(kwolekr)_
* Generate apple trees _(kwolekr)_
* Moved ore generation back to core; improved ore generation speed _(kwolekr)_
* Added `singlenode` mapgen _(celeron55)_
* Added a new map generator called `indev` (float islands at 500+, rare HUGE caves, near edges: higher mountains, larger biomes) _(proller)_

**Visual changes**

* Changed textures of cobblestone and mossy cobblestone _(PilzAdam)_

**Logistic changes**

* Split scriptapi.cpp into more files _(sapier)_
* Migrate to STL containers/algorithms _(xyz)_
* Added the pseudo game _common_ with _bucket_, _default_, _stairs_, _doors_ and _fire_ mods included; deleted those mods from minetest\_game _(celeron55 & PilzAdam)_
* Added a checkbox for finite liquids to settings menu _(proller)_

**Other changes**

* Use moving clouds as background for the main menu _(Krisi & ShadowNinja)_
* minetest.env:find\_nodes\_near() optimized to be 11.65x faster, ServerEnvironment step CPU consumption cut in half _(kwolekr)_

### Bug fixes

* Fixed build with ogles2 driver _(proller)_
* Fixed new\_style\_water (shaders are not used for this anymore) _(PilzAdam)_
* Fixed backface\_culling in tiledef; both sides of flowing liquids are now visible _(doserj)_
* Hopefully fix node replacement bug (where the node that is pointed at is replaced) _(0gb.us)_

* Added `minetest.get_all_craft_recipes(output)` _(RealBadAngel)_
* Allow any character in formspec strings with escape characters _(kwolekr)_
* Added ability to pass multiple parameters to `minetest.after()` _(Jeija)_
* Added `player:set_look_yaw()` and `player:set_look_pitch()` _(RealBadAngel)_
* Added ability to load mods from the pseudo game _common_ via `common_mods` in game.conf _(celeron55)_
* Added support for a minetest.conf file in games, wich override the default values _(celeron55)_
* Added 6d facedir to rotate nodes with _facedir_ drawtype _(RealBadAngel)_
* Added function and wrapper to predict and assign 6d rotation via `minetest.rotate_and_place()` _(VanessaE and EvergreenTree)_
* Added `minetest.add_particle()`, `minetest.add_particlespawner()` and `minetest.delete_particlespawner()` _(Jeija)_
* Added `minetest.register_ore()` to let the engine generate the ores; `default.generate_ore()` is now deprecated _(kwolekr)_
* New damage system added as described here: [Damage\_system](/index.php?title=Damage_system&action=edit&redlink=1 "Damage system (page does not exist)") _(PilzAdam & celeron55)_
* Added `place` field to sound table of tools _(PilzAdam)_

0.4.4 → 0.4.5
-------------

0.4.5 was released on March 4, 2013.

### New features

**Big gameplay changes**

* Added Mese crystals and Mese crystal fragments (crafted from 1 Mese crystal); Mese blocks can be crafted with 9 Mese crystals; Mese pickaxes are now crafted using Mese crystals; old Mese equals the new Mese block and is still generated at altitudes -1024 and below _(VanessaE & PilzAdam)_
* Doors must now be right clicked to be opened _(PilzAdam)_
* Flying through walls now requires the "noclip" privilege and noclip mode must be enabled by pressing H _(PilzAdam)_
* Added a list of servers to the "Multiplayer" tab of the main menu _(Jeija)_
* Added a mod selection menu _(doserj)_
* Jungle grass now spawns naturally again _(PilzAdam)_
* Added finite liquid support, experimental and disabled by default _(proller)_

**Smaller gameplay tweaks**

* Locked chest contents are now only shown to their owner _(PilzAdam)_
* Added ability to write several lines on a sign _(PilzAdam)_
* When sneaking, the current node/item will always be used when right clicking even if pointing a chest or a furnace _(Jeija)_
* In creative mode, hand now breaks everything nearly instantly and nodes/items are infinite _(PilzAdam)_
* Player physics are now tweakable by server admin _(Taoki)_
* Fast mode can now be used in liquids and in climbable nodes _(kwolekr)_
* Fire is now "buildable to" _(Casimir)_
* To fly at "fast" speed, the "use" key must now be held if using shift to descend _(PilzAdam)_
* Added upside down stairs and slabs _(PilzAdam)_
* Added ability to switch to fly\_mode when double-tapping space bar, disabled by default; can be enabled in the key change menu _(PilzAdam)_
* Tweaked damage and punch times of weapons, tools and hand _(Calinou)_
* Added repeated right clicking when holding the right mouse button, see "repeat\_rightclick\_time" setting in minetest.conf _(Jeija)_

**Map generation changes**

* Added L-system tree generation _(RealBadAngel & dannydark)_
* Map generation is now slightly faster and can be tweaked in minetest.conf _(kwolekr)_
* Added optional flat map generation, with and without trees _(kwolekr)_

**Visual changes**

* Mese pickaxe now has a new texture, which is more yellow _(Jordach)_
* Tweaked dirt texture so that it tiles better; improved lump and ingot textures; added fake shading to the default player texture _(Iqualfragile & GloopMaster & Jordach)_
* Added particles when digging blocks _(Jeija & PilzAdam)_
* The selection box of stairs now fits the stairs _(PilzAdam)_
* If damage is disabled, damage screen is disabled and health is not shown on the HUD _(PilzAdam)_
* Damage screen is now red fade instead of constant red; camera now tilts when receiving damage _(Jeija & PilzAdam)_
* Added "selectionbox\_color", "crosshair\_color" and "crosshair\_alpha" minetest.conf settings for changing selection outline color, crosshair color and crosshair opacity respectively _(Exio4)_

**Logistic changes**

* Minetest-c55 is now named Minetest
* Less stuff is now put in debug.txt by default, change with debug\_log\_level, default is 2
* Texture atlas is now disabled by default _(kwolekr)_
* Added and updated language translations; French, German, Portuguese, Polish and Spanish translations are 100% complete _(Calinou, kaeza, PilzAdam, sfan5, xyz, kotolegokot, pandaro, Mito551, Shen Zheyu, sub reptice, elagin, KikaRz and socramazibi)_
* Added support for downloading media from a server using cURL which is faster, disabled by default _(Ilya Zhuravlev)_

### Bug fixes

* Walking on stairs, slabs and glass now makes sounds _(PilzAdam & dannydark)_
* Fixed and cleaned EmergeThread around a bit _(kwolekr)_
* Punching entities and players with shovels and pickaxes now deals damage _(Calinou)_
* Fixed some caves having too many dead ends _(unknown)_
* Fixed the looks of some plantlike nodes by using two long planes instead of four shorter planes _(doserj)_
* Grass no longer turns into dirt below unloaded blocks _(PilzAdam)_
* Fixed a crash when clicking "Configure" when no world is selected in Singleplayer menu _(doserj)_
* Fixed dropped item collision with nodeboxes _(jordan4ibanez)_
* Fixed a glitch where the player gets liquids in his inventory when a server lags _(PilzAdam)_

* Added ability to change the itemstack in placenode callbacks _(PilzAdam)_
* Added ability to create multi-line textfields in formspecs _(Jeija)_
* Add on\_rightclick(pos, node, clicker) callback for nodes _(PilzAdam)_
* Added minetest.show\_fromspec(playername, formspec) to show formspecs via Lua _(sapier)_

0.4.3 → 0.4.4
-------------

0.4.4 was released on December 6, 2012. 0.4.4-d1 (an interim release made due to a protocol change) was released on January 2, 2013.

### New features

* Added animated 3D player and a new default skin, the default model also supports Minecraft skins _(Taoki, skin by Jordach)_
* Added shaders support (can be disabled in Settings menu), makes water a bit smaller than a full block, makes lighting look prettier _(kahrl and celeron55)_
* New default doors mod: doors have a 3D look, ability to create "double doors" added, added locked steel doors (only the owner of the door can open/close it) _(PilzAdam)_
* Improve map generation speed a lot _(hmmmm)_
* Day-night transitions are now smoother _(celeron55)_
* Water textures are now animated _(RealBadAngel (textures) and PilzAdam)_
* Added on-demand item previews (reduces load time/RAM usage), disabled by default _(celeron55)_
* Added 3D anaglyph support (red-cyan glasses) _(xyz)_
* Fire is now animated and causes damage to players _(PilzAdam, Muadtralk (textures))_
* Tweaked some textures: apple, nyan cat, bricks, papyrus, steel sword _(Calinou, VanessaE)_
* Tweaked digging animation (no more mining with the tip of your pickaxe!) _(jordan4ibanez)_
* Changed apple, sapling and papyrus selection box size to be smaller _(VanessaE)_
* Players who do not move no longer send their positions to save bandwidth _(Taoki)_
* Make steel block and brick drop themselves when dug and make them craftable back into their materials _(PilzAdam)_
* Glass now makes a sound when broken _(PilzAdam)_
* Dead players are now visible _(Taoki)_
* Changed default server tick to 0.1 second, decreasing server CPU usage _(celeron55)_
* Clients now send their position every 0.1 second too, making other player movement look smoother _(celeron55)_
* Use of /grant and /revoke commands is now logged _(dannydark)_
* Added ability for server to tweak amount of bandwidth used to upload mods to clients _(celeron55)_

### Bug fixes

* Fixed falling sand and gravel sometimes incorrectly landing _(PilzAdam)_
* Fixed empty bucket being named "emtpy bucket" (khonkhortisan and PilzAdam)
* Fixed slab to full block transformation _(PilzAdam)_
* Fixed smooth lighting between MapBlocks _(celeron55)_
* Prevent some blocks (leaves, falling sand and gravel) from giving air when dug when they disappear as you mine them _(PilzAdam)_
* Fixed papyruses and cacti growing inside trees _(PilzAdam)_
* Fixed flowing liquid animation direction calculation _(celeron55)_
* Fixed wielditem entity drawtype brightness control _(celeron55)_
* Fixed ObjectRef:punch() _(celeron55)_
* Fixed a rare bug in leaf decay _(PilzAdam)_
* Fixed trees growing into any type of node _(xyz)_
* Fixed server crashing when "/clearpassword" is typed without an argument _(Uberi)_
* Head no longer shifts downwards when you are inside transparent blocks such as glass or nodeboxes _(Calinou)_
* Directories beginning with a "." are now ignored when searching for mods on Windows _(matttpt)_
* Fixed the automagic render distance tuner _(celeron55)_

* Added 3D model support for entities _(Taoki)_
* Added attachment support (so that entities can "ride" other entities) _(Taoki)_
* Backgrounds and images can now be used in formspecs _(RealBadAngel)_
* Liquids can now be made non-renewable _(xyz)_
* Added nodedef.on\_blast() to lua\_api.txt in order to support chained explosions of any explosives _(celeron55)_
* Allow transparent image buttons _(khonkhortisan)_
* Added shutdown hook interface to Lua API _(matttpt)_
* Added "attached\_node" group to make nodes which are not attached to any other walkable node drop _(PilzAdam)_