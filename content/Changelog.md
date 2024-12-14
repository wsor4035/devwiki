# Changelog
Note that not all changes made to the code between releases are listed here. Fixes to bugs that were introduced after the previous release, small internal changes, code style fixes, and changes of the like are not listed. If you want a list of _every_ change made between releases see the [commit log](https://github.com/minetest/minetest/commits/master).

5.9.1 → 5.10.0
--------------

Released on 10 November 2024.

### Deprecations and compatibility notes

* **Minetest is now called Luanti.**
    * The game executable name has changed, thus custom links and scripts might need maintenance.
    * Any `minetest.conf` files remain compatible (naming yet not changed).
    * For Unix: `$HOME/.minetest/` remains used for system-wide installations (naming yet not changed).
    * Mods may use the `core` table instead of the equivalent `minetest`. (see lua\_api.md)
* OpenGL ES 1.0 (ancient) is no longer supported. OpenGL ES 2.0 will be used instead.
* (basic) shaders will eventually become a requirement. A warning is shown if they are disabled.

### Client / Audiovisuals

* Added a workaround to fix shader errors on buggy Intel iGPU drivers on Windows 8.1 and older (_sfan5_)
* Fixed Post Processing with the `ogles2` driver (_grorp_)
* The main menu server filter / search box now filters more intuitively (_appgurueu_)
* Touch controls are now enabled/disabled based on the used input device (_grorp_)
* Main menu: redesigned ContentDB tab (_rubenwardy_)
* Improved texture pack compatibility when using the `[mask` modifier (_SmallJoker_)
* More fancy shaders (_GefullteTaubenbrust2_)
    * Server-controlled bloom shader API (_grorp_)
    * Follow-up fixes (various contributors)
* Fixed sound mute on macOS (_sfence_)
* Improved formspec scaling (_grorp_)
* The minimap is again scaled proportional to the screen size (_grorp_)
* Improved distinction of touch-related settings (_grorp_)
    * UI scaling settings and touch input are no longer tightly tied together (_okias_)
* Transparency sorting now works more reliably (_Desour_)
    * Can be disabled entirely with `transparency_sorting_distance = 0`
* Setting for debugging purposes: `show_block_bounds_radius_near` (_Desour_)
* Windows touch controls are no longer enabled because they exist
* Setting `smooth_scrolling` to disable smooth scrolling (_grorp_)
* Touchscreens/Android: Button bar replaced with a grid menu for easier access (_grorp_)
* (IME candidate list in Windows (_y5nw_)) - inactive: requires a USE\_SDL=1 build.

### World / Server / Environment

* More fine-grained control over anticheat by settings (_zmv7_)
* "Access denied" strings may now be translated (_Emojigit_)
* Setting `server_announce_send_players` to hide the player names from the public server list (_Emojigit_)

### Script API / Modding

* Gettext and plural support for client-side translations (_Ekdohibs_. _y5nw_)
* Option to calculate the scroll container size automatically (_SmallJoker_)
* Player controls API now supports joystick inputs (x/y) (_grorp_)
* 6 textures support for `drawtype = "allfaces*"` nodes (_DragonWrangler1_)
* ABM without\_neighbors field (_sfence_)
* Death formspec can now be customized (_grorp_)
* Bulk LBM support (_sfan5_)
* Players can now be requested to rejoin on kick (by mods) (_Emojigit_)
* Static glTF models and animated models are now supported (_JosiahWI_, _appgurueu')_
* The hotbar is now mod-customizable (_cx384_)
* `core.get_server_status` and `core.privs_to_string` are now sorted (_zmv7_)
* Overridable HP and breath logic, see `ObjectRef:get_flags` (_sfence_)
* Fix animations not being restartable (requires up-to-date client and server) (_appgurueu_)
* `core.close_formspec` (and equivalent) no longer throw incorrect deprecation warnings (_appgurueu_)
* Object observers API (_appgurueu_)
    * This allows mods to selectively show entities to certain players.
* New functions:
    * `core.ipc_(cas|poll)` for async communication (_sfan5_)
    * `core.bulk_swap_node` (_ryvnf_)
    * `core.colorspec_to_table`, `core.time_to_day_night_ratio` (_grorp_)
    * vector utils (ceil, sign, abs, random\_in\_area) (_kromka-chleba_)
    * `core.is_valid_player_name` (_appgurueu_)
    * `vector.random_direction` (_kno10_)
    * `table.keyof` (_Emojigit_)
* Fixes related to ObjectRef lifecycles and crashes caused by attachments (_sfan5_)
* Various script API documentation improvements (_Zughy_, _nauta-turbidus_, _appgurueu_)

### Misc / Maintenance

* Lots of renaming work (_grorp_, _appgurueu_, _Wuzzy_)
* Server + client build targets will now build faster (_sfan5_)
* Tracy profiler support (_Desour_)
* Many cleanups and performance improvements (_sfan5_)
* Network improvements (_sfan5_, _red-001_)
* Compiling/build improvements and fixes (_nerzhul_, _AMDmi3_, _Zughy_, _sfan5_, _SmallJoker_)
* devtest game improvements (_appgurueu_, _Desour_)
* Various crash/sanity fixes

5.9.0 → 5.9.1
-------------

Released on 15 September 2024.

### Highlights

* Many bugfixes :)

### Client / Audiovisuals

* Reverted rendering optimizations that caused anomalies with certain hardware (_grorp_)
* Main menu: Mapgen flags starting with "no\*" are no longer shown (duplicate) (_appgurueu_)
* Android: Fixed input issues (_grorp_)
* Android: The minimap can again be proportional to the screen size (requires an up-to-date server) (_grorp_)
* Sneak-sumping onto a stack of 2 nodes is again possible (_SmallJoker_)
* Clouds no longer disappear when approaching them (_sfan5_)
* The CSM help dialogue now uses "." instead of "/" (_zmv7_)
* Windows: disabled touchscreen autodetection due to lack of support of the non-SDL build (default for 5.9.x) (_rubenwardy_)

### World / Server / Environment

* Network improvements for slow connections (_sfan5_)

### Script API / Modding

* yawsprite entities now work on OpenGL ES 2 (Android) (_sfan5_)
* Fixed animation not playing back on upright sprite entities on most systems (_appgurueu_)
* Bone overrides again return the same angles that were specified by mods to ease motion interpolation (_appgurueu_)
* Fixed animations not being restartable _appgurueu_)
* `minetest.show_formspec` with an empty formspec name is no longer marked as deprecated (_appgurueu_)

### Misc / Maintenance

* macOS 12 support (_sfence_)
* Various fixes
* Build fixes (_AMDmi3_)
* Windows: removed symlink that caused issues while extracting the game archive (_sfan5_)

5.8.0 → 5.9.0
-------------

Released 2024-08-11

### Highlights

* Rendering performance improvements (_paradust7_, _sfan5_ & _x2048_)
* Added godrays shader (_x2048_)
* New multithreaded Lua mapgen API to improve performance of custom mapgens. (_sfan5_)
* Android: Punch with short tap (_grorp_)
* Work in the background on switching to SDL2 for windowing and input (but not enabled in this release)

### Deprecations and compatibility notes

* "mod\_translation\_updater.py" is now located at [https://github.com/minetest/modtools](https://github.com/minetest/modtools) (_Zughy_)
* The setting "opaque\_water" is now called "translucent\_liquids". (_Xeno333_)
* Disabling fog and camera updates now requires the "debug" privilege (_sfan5_)
* Since 5.9.0-dev, the Minetest repository now includes IrrlichtMt. The minetest/irrlicht repository is no longer a dependecy of newer releases.
* nodebox and mesh nodes now require `use_texture_alpha` to render with transparency (_sfan5_)
* In the HUD elements defintion, `hud_elem_type` was renamed to `type` (_cx384_)
* Trusted mod directories are now readonly. Writing to any mod directory is now deprecated (_rubenwardy_)

### Work on SDL2

As part of Minetest's efforts to modernise and improve graphics code, we've been working on switching to SDL2 for windowing and input. This will allow all platforms to support touch screen, keyboard+mouse, and gamepads. Due to remaining issues, Minetest 5.9.0 does not use SDL2 yet. But the ground work is there to support it in the future

**Note: none of the following is available in 5.9.0 as SDL2 is disabled**

* Improved cross-platform touchscreen support. You can now use touchscreen controls on desktop without a special build. (_grorp_, _okias_)
* F11 to toggle fullscreen
* Support for hidef displays

### Client / Audiovisuals

* New setting `contentdb_enable_updates_indicator` to disable ContentDB requests (_rubenwardy_)
* Make main menu more responsive by using async HTTP calls everywhere (_grorp_)
* Formspecs are now closed by a single tap/click outside (_grorp_)
* Smooth scrolling (_grorp_)
* Add `repeat_dig_time` setting (_ryvnf_)
* Add support for translating content titles and descriptions (_rubenwardy_)
* Rendering performance improvements (_paradust7_, _sfan5_ & _x2048_)
* Add help formspec for CSM commands (_Zemtzov7_)
* Android: Fix app name in the notifications (_srifqi_)
* Android: Add selection dialog (drop down/combo box) (_srifqi_)
* Remove controls listed in the pause menu (not suited for touch inputs) (_Zughy_)
* Remove server's address and port from pause menu (_srifqi_)
* Fix semi-transparent appearance of objects (players/entities) when shaders are disabled (_SmallJoker_)
* Allow mods to swap the meaning of short and long taps (punch with short tap) (_grorp_)
* Recognize double-taps as double-clicks (_grorp_)
* Make the loading screen progress bar respect "gui\_scaling" (_grorp_)
* Initial implementation of 'Godrays' shader (_x2048_)
    * Make volumetric light effect strength server controllable (_lhofhansl_)
* Android: Pause rendering while the app is paused (efficiency) (_grorp_)
* Add dithering, enabled by default, setting `debanding` (_HybridDog_)
* `sound_volume_unfocused` for custom sound volume on focus loss (_srifqi')_

### World / Server / Environment

* Minimap textures can now be overwritten by the server (_cx384_)
* Add flag to control mgv6 temple generation (_sfan5_)
* Android: safer and more reliable setting saving (_grorp_)
* Fix multiple password changes in one session (_savilli_)
* More performant improvement object (player/entity) management (_sfan5_)
* Mapblock loading / view range fixes (_lhofhansl_)
* Setting `protocol_version_min` (_Warr1024_)
* Inventory changes
    * Usability fixes (_sfence_)
    * Reordering of inventory callbacks (_SmallJoker_)
    * Prevent item loss when stacking oversized ItemStacks (_SmallJoker_)
* Avoid movement jitter while attached (_lhofhansl_)
* Fixed improper liquid flow (_ZenonSeth_)

### Script API / Modding

* `core.override_item` additional parameter for fields to remove (_appgurueu_)
* Collision moveresult now provide the object's own position (_grorp_)
* Add physics overrides for walk speed and Fast Mode (_grorp_)
* Allow `nil` puncher in `` ObjectRef:punch(..)` `` (_sfence_)
* HUD: Text element color support (_SmallJoker_)
* Allow optional actor in `core.(place|dig|punch)_node` (_Emojigit_)
* Add button\_url\[\] and hypertext element to allow mods to open web pages (_rubenwardy_)
* Add world-independent storage directory for mods (_rubenwardy_)
* ItemMetaData-controlled pointing range (_cx384_)
* Add L-system trees as decorations (_cx384_)
* Expose SHA256 algorithm to Lua (_sfan5_)
* Multi-threaded Lua for mapgen (_sfan5_)
    * This is a set of new API functions
* Allow dynamic\_add\_media at mod load time (_sfan5_)
* Move hard coded minimap to Lua (builtin) (_cx384_)
* Tool items: Add wear bar color API (_techno-sam_)
* Improved `[combine` parameter checks (_sfan5_)
* Fog API
    * Fix fog moon tint not working (_appgurueu_)
    * Allow fog color to be overriden in all cases (_sfan5_)
* Fix revoke callbacks being run for `false` values passed to `set_privileges` (_appgurueu_)
* Implement `pointabilities` API to selectively point or block the raycast of tool items (_cx384_, _lhofhansl_)
    * \+ Lua raycast support (_grorp_)
* Add rotation support for wallmounted nodes in 'ceiling' or 'floor' mode (_Wuzzy_)
* Add API for restoring PseudoRandom (discouraged) and PcgRandom (recommended) state (_sfence_)
* Add `player:hud_get_all()` (_cx384_)
* Fix dividing by zero crashes in texture modifiers (_cx384_, _SmallJoker_)
* More modder-friendly output of the Lua profiler (_fluxionary_)
* Add `ObjectRef:add_pos(..)` (_sfence_)
* Rename `hud_elem_type` to `type` (_cx384_)
* Fix `on_(grant|revoke)` not being run by mods (_appgurueu_)
* Extend bone override capabilities (`ObjectRef:set_bone_override`) (_appgurueu_)
* Add `touch_controls` to `core.get_player_window_information()` (_grorp_)
* Persistent formspecs (re-sent on close) can no longer be closed (_SmallJoker_)

### Misc / Maintenance

* Many different documenation improvements
* Mod translation script improvements (_srifqi_, _sfan5_)
* Rename \`MINETEST\_SUBGAME\_PATH\` to \`MINETEST\_GAME\_PATH\` (_cx384_)
* Updates of the bundled libraries and Lua fixes (via _sfan5_)
* Support OpenGL 3 (_numberZero_)
* Network code maintenance (_sfan5_)
* Build system maintenance (_sfan5_, _siboehm_)
* Unittest and benchmark improvements (_sfan5_, _numberZero_)
* Other code maintenance and improvements (_sfan5_)
* Update to Android SDK 34 (_rubenwardy_)

### Minetest Game

* No longer bundled in Minetest. Please have look at [https://github.com/minetest/minetest\_game/](https://github.com/minetest/minetest_game/)

5.7.0 → 5.8.0
-------------

Released on 4 December 2023.

### Deprecations and compatibility notes

* **Minetest Game is no longer the default game and will no longer be shipped by Minetest.** If you want it back, install it by using the “Content” tab
* `lua_api.txt` has been converted to Markdown and renamed to `lua_api.md`
* Android now builds via CMake (_sfan5_)
* Compiling: C++17 support is now required
* Node definition field `air_equivalent` is now documented—as deprecated.
* Reading/defining initial object properties directly from an entity definition is deprecated; they should be moved to `initial_properties`

### Client / Audiovisuals

* Main menu: Redesign and unify settings interface (_rubenwardy_, _grorp_, icon by _Zughy_)
* Main menu: better prompt to install a game when none is installed (_ROllerozxa_)
* Main menu: various fixes (_grorp_, _ROllerozxa_)
* ContentDB GUI: Load package list asynchronously (_grorp_)
* Option to invert direction or disable mouse wheel for hotbar item selection (_srifqi_)
* Inventory mouse shortcut improvements (_OgelGames_)
    * Holding down Shift+click while moving the mouse over item slots now continously moves items to other inventory (if available)
    * Press Shift+click on the crafting output slot to craft and move result to inventory
        * Left mouse button: Craft as many as possible
        * Mouse wheel: Craft 10 times
        * Right mouse button: Craft once
    * Drag an item stack over empty slots to split stacks evenly
    * Hold down Left mouse button while holding an item stack and move the cursor over the slots to pick up items of the same type
    * Double-click an item stack to pick up all items of the same type in this inventory
* Implement `check_offset` for decorations (_nephele-gh_)
* Touchscreen input improvements (_srifqi_)
* Rendering-related performance improvements and fixes (_numberZero_)
* Add antialiasing filters (FXAA, SSAA) (_x2048_)
* Reverse eye-offset Z-coordinate in 3rd person front view (_lhofhansl_)
* DPI-aware crosshair (_grorp_)
* Prevent early respawns caused by up/down button in the death screen (_srifqi_)
* Sounds and animations are now paused in pause menu in singleplayer (_DS_)
* Android: Place nodes with single tap (_grorp_)
* Android: Higher default graphics settings (_grorp_)
* Android: Auto-detect locale (_grorp_)
* Android: ignore broken language files (_srifqi_)
* X11 (Linux): Add primary selection (copy & paste via select & middleclick) support (_DS_)

### World / Server / Environment

* Major speedup for crafting shapeless craft recipes (Hocroft-Karp algorithm) (_DS_)
* Fix crash on handling wallmounted nodes with invalid param2 (_savilli_)
* Fix biomes not repecting their Y limits (_Radar6255_)
    * Especially thin biomes will now be generated as intended.
* Saner (HTTP) timeout limits and log messages (_sfan5_)

### Script API / Modding

* Reading/defining initial object properties directly from an entity definition is deprecated; they should be moved to `initial_properties`
* Add ability to override item images using ItemMetaData (_rubenwardy_)
* Add node pos to node damage HP change reason (_Radar6255_)
* Add `vector.in_area()` utility function (_AFCMS_)
* Add focused styling to buttons (_rubenwardy_)
* Add min/max protocol version to `minetest.get_version()` (_BuckarooBanzay_)
* Add additional texture modifiers (_Treer_)
* Add node group `disable_descend` to disable actively descending down climbable nodes and nodes with liquid move physics (_Wuzzy_)
* Add `VoxelArea::intersect()` (_sfan5_)
* Allow nodes to have their `post_effect_color` affected by lighting (_grorp_)
* Fix potential freeze in `core.check_for_falling` (_savilli_)
* Send everlasting particle spawners to all players (_chmodsayshello_)
* Allow `place_param2 = 0` node placement predictions (_SmallJoker_)
* New player physics overrides for climb speed, sneak speed, acceleration, liquid fluidity and liquid sink speed (#11465) (_Wuzzy_)
* Allow to set custom third person front view camera offset (_grorp_)
* Add script to update/generate mod translations: `util/mod_translation_updater.py` (_Wuzzy_)
    * See `util/README_mod_translation_updater.md` for details
* Add `start_time` to sound parameter tables (part of #12764) (_DS_)

### Misc / Maintenance

* Entity/Object fixes and unittests (_numberZero_)
* Lua environment cleanups and improvements (_sfan5_)
* Various documentation improvements (_Zughy_, _Wuzzy_)
* Inventory code fixes (_SmallJoker_, _DS_)
* Many various code fixes (_sfan5_, _grorp_, _srifqi_)
* Opt-out option for Doxygen generation on build (_nerzhul_)
* Sound code cleanups and improvements (#12764) (_DS_)
    * Long sounds in sound packs, or sent via dynamic media, no longer cause client freezes on load
    * Positional sounds can be faded now
    * Documentation
    * Other improvements listed elsewhere
* Faster client load times (#12764 and irr#233) (_DS_)

### Minetest Game

* **Minetest Game is no longer the default game and no longer installed by default**
* New water textures (the old ones were [non-free](https://github.com/minetest/minetest_game/issues/3051)) (_Lopano_)
* Improve leaves textures in "Opaque Leaves" mode (_Wuzzy_)
* When a player dies in protected air, bones now spawn as a block instead of dropping as an item (_OgelGames_)
* Add API for sapling growth (_aegroto_)
* Hook callbacks for `default.set_inventory_action_loggers` (_appgurueu_)
* Fix logic error in bed rotation (_fluxionary_)
* Fix coral and kelp duplication glitch with sticky piston from Mesecons mod (_zmv7_)
* Fix players being able to skip many nights at once by spam-clicking bed (_appgurueu_)
* Fix not updating vessel shelf infotext (_Niklp_)
* Fix bookshelf infotext not updating when adding, removing or moving items inside (_Montandalar_, _appgurueu_)
* Update translations: German (_Wuzzy_), Spanish (_David Leal_), Ukrainian (_Andriy_), French (_xin_)

5.6.0 → 5.7.0
-------------

Released on 8 April 2023

### Deprecations and compatibility notes

* The default key for pitchmove was removed. Specify a key manually to use this feature.
    * See [https://github.com/minetest/minetest/pull/13319](https://github.com/minetest/minetest/pull/13319) for details
* Special handling of `${key}` syntax in metadata values are deprecated
    * See [https://github.com/minetest/minetest/pull/12970](https://github.com/minetest/minetest/pull/12970) for details
* Worlds with unresolved dependencies can no longer be loaded. This ensures that the specified mods are loaded properly.
    * See [https://github.com/minetest/minetest/pull/12542](https://github.com/minetest/minetest/pull/12542) for details
* The default key for (un)limited range was removed. Specify a key manually to use this feature.
    * See [https://github.com/minetest/minetest/pull/12632](https://github.com/minetest/minetest/pull/12632) for details
* Development Test is no longer being distributed in official Minetest releases
    * This was never meant for players to begin with, this “game” is exclusively meant for engine development
    * To get it back, build Minetest from source code (recommended) or download Development Test from [ContentDB](https://content.minetest.net/packages/Minetest/devtest/)

### Client / Audiovisuals

* Fix main menu error when submitting invalid port numbers (_GoodClover_)
* Fix ChatPrompt crash in very narrow windows (_DS_)
* Fix missing shadows when sun tilt is zero (_x2048_)
* Android: Make OpenGLES 2 the default driver (_ROllerozxa_)
* 8x block meshes for improved performance (_x2048_)
    * Configuration options and bugfixes (_lhofhansl_, _x2048_)
* Decrease minimum for repeat\_place\_time (_DS_)
* Fix Enter key after creating a new world (_srifqi_)
* Improve chat history (_TurkeyMcMac_)
* Add dynamic exposure correction (_x2048_)
    * This is also configurable by the Lua API
* Improve the occlusion culling algorithm (i.e. better efficiency) (_x2048_)
* Use multiple threads for mesh generation (i.e. faster rendering) (_x2048_)
* Removed pageflip 3D mode (because broken) (_ROllerozxa_)
* Fix progress bar look on HiDPI displays (_kilbith_)
* Fix `plantlike_rooted` world-aligned node base textures (_TurkeyMcMac_)
* Fix issues caused by attached node placement prediction (_TurkeyMcMac_)
* Avoid shadow flicker at certain angles (_x2048_)
* Chat: fix the unicode characters crowded together on prompt (_snowyu_)
* Take geographic distance into account for server list ordering (_sfan5_)
* Fix sneaking on nodes with large collision boxes (_SmallJoker_)
* Faster light calculations for rendering (_TurkeyMcMac_)
* Android: Improve double-tap for jump detection (_srifqi_)
* Add Bloom shader (_x2048_)
* Restore and enhance bouncy behavior (_pecksin_)
    * Bouncy nodes now let you control the jump height with the jump/sneak keys
* Fix `liquid` drawtype faces sometimes not rendering (_Wuzzy_)
* Apply DPI Scaling to the main menu (_ElliottLester_)
* Improve shadow updates efficiency (_x2048_)
* Textures: introduce world-align overrides (_SmallJoker_)
* Fix crash when stars are reset (_Zughy_)

### World / Server / Environment

* Reduce server CPU consumed by occlusion culling (_lhofhansl_)
* Improve loaded block handling (i.e. better efficiency) (_lhofhansl_)
* Fix `/help` privs checks (_TurkeyMcMac_)
* Add mod storage PostgreSQL backend (_TurkeyMcMac_)
* Update floating nodes when liquid underneath vanishes (_TurkeyMcMac_)
* Add zstd compression support to API function (_20kdc_)

### Script API / Modding

* Server: Fix error caused by sending too long chat messages (_SmallJoker_)
* Correct handling of leftover items in `core.item_eat` (_DS_)
* Various lua\_api.txt clarifications and fixes (_Wuzzy_, _jordan4ibanez_, _kab0u_, _veprogames_, _aerkiaga_, _DS_)
* Improve `minetest.close_formspec` server-side safety (_luk3yx_)
* Handle nodes changed within another LBM and ABM loop (_TurkeyMcMac_)
* Fix segfault caused by invalid PNG data in `[png:` (_SmallJoker_)
* Add `minetest.get_player_window_information()` (_rubenwardy_, _DS_ (bugfix))
* Make `body_orbit_tilt` configurable (_sofar_)
* Add chat HUD flag (#13189) (_GreenXenith_)
* Improve `MetaDataRef:{get,set}_float` precision (_TurkeyMcMac_)
* Fix error caused by an empty separator for `string.split` (_TurkeyMcMac_)
* Add `player:set_lighting( {saturation = float} )` (_lhofhansl_)
* Add callback `on_mapblocks_changed` (_TurkeyMcMac_)
* Improved Lua error handling (_TurkeyMcMac_)
* Expose `dtime_s` to LBM handler (_sfan5_)
* Let mods choose a forceload limit (_TurkeyMcMac_)
* Add `minetest.get_mapgen_edges` (_TurkeyMcMac_)
* Add `minetest.get_game_info` and allow reading game.conf (_TurkeyMcMac_)
* Add support for facedir/4dir nodes to be attached with `attached_node` (_Wuzzy_)
* Add additional `attached_node` options: always attach to ceiling, always attach to floor (_Wuzzy_)
* Fix errors caused by schematic reading (_TurkeyMcMac_)
* Fix `set_nametag_attributes` resetting the text in subsequent calls (_snowyu_)
* game.conf: Add setting to use volatile a map backend (_SmallJoker_)
* Allow rotating entity selectionboxes (_appgurueu_)
* Add VoxelArea() constructor for easier use (_TurkeyMcMac_)
* Fix formspec focus issue caused by empty element names (_DS_)
* Faster vector, node and content ID access when using LuaJIT (_TurkeyMcMac_)
* Speed up find\_nodes\_in\_area (_TurkeyMcMac_)
* Add an item pick up callback (_DS_)
* Implement tool use sounds (_sfan5_)
* Fix inconsistent craft replacement behavior (_Wuzzy_)
* Fix potential error in craft recipes (_savilli_)
* Add paramtype2s `4dir` and `color4dir` for 4 horizontal rotations and 64 colors (_Wuzzy_)
* Bugfix: Allow looped animation to be used safely with old clients (_sfan5_)
* Reassure previous nil behaviour for `tiles` and `special_tiles` (_Zughy_)
* Add buffer argument to `VoxelManip:get_light_data` (_TurkeyMcMac_)
* Fix crash when crafting callbacks return strings (_Zughy_)

### Misc / Maintenance

* Fix crash while exiting to the main menu on macOS (_x2048_)
* Rendering code cleanups (_x2048_)
* Fix occasional black screen on startup (_x2048_)
* Android: Build and logging improvements (_sfan5_)
* Improve installation instructions (_lynx197_, _sofar_, _tamara-schmitz_)
* Various code cleanups and optimizations (_sfan5_, _ROllerozxa_, _nerzhul_, _GermanAizek_)
* Implement --debugger option to improve UX when debugging crashes (_sfan5_)
* Various Development Test changes
    * Many, many additions and improvements (_Wuzzy_)
    * Add jukebox and branding iron (_DS_)
* Development Test is no longer officially distributed with Minetest releases
* Android: various maintenance and fixes (_srifqi_)
* Unittest improvements (_Wuzzy_, _TurkeyMcMac_, _rubenwardy_)

### Minetest Game

* Limit and sanitize formspec fields (_appgurueu_)
* Fix player\_api.set\_model not updating the animation (_appgurueu_)
* Ensure chests close properly (_fluxionary_)
* Ensure proper creative hand override (_AntumDeluge_)
* Fix error if /home is executed with an invalid name (_zmv7_)
* Fix wall craft registrations (_alek13_)
* Screwdriver: 4dir node support (_Wuzzy_)

5.6.0 → 5.6.1
-------------

Released on 19 September 2022.

### Client / Audiovisuals

* Fix tooltips for dropdown, scrollbar and more (_Desour_)
* Allow the comma as clickable URL component (_pecksin_)
* Correct the entity glow calculation (_x2048_)
* Get the setting `texture_min_size` to work again (_fluxionary_)
* Scale hardcoded/integrated GUIs with the system-reported DPI (_ElliottLester_)
* Overwriting a package via "Content" no longer triggers an error (_rubenwardy_)

### World / Server / Environment

* Fix potential use-after-free with item metadata (_TurkeyMcMac_)
* Compatibility patch to not freeze older clients due to negative "frame\_length" Tile Animation values (_sfan5_)
* Dynamic shadows performance improvement by delaying non-urgent mapblocks (_x2048_)

### Script API / Modding

* Fix several crashes caused by `clear_craft` in combination with aliases (_savilli_)
* Serialization: Restore (full) pre-5.6.0 compatibility (_appgurueu_)
* LuaJIT: Workaround to allow larger serializations (_appgurueu_)
* Enforced hp\_max > 0 for entities (_appgurueu_)
* Node Definition "tiles" and "special\_tiles" again default to `nil` when not specified (_Zughy_)
* Allow `minetest.register_on_craft` to return strings (was: ItemStack) (_Zughy_)
* `ObjectRef:set_stars` to reset the stars no longer throws an error (_Zughy_)

### Misc / Maintenance

* x86 Android build fixes (_savilli_)

5.5.0 → 5.6.0
-------------

Released on 4 August 2022

### Deprecations and compatibility notes

* `name` in game.conf is deprecated for the game title
    * For specifying the game title from now on, use `title` instead

### Client / Audiovisuals

* Dynamic shader-based shadows for: nodes, entities, wield (_x2048_)
    * Includes many, many bugfixes and improvements (tuning, performance)
* Fixed statbar HUD background scaling and numbering (_appgurueu_)
* Apply texture pack main menu textures immediately (_ROllerozxa_)
* Fix footsteps for players whose collision box min y != 0 (_grorp_)
* Add depth sorting for node faces (_x2048_)
    * This fixes appearance issues when looking through multiple semi-transparent nodes.
    * This works only up to a distance of 16 nodes by default. Use the `transparency_sorting_distance` setting to adjust this
* Optimize swapping nodes with equivalent lighting (_TurkeyMcMac_)
* Fix item entity Z-fighting (_appgurueu_)
* Use mod names/titles instead of technical names to display (_GoodClover_)
* Fix texture packs not showing as enabled in mainmenu (_rubenwardy_)
* Debug screen now shows "<unknown node>" at the top if an unknown node is pointed (_Wuzzy_)
* Enable chat clickable weblinks by default (Ctrl+Click) (_Froggo_)
* HUD: Fix outdated selection boxes (_appgurueu_)
* Make `no_screenshot` image more clear (_Zughy_)
* Add register dialog to separate login/register (_rubenwardy_)
* No damage effects on `hp_max` change (_appgurueu_)
* Fix updating glow and light calculation on entities (_sfan5_)
* Fix unknown nodes sometimes displaying the "no texture" instead of the "unknown node" texture (_Wuzzy_)

### World / Server / Environment

* Distinct mod path values in world.mt to avoid issues with duplicated mod names (_rubenwardy_)
* Fix broken server startup if curl is disabled (_sfan5_)
* Increase max. objects per block defaults (_appgurueu_)
* Builtin: Allow to revoke unknown privileges (_SmallJoker_)
* Fix some textures not being sent correctly to older clients (_Oblomov_)
* Fix several registration/authentication related issues (_sfan5_)
* Fix dependency enabling of mods and modpacks (_rubenwardy_, _TurkeyMcMac_)
* Fix cooking and fuel crafts with aliases (_TurkeyMcMac_)
* Commands: Some numbers can be replaced or prepended with "`~`" for values relative to the current one (_Wuzzy_)
    * "`~`" is equivalent to "`~0`"
    * Supported commands: `/deleteblocks`, `/emergeblocks`, `/fixlight`, `/spawnentity`, `/teleport`, `/time`
    * Example: "`/teleport 15 ~5 ~`" teleports to (15, <current Y coordinate plus 5>, <current Z coordinate>)
* Don't allow banning in singleplayer (_sfan5_)
* Docs: Add description of privileges (_x2048_)
* Increase max FPS on Android to 60 (_ROllerozxa_)
* Add many limits to settingtypes + engine (_Wuzzy_, _SmallJoker_)
* Reorganise settingtypes.txt (_rubenwardy_)

### Script API / Modding

* Improved formspec documentation (_DS_)
* Optimization: Send HUD flags only if they changed (_appgurueu_)
* Allow to set the displayed item count and its alignment via item meta: `count_meta`, `count_alignment` (_DS_)
* Add support for 'seed' in `disallowed_mapgen_settings` (_Wuzzy_)
* List of documentation improvements:
    * `AreaStore` (_SmallJoker_)
    * Lua `vector` helper class (_sfan5_)
    * `spawn_by` for decorations (_Zughy_)
    * LBM documentation (_TurkeyMcMac_)
    * Overall improvements (_sfan5_)
* Allow `get_sky` to return a table of all sky-related parameters (_Zughy_)
* Add `basic_debug` HUD flag to control display of debug info like position in the debug screen (on by default) (_appgurueu_)
* Fix memory leak from `SpatialAreaStore` (_setupminimal_)
* Add function `ObjectRef:set_lighting()` to control shadow intensity from the game/mod (_x2048_)
* Fix '`[combine`' when `EVDF_TEXTURE_NPOT` is disabled (_paradust7_)
* `hud_get`: Return precision field for waypoint (_appgurueu_)
* Add Async environment for parallelized Lua code execution (_sfan5_)
    * `minetest.handle_async`
    * `minetest.register_async_dofile`
* Fix Minetest blaming the wrong mod for errors (_appgurueu_)
* Deprecate game.conf `name`, use `title` instead (#12030) (_rubenwardy_)
* Protect a few more settings from being set from mods (_sfan5_)
* Add function `ObjectRef:respawn()` to invoke player respawn (_sfan5_)
* Handle Lua entity HP changes correctly (like punches) (_sfan5_)
* Add tool helper function `ItemStack:add_wear_by_uses()` to add tool wear in such a way that it has a given number of uses (_Wuzzy_)
* Add `minetest.get_tool_wear_after_use` to simulate tool wear when expecting it to break after a given number of uses (_Wuzzy_)
* `on_deactivate` entity callback: distinguish removal and unloading (_appgurueu_)
* Remove `tile_images` and `special_materials` obsolete code (_Zughy_)
* `set_stars`: Allow to set maximum star opacity at daytime with `day_opacity` (_Wuzzy_)
* FormSpec: 9-slice images, `animated_image`, and `fgimg_middle` (_v-rob_)
* Animated particle spawners (_velartrill_)

### Misc / Maintenance

Code details are intentionally omitted due to the changelog target audience's interests.

* Fix macOS compile instructions (_sfan5_)
* Various C++ code cleanups and improvements (_TurkeyMcMac_, _sfan5_, _Oblomov_, _SmallJoker_, _Octavian_, _RichardTry_, _savilli_, _JosiahWI_)
* List of DevTest game improvements:
    * TGA test nodes (_ehrlemann_)
    * Test weapons and armorball modes (_Wuzzy_)
    * Nodes and items for testing overlays (_Wuzzy_)
    * Entity lifecycle and callbacks (_sfan5_)
    * Item metadata editor (_Wuzzy_)
* Minetest now uses C++14
* Remove direct OpenGL(ES) dependency (_sfan5_)
* Compile Lua as C++ to properly catch exceptions (_TurkeyMcMac_)
* Build system improvements (_sfan5_, _ShadowNinja_, _LoneWolfHT_)
* Run automated tests when Lua files change (_x2048_)
* Add JSON (de)serialization benchmarks (_paradust7_)
* Performance optimizations by caching (mapblocks, collisionbox) (_sfan5_)
* Add more Prometheus metrics (_sfan5_)
* Add documentation to list breaking changes for the next major release (_Zughy_)
* Patch built-in Lua to fix miscompile on Android (_paradust7_)
* Fix BSD iconv declaration (_savilli_)
* Fix Android input box crash (_ROllerozxa_)

### Minetest Game

* Improved cart movement behavior (_SmallJoker_)
    * Improved direction handling
    * Smoother-out 'end-of-rail' animation
    * Other improvements
* Dynamic shadow intensity increases with cloud density (only has an effect if you have dynamic shadows enabled) (_lhofhansl_)
* Allow mods to override player animation globalstep with `player_api.globalstep` (_LoneWolfHT_)
* Log API added (_nixnoxus_)
* Fix crash if player has no model (_Lars Mueller_)
* Fix broken `get_animation` in `player_api` (_bell07_)
* Fix furnace fire sound continuing to play after being destroyed (_Wuzzy_)
* Fix TNT blowing up `ignore` nodes (_Wuzzy_)
* Fix some hoes not breaking after the intended number of uses (_Wuzzy_)
* Fix book duplication glitch (_appgurueu_)
* Fix incorrect behavior of glass and obsidian glass if param2 was changed (_appgurueu_)
* Fix cart sometimes facing the wrong way at slopes (not a 100% perfect bugfix tho) (_SmallJoker_)
* New translation: Polish (_mrubax10_)
* Translation updates: Ukrainian (_baytuch_), Russian (_baytuch_), German (_Wuzzy_), Lojban (_Wuzzy_), Esperanto (_quarthex_)

5.5.0 → 5.5.1
-------------

Released on 15 May 2022.

### World / Server / Environment

* Fix server crash due to duplicate user registrations (_sfan5_)
* Fix cooking and fuel crafts with aliases (_Jude Melton-Houghton_)
* Fix some textures not being sent correctly to older clients (_Giuseppe Bilotta_)
* Fix broken server startup if curl is disabled (_sfan5_)
* Fix password changing getting stuck if wrong password is entered once (_sfan5_)
* Apply disallow\_empty\_password to password changes too (_sfan5_)

### Client / Graphics

* Fix various issues with Select Mods and Content (_rubenwardy_, _Jude Melton-Houghton_, _Alex_)
* ContentDB: Fix ungraceful crash on aliases when list download fails (_rubenwardy_)
* Fix performance issue due to hardware buffer counters (_paradust7_)
* HUD: Update selection highlight every frame to avoid glitches (_Lars Müller_)
* Fix '\[combine' when EVDF\_TEXTURE\_NPOT is disabled (_paradust7_)
* Fix footsteps for players whose collision box min y != 0 (_Gregor Parzefall_)
* Fix undefined behavior in TileLayer (_Daroc Alden_)
* Use absolute value for bouncy in collision (_pecksin_)
* Fix builtin statbar backgrounds (_Lars Mueller_)

### Misc

* Fix possible unreliable behavior due to uninitialized variables (_Octavian_)
* Fix Minetest blaming the wrong mod for errors (_Lars Müller_)
* Fix some memory leaks (_SmallJoker_, _Daroc Alden_, _Daroc Alden_)

### Minetest Game

* player\_api mod: Fix crash if player has no model (_appgurueu_)
* player\_api mod: Mods can now override globalstep by overriding player\_api.globalstep (_LoneWolfHT_)
* Shadow intensity (of dynamic shadows) changes with weather (_lhofhansl_)
* Some cart movement behavior fixes (_SmallJoker_)
* Fix some translations in uk and ru locales (_baytuch_)

5.4.0 → 5.5.0
-------------

Released on 30 Jan 2022.

### Deprecations and compatibility notes

* FORMSPEC\_API\_VERSION is now 5
* New maps are now zstd compressed to reach faster and/or more efficient compression
* Switched to our own fork of the rendering engine: IrrlichtMT
    * Removed support for DirectX
    * Dropped support for obscure and undocumented file formats: pcx, ppm, psd, wal, and rgb
* Modding: Missing "mod.conf" is now deprecated. Results in warnings (_rubenwardy_)
    * Add mod.conf with name = yourmodname
* Modding: depends.txt and description.txt are now deprecated
    * Specify dependencies using "depends" and "optional\_depends" in mod.conf
    * Specify description using "description" in mod.conf
* Modding: Creating vectors like this: `{x=1, y=2, z=3}` is now deprecated
    * Use `vector.new` instead
* Bitmap fonts are no longer supported
    * Use TTF fonts instead

### Features: General

* Add game name to server status string (_sfan5_)
* Improve TTF support for pixel-style fonts (_v-rob_)
* Joystick support for DragonRise GameCube controller (_Izzette_)
* Add "`MINETEST_MOD_PATH`" environment variable (_emixa-d_)
* Touch UI support for desktop builds (#10729) (_TheBrokenRail_)
* Switch MapBlock compression to zstd (_lhofhansl_)
* Joystick sensitivity for player movement (_NeroBurner_) + fixes (_sfan5_)
* Gettext support on Android (_Pevernow_)
* Make web links in chat clickable (Feature disabled by default, use setting `clickable_chat_weblinks`) (_pecksin_)
* Add a key to toggle display map block boundaries (F8 by default) (_grapereader_)
* Improved wording of various chat command outputs (_Wuzzy_)
* Normal texture support (for minimap shading) (again) (_numberZero_)
* Scale mouse/joystick sensitivity depending on FOV (_Elias Åström_)
* Various DevTest game additions and improvements (_Wuzzy_)
* Chat commands: Show the execution time if the command takes a long time (_HybridDog_)
* Improved item placement prediction (_sfan5_)
* Anticheat: Faraway inventory access protection (_SmallJoker_)
* Pause animations while game is paused (_numberZero_)

### Features: Main menu and ContentDB

* Chop game background in mainmenu (_appgurueu_)
* ContentDB: Add support for package aliases / renaming (_rubenwardy_)
* Improved "Join Game" tab (_sfan5_)
* Builtin function translation (_Wuzzy_, _Zughy_)
* Translation support for the builtin functions (_Wuzzy_, _snowyu_) + updates (_Wuzzy_, see CONTRIBUTING file)
* Handle modpacks containing modpacks properly (_Elias Fleckenstein_)
* Texture pack toggle by double clicking (_Yaman Qalieh_)

### Features: Modding

* Sky API: Reset by empty arguments (_Zughy_)
* Use a database for mod storage (internal) + CSM auto-migration (_TurkeyMcMac_)
* Add padding\[\] element to formspecs (#11821) (_v-rob_)
* Disable inventory if player's inventory formspec is blank (_ROllerozxa_)
* Add minetest.disconnect\_player (_Corey Powell_)
* Add Lua bitop library (_Lejo_)
* Allow for game-specific menu music (_ExeVirus_)
* Add minetest.rmdir, minetest.cpdir and minetest.mvdir (_octacian_)
* Add no\_texture.png as fallback for unspecified textures (_Wuzzy_)
* Add minetest.get\_server\_max\_lag() (_Wuzzy_)
* Split node field 'liquid\_viscosity' into two: liquid\_viscosity (how fast liquid flows) and move\_resistance (how much it slows players) (_Wuzzy_)
* Improved dynamic\_add\_media functionality (_sfan5_)
* Add group-based tool filtering for node drops (_Treer_)
* Add disable\_settings to game.conf to get rid of "Enable Damage"/"Creative Mode"/"Host Server" checkboxes (_Df458_)
* Add a simple PNG image encoder with Lua API + texture modifier `[png` (_hecks_)
* Add bold, italic and monospace font styling for HUD text elements (_sfan5_)
* Add wallmounted support for plantlike and plantlike\_rooted nodes (_Wuzzy_)
* Add API for mods to hook liquid transformation events (_Warr1024_)
* Add min\_y and max\_y checks for Active Block Modifiers (ABM) (_sfence_)
* Add metatables to Lua vectors (_DS_)
* Add minetest.compare\_block\_status function (_SmallJoker_)
* Add minetest.colorspec\_to\_colorstring (_v-rob_)
* Put torch/signlike node on floor if paramtype2=="none" (_Wuzzy_)
* Return ObjectRef from minetest.spawn\_falling\_node() (_benrob0329_)
* Modifyable player fall damage via armor group (_Wuzzy_)
* Add vector.to\_string and vector.from\_string (#10323) (_DS_)
* Add math.round and fix vector.round (_v-rob_)
* Degrotate support for mesh nodes (_numberZero_) + fixes (_sfan5_, _Wuzzy_)
* lua\_api.txt: Fix style selector examples (_Df458_)
* Nested Settings are now also contained in to\_table (_SmallJoker_)

### Bugfixes

* Fix Minetest logo when installed system-wide (_ROllerozxa_)
* Cancel emerge callbacks on shutdown (_TurkeyMcMac_)
* Free arguments of cancelled minetest.after() jobs (_sfan5_)
* Fix damage wraparound if very high damage (_Wuzzy_)
* Cap damage overlay duration to 1 second (_Wuzzy_)
* Rendering fixes: Add more neighbors on mesh update (_numberZero_)
* Don't let HTTP API pass through untrusted function (_sfan5_)
* Fix URL escaping in content store (_sfan5_)
* Fix find\_nodes\_in\_area misbehaving with out-of-map coordinates (_sfan5_)
* Minimap: gamma-correct average texture colour calculation (_HybridDog_)
* Fix item duplication if player dies during interact callback (_sfan5_)
* View bobbing fixes (_appgurueu_)
* Fix player HP desync between client and server (_savilli_)
* Rendering fixes: Order drawlist by distance to the camera (_x2048_)
* Fix crash when .conf release field is invalid (_rubenwardy_)
* Performance: Fix client-side performance of chat UI (_DS_)
* Fix HUD multiline text alignment (_appgurueu_)
* Send correct updates to clients after node metadata clear (_TurkeyMcMac_)
* Remove redundant on\_dieplayer calls (_savilli_)
* Fix 6th line of infotext being cut off in half (_Wuzzy_)
* Validate staticdata and object property length limits (_sfan5_)
* Fix scaled world-aligned textures being aligned inconsistently for non-normal drawtypes (_Wuzzy_)
* Various lua\_api.txt corrections and improvements (_Df458_, _random-geek_, _Wuzzy_, _Francisco_, _Zughy_)
* Run on\_grant and on\_revoke callbacks after privs change (_AFCMS_)
* Fix base64 validation and add unittests (_appgurueu_)
* Fix cloud fog being broken for high clouds (_Wuzzy_)
* Attachments: various bugfixes (_SmallJoker_)
* Rendering engine fxes and cleanups (_nerzhul_)
* Multiple OpenGL ES fixes (_sfan5_)
* Make edit boxes respond to string input (IME) (_yw05_)
* cURL timeout fixes and increased default timeout (_sfan5_)
* Fix wield image of plantlike\_rooted (_Wuzzy_)
* Fix attached-to-object sounds volume (_Desour_)
* Fix segfault for model\[\] without animation speed (_kilbith_)
* Crash fix when models fail to load (_sfan5_)
* Access protections for per-player detached inventories (_SmallJoker_)
* mg\_name and mg\_flags can no longer be set by Lua (minetest.conf) (_sfan5_)
* Interlaced 3D mode fixes (_srifqi_)
* Fix hud\_change and hud\_remove functionality after hud\_add calls (_savilli_)
* Fix number of times a tool can be used before breaking being off by a number between 1 and 32767 (_Wuzzy_)
* Various stability fixes (server and client crashes)

### Maintenance

* Rendering improvements: use dedicated GPU, improve frame calculations (_sfan5_)
* Fully remove bitmap font support (use TTF now) (_sfan5_)
* Restore GCC 5 compatibility (_JosiahWI_)
* Remove creative/damage info in Esc/Pause menu (_Wuzzy_)
* Update to Android target SDK 30 (_rubenwardy_)
* Add macOS build docs (_andkerr_)
* Android: Use scoped app storage (_rubenwardy_)
* Make /status message easier to read (_Wuzzy_)
* Clean up/improve some scriptapi error handling code (_sfan5_)
* Add hint to error message on how to build with in-tree Irrlicht (_20kdc_)
* Optimize vector length calculations (_Lean Rada_)
* Remove hardcoded "You died." message in chat (_Wuzzy_)
* Remove unsupported video drivers (_hecks_)
* Document hypertext formspec element escaping (_Wuzzy_)
* Drop --videomodes, fullscreen\_bpp and high\_precision\_fpu settings (_sfan5_)
* PostgreSQL fixes and improved error messages (_sfan5_)
* Improved liquid documentation (_Wuzzy_)
* Improved mipmapping-related code (_sfan5_)
* Rendering engine was changed from Irrlicht to [IrrlichtMt](/index.php?title=IrrlichtMt&action=edit&redlink=1 "IrrlichtMt (page does not exist)") (Minetest's fork of Irrlicht) (_sfan5_)
* Performance: Draw items as 2D images (instead of meshes) when possible (_sfan5_)
* Sanity check: Block & report player self-interaction (_appgurueu_)
* Multiple font code cleanups and improvements (_sfan5_)
* IrrlichtMt switch related fixups (_kilbith_. _sfan5_, _nerzhul_))
* Performance improvements during media/mesh loading (_sfan5_)
* Json is now taken from the system by default (_sfan5_)
* Various build bot and setup changes (_sfan5_)
* Restructured "/teleport" command (_HybridDog_)
* Consistent Aux1 key naming (_Wuzzy_)
* Many many internal cleanups and fixes (_sfan5_, others)

### Minetest Game

* Add “Read” and “Write” tabs to book interface when you own the book (_orbea_)
* Allow to write books without text or title (_orbea_)
* Make identical keys stackable (_Luis Royer_)
* Fix creative inventory trash slot not working for player named “trash” (_Montandalar_)
* Fix sunlight propagation for glass stair/slab (_An0n3m0us_)
* Fix glass bottle with firefly not being placable in vessels shelf (_An0n3m0us_)
* Other bugfixes
* Translations: Esperanto (_Jason Cartwright_), Russian (_ptah-alexs_), Japanese (_nogajun_), German (_Wuzzy_), Slovak (_Daretmavi_), French (_Olivier Dragon_), Swedish (_ROllerozxa_), Chinese (_雷哲翰_), Ukrainian (_baytuch_)

5.3.0 → 5.4.0
-------------

Released on 23 Feb 2021.

### Deprecations and compatibility notes

* Removed support for bumpmapping, generated normal maps, and parallax occlusion (_Lars_, _hecks_)
    * These features had fundamental issues, several bugs, and were broken on some platforms.
* Deprecated node field value: `use_texture_alpha = true/false`
    * Fix: Use `"clip"`, `"blend"` or `"opaque"` (see documentation)
* Deprecated `get_player_velocity` and `add_player_velocity` (_rubenwardy_)
    * Fix: replace with `get_velocity()` and `add_velocity()`
* Deprecated multiply and divide with two vectors (Schur product and quotient) (_DS_)
    * Fix: implement your own version
* By default, the crosshair will now change to an "X" when pointing to objects. If your game had a custom crosshair, this might come as a surprise and break graphical consistency.
    * Fix: Specify object\_crosshair.png image
* Added deprecation warning for node field: `alpha` (only limited compatibility provided)
    * This was already deprecated and undocumented.
    * Fix: Replace by `use_texture_alpha`
* Fixed deprecation warning when certain ores types ("sheet", "puff", "blob" and "vein") are missing noise\_params (_rubenwardy_)
    * These ore types require noise\_params. To keep the same behaviour, you can use the following values:

```
noise_params = {
    offset  = 0,
    scale   = 1,
    spread  = {x=250, y=250, z=250},
    seed    = 12345,
    octaves = 3,
    persist = 0.6,
    lacunarity = 2,
    flags = "defaults",
}

```


### Features

#### General

* Make 'place' and 'dig' keys freely configurable (only via minetest.conf for now: `keymap_place` and `keymap_dig`) (_ANAND_, _Markus Koch_)
* Freely bindable mouse buttons (only via minetest.conf for now: `KEY_LBUTTON`, `KEY_MBUTTON`, `KEY_RBUTTON`) (_ANAND_, _Markus Koch_)
* Add 'ores' global mapgen flag (_Paramat_)
* Mapgen Flat: Add caverns, disabled by default (_Paramat_)
* Semi-transparent background for nametags (_Zughy_, _rubenwardy_)
* Disable object selectionboxes by default (_LoneWolfHT_)
* Change crosshair when pointing to objects ("X" shape by default) (_LoneWolfHT_)
* Shaders for Android (GLES 2) (_Vitaliy_)
* Load media from subfolders (_DS_)
* Allow configuring block disk and net compression. Change default disk level. (_Lars_)

#### Main menu and ContentDB

* ContentDB: Add dependency resolution, update all, and download queues (_rubenwardy_)
* ContentDB: Add overwrite dialog when content is already installed (_rubenwardy_)
* ContentDB: Use icons for buttons (_Zughy_)
* Add open user data button to main menu (_rubenwardy_)
* Main menu: Add clear button and icon for search input (_Andrey_)
* Improve layout of main menu 'local' tab (_Paramat_)

#### Modding: GUI (Formspecs) / HUD

* Add sound effect style option (_Pierre-Yves Rollo_)
* Add 3d model formspec element (_Jean-Patrick Guerrero_, _SmallJoker_, _Thomas--S_)
* Add minimap and compass HUD elements (_Pierre-Yves Rollo_, _Jean-Patrick Guerrero_)
* Make bgcolor tint button background images (_Hugues Ross_)
* Add gradients and borders to FormSpec boxes (_v-rob_)
* Add font styling options (_v-rob_)
* Add set\_focus\[\] to initially focus elements (_v-rob_)
* Make dropdowns optionally return event based on index, not value (_v-rob_)
* Avoid drawing clipped out formspec elements (_EvidenceB_)
* Darken tabheader background color (_Kezi_)
* Add inventory list styling: spacing, slot size, and noclip (_v-rob_)
* Add support for custom object crosshair image: object\_crosshair.png (_LoneWolfHT_)

#### Modding: Other

* Add support for showing attached objects whilst in first person mode (_Jordach_)
* Add ability to cancel a minetest.after call after it was started (_tenplus1_)
* Add on\_rightclickplayer callback (_sorcerykid_)
* Add on\_deactivate callback for luaentities (_hecks_)
* Add minetest.get\_objects\_in\_area (_Elias Fleckenstein_)
* Add ObjectRef:get\_children() (_Zughy_)
* Add a short\_description to be used by mods (_DS_)
* Add minetest.get\_artificial\_light and minetest.get\_natural\_light (_HybridDog_)
* Add register\_on\_chatcommand to SSM and CSM (_Elijah Duffy_)
* Add vector.offset (_DS_)
* Register missing get\_texture\_mod function (_karamel59_)
* content\_cao: Support texture animation for upright\_sprite (_sfan5_)
* Add PUT and DELETE request + specific method value to HTTP API (_Lejo_)
* Nodes are now allowed to have the "liquid" or "flowingliquid" drawtype for non-liquids (liquidtype=none) (_Wuzzy_)
* Play 'place\_failed' sound if trying to place a node into an occupied space or it was an "attachable" node that failed to attach (_Wuzzy_)
* Implement grouped mode for find\_nodes\_in\_area (_sfan5_)
* Clean up sound\_fade (_hecks_)
* Chat commands: Show help message if func returns false without message (_HybridDog_)
* Node use\_texture\_alpha field supports now 3 modes "blend", "clip" and "opaque" (deprecated true/false values)

### Other enhancements and maintenance

* Cross-reference the node level manipulation functions (_Oblomov_)
* Update fallback fonts and mark additional locales as broken (_sfan5_)
* Clean up l\_object.cpp (_Zughy_)
* Devtest: Improve various things (_Paramat_, _HybridDog_, _Wuzzy_)
* Android: Add CI with saving artifacts (_Maksim_)
* Add NetBSD cpu affinity support code (_David CARLIER_)
* Android: drop simple MainMenu (_Maksim_)
* Add support for Haiku OS (_David CARLIER_)

### Bug fixes

#### Security

* Prevent players accessing inventories of other players (_Lars Müller_)
* Inventory: Protect Craft and Drop actions (_SmallJoker_)
* Prevent interacting with items out of the hotbar (_Lejo_)
* Fix inventory swapping not calling all callbacks (_Lars Müller_)
* Patch fast/teleport vulnerability when attached to an entity (_Elias Fleckenstein_)
* Prevent games from setting secure settings (_rubenwardy_)
* Prevent players from being able to modify ItemStack meta (_luk3yx_, _rubenwardy_)

#### Other

* Fix dropped craftitems/tools not using light\_source values (_LoneWolfHT_)
* Fix when on\_player\_hpchange is called (_SmallJoker_)
* Use JSON for favorites list, fixing many bugs (_rubenwardy_)
* Fix hypertext and textarea elementing consuming scroll events (_v-rob_)
* Fix ESC in error dialog from closing Minetest (_Yaman Qalieh_)
* Remove null bytes from TOCLIENT\_BLOCKDATA (_luk3yx_)
* Load system-wide texture packs too (_Zughy_)
* Fix Android support in bump version script (_rubenwardy_)
* ContentDB: Ignore content not installed from ContentDB (_rubenwardy_)
* Sanitize server IP field in mainmenu (_Zughy_)
* Fix item tooltip background color not working (_Lars Mueller_)
* Display Minetest header when menu\_last\_game value isn't available anymore (_Zughy_)
* Fix minetest.is\_nan (_Lars Mueller_)
* Fix some minor code issues all over the place (_sfan5_)
* Minor profiler fixes. (_Lars_)
* Fix fallnode rotation of wallmounted nodebox/mesh (_Wuzzy_)
* Make installer create its own Minetest folder (_LoneWolfHT_)
* Implement mapblock camera offset correctly (_hecks_)
* Fix MSAA stripes (_HybridDog_)
* Fix certain connected nodeboxes crashing when falling (_sfan5_)
* Avoid generating the same chunk more than once with multiple emerge threads. (_Lars_)
* Fixed various issues with stars, sky, and clouds (_numzero_)
* Fix falling image of torchlike if paramtype2="none" (_Wuzzy_)
* Fix player sprite visibility in first person (_sfan5_)
* Fix object interaction distance not being checked (_rubenwardy_)
* Block attempts to connect to the client (_red-001_)
* Fix segfault in deprecation logging due to tail call, log by default (_rubenwardy_, _SmallJoker_)
* Player physics: Ensure larger dtime simulation steps (_Lars Müller_)
* Avoid resending near blocks unnecessarily. (_Lars_)
* Fix CSMs on arm64 (_luk3yx_)
* Fix Media... 0% on loading screen (_Maksim_)
* Implement unloading of static\_save=false objects according to existing docs (_sfan5_)
* Decouple entity minimap markers from nametags replacing with show\_on\_minimap property (_sfan5_)
* Periodically release all mesh HW buffers to avoid an Irrlicht bottleneck. (_Lars_)
* Fix float argument check in minetest.set\_timeofday() (_Zughy_)
* Avoid drawing invisible blocks on the client. (_Lars_)
* Fix scroll bar overlapping text (again) (_random-geek_)
* Reduce the FPS when the window is unfocused (_HybridDog_)
* Android: replace InputDialogActivity on simple dialog window (_Maksim_)
* Correct erroneous reported max lag with prometheus (_Buckaroo Banzai_)
* Fix horizontal/vertical merging bug of hardware-colored framed glass (_Paramat_)
* Fix chat/infotext overlap if many chat lines (_Wuzzy_)
* Settings: Fix crash on exit (_SmallJoker_)
* Record player existence in dummy database. (_Lars_)
* Darwin platform build fix (_David CARLIER_)
* Scale inventory image for scaled allfaces nodes (_Wuzzy_)
* Fix NetBSD build (_David CARLIER_)
* shaders: Fix transparency on GC7000L (_mntmn_)
* Fix MSVC compiler warnings (_adrido_)
* Fix light overflow of u8 if light is saturated at 255 (_BenjaminRi_)
* Fix missing translation call in hypertext (_Pierre-Yves Rollo_)
* Render nodeboxes with opaque material if possible (_sfan5_)
* Fix precision not working in hud\_change (_Lars Müller_)
* Fix build for Visual Studio (explicitly cast pointers) (_Seeker_)
* Fix GCC class-memaccess warnings (_Paul Ouellette_)
* Falling: Fix error caused by missing param2 (_SmallJoker_)
* Allow starting local server using --go again (_SmallJoker_)
* decode\_base64: Allow '=' padding character (_SmallJoker_)
* Sanitize world directory names on create. Keep original name separate (_Hugues Ross_)
* Improve bad/missing default inventory+wield images of node drawtypes, affecting: airlike, signlike, torchlike, raillike, plantlike, plantlike\_rooted, firelike, flowingliquid (_Wuzzy_)
* Android: Fix ConfirmRegistration and PasswordChange input and scale size (_Maksim_)
* Formspecs: volume and key settings windows can now be closed by doubleclicking/tapping (_Zughy_)

### Minetest Game

* Add crafting guide (_Paul Ouellette_)
* Added 5 wood variants of Mese Post Light (_An0n3m0us_)
* Add environment sounds for lava and active furnace (_An0n3m0us_)
* Change several block sounds (_An0n3m0us_)
* Fix players sleeping in an occupied bed (_An0n3m0us_, _Wuzzy_)
* Fix 'sleepwalking' in bed (_An0n3m0us_, _Wuzzy_)
* Fix sleeping player flying off the bed when damaged and flying far away from the bed after death (_An0n3m0us_)
* Fix sleeping player being immobilized and bed undiggable after death (_An0n3m0us_)
* Fix furnace infotext not always updating when removing item (_orbea_)
* New translation: Slovak (_Daretmavi_)
* New translation: Brazilian Portuguese (_ronaldo_)
* New translation: Lojban (admittedly not a very good translation) (_robintown_, _Wuzzy_ and others)
* Update existing translations (various people)

5.2.0 → 5.3.0
-------------

Released on 9 July 2020.

### Modder Update Guide

* Lua API: `minetest.PLAYER_MAX_BREATH_DEFAULT` set to 10 (was 11). This can cause problems with “statbar” mods (like \[hudbars\]) that rely on the old value, so those likely need updating
* Default in Minetest Game was incorrectly overriding dropped items. Make sure to update any overrides to pass new arguments to on\_step to the original function

### Client / Audiovisuals

* Smoother camera movement to fix jump glitches (_paramat_)
* More precise player controls handling (_TheTermos_)
* Fix bone-attached entities (_hecktest_)
* Fix incorrect position data on attach (_hecktest_)
* Fix HUD scaling (mainly for Android) (_MoNTE48_)
* Fix incorrect entity light calculations (_SmallJoker_, _sfan5_)
* Add chat\_log\_level and chat\_font\_size setting (_SmallJoker_)
* New default sky color gradient (_TheTermos_)
* Change default keys for camera/minimap to C/V (_Wuzzy_)
* Fix breath bar scaling (_ANAND_)
* Fix bone position changes breaking animations (_theviper121_)
* No grey screen when C++ errors are thrown by Lua (_pauloue_)
* Android: add OpenGL ES 2 support (_MoNTE48_)
* Reuse object\_shader for "wielditem" and "item" entities (_dcbrwn_)
* Shaders: Fix OpenGL < 4.3 compatiblity (_SmallJoker_)
* Formspec: properly display altered inventory lists (_DS_)
* Android: Various input-related fixes (_MoNTE48_)
* Android: Android Studio support, improve everything (_MoNTE48_)
* Remove sound menu and show proper msgs if sound is off (_Wuzzy_)
* Highlight hovered formspec elements when pressing F5, for testing (_SmallJoker_)
* Implement DPI scaling for Windows (_sfan5_)
* Allow relative directories for \`screenshot\_path\` (_Calinou_)
* Add (optional) tone mapping for entities (_dcbrwn_)
* Add new mapgen options in world creation dialog (_Wuzzy_)
* Add support for overriding item inventory/wield images in texture packs (_Df458_)

### GUI (Formspec)

* Fix wrong image button scaling (_pyrollo_)
* Document `*_hovered` and `*_pressed styles` as deprecated (_v-rob_)
* Add buttons to ContentDB in game bar and configure world (_rubenwardy_)
* Add universal style selector “`*`” (_v-rob_)
* Add `content_offset` and `padding` style properties for buttons (_Df458_)
* Add `scroll_container` element (_DS_)
* CSS-like state-selection for style elements (_Df458_)

### World / Server / Environment

* Fix liquids refusing to flow in X+ or Z+ in some cases (_sfan5_)
* Rework functionality of leveled nodes (_Wuzzy_)
* New Mapgen V7 floatland implementation (_paramat_)
* Server: Better emerge multithreading, various fixes (_sfan5_)
* Correctly indicate failure in /spawnentity (_sfan5_)
* Add PostgreSQL authentication backend (_nerzhul_)
* Add chat command "/revokeme (priv)" (_Panquesito7_)
* Optimize get\_objects\_inside\_radius calls (_nerzhul_)
* Fix world migration to PostgreSQL (_sfan5_)
* Collision detection fixes and follow-up bug fixes (_TheTermos_)
* Many many networking improvements (_sfan5_)

### Script API / Modding

* Log warning when `secure.enable_security` is disabled (_rubenwardy_)
* Exposed zoom key to the API (_appgurueu_)
* Add LevelDB auth database (_luk3yx_)
* Add vector functions useful for working with rotations (_NetherEran_)
* Add `minetest.is_creative_enabled` (_Wuzzy_)
* Add `minetest.on_authplayer` callback (_sorcerykid_)
* HUD: Implement scalable texts (_LoneWolfHT_)
* HUD: "off state" icon feature for statbars (_Wuzzy_)
* `set_fov`: Add time-based transitions (_ANAND_)
* Expose collision information to LuaEntity `on_step` (_sfan5_)
* Enforced type checks for registration fields (_SmallJoker_)
* Add server side translations capability (_pyrollo_)
* Fix alias handling of `minetest.get_content_id` (_sfan5_)
* Document inheritance of different noise seeds (_paramat_)
* Add default stack size setting (_nephele_)
* Play `player_jump` sound when player jumps (_Wuzzy_)
* HUD: Better waypoints and new image variant (_appgurueu_)
* CSM: Implement `minetest.sound_fade()` (_sfan5_)
* Error on invalid mapgen alias (_Wuzzy_)
* Add `allowed_mapgens` option in `game.conf` (_wt_)
* Lua API documentation clarifications (_Wuzzy_)
* `minetest.PLAYER_MAX_BREATH_DEFAULT` set to 10 (was 11) (_ANAND_)

### Misc / Build

* Android: Hide media from galleries etc (_rubenwardy_)
* Minimal development test \[minimal\] renamed to “Development Test” \[devtest\] (_Wuzzy_)
* Complete overhaul of Development Test, many new features added for testing the engine, more documentation added in README files, etc. (_Wuzzy_)
* Particle & ParticleSpawner code cleanup (_sfan5_)
* Add Prometheus support (_nerzhul_)
* Fix detection of in-place path\_locale when RUN\_IN\_PLACE=0 (_sfan5_)
* List STATIC\_LOCALEDIR in "--version" (_sfan5_)
* Many code optimizations (_sfan5_)
* Wireshark dissector update (_sfan5_)
* Split and re-organize server object code (_nerzhul_)
* Automatic build improvements (_sfan5_, _nerzhul_)

### Minetest Game

* Rename “Dry Dirt” and related blocks to “Savanna Dirt” and similar (_paramat_)
* Added Wild Cotton: grows in savannas, drops Cotton Seeds (_paramat_)
* Sort items into correct categories (_An0n3m0us_)
* Tune cloud density variation (_paramat_)
* Fix broken Creative inventory search in translation (_sfan5_)
* Make Straw Stairs/Slabs usable as fuel (_Paul Ouellette_)
* New textures: Dry Shrub, Brake Rail (_Extex101_, _Hooded Ice_)
* Block particles when leaves decay, TNT explodes (_sfan5_)

5.1.0 → 5.2.0
-------------

Released on 5 April 2020.

### Client / Audiovisuals

* Fix alpha blending in texture modifiers (_Warr1024_)
* Make natural night light as bright as MT 0.4.16 (_paramat_)
* Shader fixes (_lhofhansl_, _SmallJoker_)
* Clean up font caching, fix bitmap fonts (_SmallJoker_)
* Waves generated with Perlin-type noise #8994 (_lhofhansl_)
* Attachments: Fix glitches after detach (_SmallJoker_)
* Let node 'place' and 'dug' sounds be heard by other players (_sfan5_)
* Fix weird looking liquid source (_Wuzzy_)
* Basic model shading (_dcbrwn_)
* Improve arm inertia animations (_kilbith_)

### GUI Improvements

* Add visual feedback for button states (_Df458_)
* Formspec: draw order and clipping for all elements (_DS_)
* Refactor internal button styling/rendering code (_Df458')_
* Formspec: Fix clicking on tooltip-obstructed elements (_DS_)
* Formspec: change cursor on fields and co. (_DS_)
* Various new formspec bug fixes (_SmallJoker_)
* Formspec: Add 9-slice background support to button elements (_Df458_)
* Formspec: add hypertext\[\] element (_pyrollo_)
* Formspec: animated\_image\[\] (_Df458_, _kilbith_)
* Make clipping of formspec elements more consistent (_Df458_)
* Remove outdated field\_close\_on\_enter\[\] warnings in element parameters (_SmallJoker_)
* Fix mouse events sent to wrong GUI elements when dragging (_sfan5_)
* Restore intuitive click-through behaviour (_DS_)

### Enhancements

* Wear out tools on punch (_sfan5_)
* Tunnels: Completely disable generation when 'cave width' >= 10.0 (_paramat_)
* Randomwalk cave liquids: Remove deprecated 'lava depth' (_paramat_)
* Automatically enable the mod's dependencies in the world config menu (_HybridDog_)
* Clean up craft replacements docs (_pauloue_)
* Falling nodes: add missing support for light sources, most drawtypes, and paramtype2s (_Wuzzy_)
* Remove legacy flat-file map code and documentation (_random-geek_)
* Fix packet receiving in server and client (_sfan5_)
* Key settings: Cancel with escape, clear with delete (_SmallJoker_)

### Script API / Modding

* CSM: Introduce get\_modpath() (_sfan5_)
* CSM: Remove non-functional minetest.get\_day\_count() (_sfan5_)
* Add z-index management to HUD (_pyrollo_)
* Add table.key\_value\_swap and table.shuffle (_HybridDog_)
* Map download: Escape ':' to '\_' (NTFS/FAT\* systems) (_Montandalar_)
* Settings: Add get\_flags API for mapgen flags (_SmallJoker_)
* Improve minetest.sound\_play with ephemeral sounds and player exclusion (_sfan5_)
* Reworked validity checks for entities (_sfan5_)
* Documentation: Add advice on lifetime of ObjectRefs (_sfan5_)
* Allow texture modifiers in hotbar textures (_Warr1024_)
* Nodes with torchlike drawtype and custom visual\_scale now are rendered attached to surface instead of being centered (_Wuzzy_)
* Add documentation of VoxelArea 'ystride', 'zstride' (_paramat_)
* Lua API: Document HP, breath and damage limits (_SmallJoker_)
* Various documentation improvements (_Wuzzy_)
* CSM: Corrections to client\_lua\_api.txt (_sfan5_)
* Make minetest.item\_place\_node return position of placed node (_Bluebird_)
* Call on\_secondary\_use when object is right-clicked (_sfan5_)
* CSM: Various fixes (_sfan5_)
* Many pathfinder bugfixes and improvements (_Wuzzy_)
    * Fix failure to find path if start or end pos is over air (_Wuzzy_)
    * Fix very broken implementation of A\* search (_Wuzzy_)
    * No longer jump through solid nodes (_Wuzzy_)
    * Return nil if start or end pos is solid (_Wuzzy_)
* New set\_sky, set\_sun, set\_moon and set\_stars (_Jordach_)
* Secure and document minetest.deserialize() (_luk3yx_)
* minetest.get\_content\_id: throw error for unknown nodes (_HybridDog_)

### Misc / Build

* Don't install fonts on ENABLE\_CLIENT=0 configurations (_sfan5_)
* Fix memleaks in formspecs (_SmallJoker_)
* Android: build fixes & compat fixes (_MoNTE48_, _nerzhul_)
* Run luacheck in travis, add luacheck (_rubenwardy_)
* Android: fix cyrillic characters (_Maksim_)
* Various build issue fixes (Clang, Travis CI) (_sfan5_)

### Minetest Game

* Simple weather that varies the clouds (_paramat_)
* More realistic boat physics (_gang65_)
* Creative Inventory search: Item with exact match appears in first spot (_sfan5_)
* Creative Inventory: More visual tweaks (_Andrey2470T_)
* Improve player model animation (_An0n3m0us_)
* Increase water opacity (_lhofhansl_)
* Reset spawn position when bed is destroyed (_Desour_)
* Papyrus now appears in rainforest swamps as well (_paramat_)
* New/updated translations:
    * French (_DrHackberrry_)
    * Spanish (_runsy_)
    * Italian (_h4ml3t_)
    * Russian (_Andrey2470T_)
    * Swedish (_Aresiel_)
    * Malay (_MuhdNurHidayat_)
    * Chinese (_zaoqi_, _IFRFSX_)
* Bugfix: TNT mod crashed when entities disappeared during explosion (_sfan5_)
* Bugfix: Papyrus in savanna did not appear in 5.1.0, it has been added back (_paramat_)
* Bugfix: Screwdriver was able to rotate torches into weird positions (_An0n3m0us_)
* Bugfix: Players could be knocked back when attached (_sfan5_)

5.1.0 → 5.1.1
-------------

Released on 17 January 2020.

This release is based upon bugfixes from 5.2.0-dev.

### Client / Audiovisuals

* Fix player-bound sound playback (_SmallJoker_)
* Fix item eat sound not played if last item (_Wuzzy_)

### World / Server / Environment

* Formspecs: Reset version number on rebuild (_SmallJoker_)
* Rework packet receiving in ServerThread (_sfan5_)
* Fix core.chat\_format\_message crashes (_ClobberXD_)
* Fix spaces breaking formspec\_version\[\] tag (_rubenwardy_)

### Misc / Build

* MacOS/BSD: Fix build issue due to conflicting s64 type definitions (_AMDmi3_)
* Fix find\_path for newer jsoncpp installations (**vilhelmgray**)
* Update translations

5.0.1 → 5.1.0
-------------

Released on 12 October 2019.

### Map generator

* Mapgen Carpathian: Add optional rivers (_paramat_)
* Move more dungeon parameter selection to mapgens (_paramat_)
* Dungeons: Make multiple large rooms possible (_paramat_)

### Client / Audiovisuals

* Change pitch fly binding to 'P', add to change keys menu (_rubenwardy_)
* Android settings: Use 'simple' leaves instead of 'fancy' (_paramat_)
* Fix 3rd person selection range (_srifqi_)
* Make scrollbars' bar variable in size (_stujones11_)
* Damage: Play no damage sound when immortal (_SmallJoker_)
* Increase upper limit of display\_gamma to 10 (_ClobberXD_)
* Optimize and unify mesh processing (_Vitaliy_)
* Re-order mapgens in mainmenu and 'all settings' mapgen selection (_paramat_)
* Scrollbars: Move directly to clicked pos if clicked into tray (_DS-Minetest_)
* Fix broken attachments on join (_SmallJoker_)
* Fix inventory\_overlay for nodes without inventory\_image (_DS-Minetest_)
* Better F6 profiler (_SmallJoker_)
* Fix minimap markers (_theviper121_)
* Textures: Load base pack only as last fallback (_SmallJoker_)

### Builtin (Lua / Media / Documentation)

* Add /help formspec for commands and privileges (_SmallJoker_)
* Lua API: Add link to Minetest Modding Book (_ClobberXD_)
* Force item entities out of solid nodes (_sfan5_, based on _Wuzzy_\`s work)
* Lua API: Various fixes (_DS-Minetest_, _SmallJoker_)
* Rename "private messages" to "direct messages" (_Calinou_)
* Automatically enable depending mods in the dialogue (_HybridDog_)
* All settings: Fix missing flags checkboxes (_srifqi_)

### World / Server / Environment

* Various network performance improvements (_osjc_)
* Force send a mapblock to a player (_sofar_)
* Revert ItemStacks being limited to the 'stack\_size' value (_ClobberXD_)
* Save forceloaded blocks file periodically (_Thomas Rudin_)
* Improve ABM time budget handling (_lhofhansl_)
* Group "immortal" also protects players from damage (_Wuzzy_)
* Optimize usage of TOSERVER\_GOTBLOCKS packet (_sfan5_)
* Network: several bugfixes (_sfan5_)
* Mapgen::spreadLight performance improvement (_DS-Minetest_)
* Improve occlusion culling in corridors with additional check (_sfan5_)
* Inventory: Delay dirty lists, and send changes incrementally (_SmallJoker_)
* Other inventory bugfixes (_sfan5_, _SmallJoker_)
* Move debug.txt after it grows too big (_HybridDog_)
* Trigger on\_place in many situations even if prediction failed (_DS-Minetest_)
* Punchwear (improved) (_sfan5_)

### Script API / Modding

* Add deprecation warnings for ObjectRef:get/set\_attribute (_ClobberXD_)
* Nodedef 'drop' documentation: Improve (_paramat_)
* Mark tool filtering in node drop documentation as deprecated (_paramat_)
* Add node field to PlayerHPChangeReason table (_pauloue_)
* Don't call on\_hpchange callbacks if HP hasn't changed (_ClobberXD_)
* Add disable\_jump to liquids and ladders (_SmallJoker_)
* Add support for 9-sliced backgrounds (_rubenwardy_)
* Add compatible, consistent coordinate system to FormSpecs (_v-rob_)
* Document ObjectRef:remove under Lua entity (_ClobberXD_)
* Docs: Clarify where to check for 'protection\_bypass' (_SmallJoker_)
* Add vector.dot and vector.cross (_HybridDog_)
* Improve documentation of mapgen aliases (_paramat_)
* Remove debug.upvaluejoin to prevent leak of insecure environment (_fluxionary_)
* Fix previously crashing minetest.get\_craft\_result() (_pauloue_)
* Allow toolcaps to override the built-in times for dig\_immediate (_sfan5_)
* Formspec styling using style\[\] (_rubenwardy_)
* Customizable chat message format (_ClobberXD_)
* Velocity modifiers for players (_sfan5_)
* Fix some issues with minetest.clear\_craft (_pauloue_)
* Add function \`minetest.read\_schematic\` (_paly2_)
* Formspecs: formspec\_version\[\] element (_SmallJoker_)
* Per-player FOV overrides and multipliers (_ClobberXD_)

### Misc / Build

* Find PostgreSQL correctly (_adrido_)
* Add compatibility to vcpkg buildsystem (_adrido_)
* Android: Use system provided path for default TMPFolder setting (_stujones11_)
* Fix handling of --color and --worldlist command line arguments (_mmattes_)
* Unified OpenGL ES support (_sfan5_)

### Minetest Game

* Added dry dirt and dry dirt with dry grass. Grass never spreads on dry dirt (_paramat_)
* Savannas now have dry dirt and dry dirt with dry grass (_paramat_)
* Added steel bar door and steel bar trap door
* Added setting “enable\_fence\_tall” for fences that cannot be jumped over (_mbartlett21_)
* Firefly in a bottle can now be placed into vessels shelf
* Add flowing water sound
* Underground biomes extend much deeper, down to Y=-255
* Make the creative mod hand dig 'dig\_immediate' nodes fast (_paramat_)
* Add new TNT sounds (_TumeniNodes_)
* Add missing infotext to nodes (_An0n3m0us_)
* Added translation support
* Added German, French, Spanish and Italian translations (_Wuzzy_, _Hamlet_, _JDiaz_, _DrHackberry_)

5.0.0 → 5.0.1
-------------

5.0.1 was released on March 31, 2019.

* Fix detached inventory serialisation (_rubenwardy_)
* Fix texture rotation for wallmounted nodeboxes (_sfan5_)
* Fix build failing on some compilers (_rubenwardy_)
* Warn about issues with the num\_emerge\_threads setting (_paramat_, _sofar_)
* HPChange Reason: Fix issues with custom reasons (_rubenwardy_)
* Fix FreeBSD build by handling std::time\_t properly (_rubenwardy_)
* Confirm registration GUI: Remove positional strings to fix Windows bug (_paramat_)
* Prevent multi-line chat messages server-side (_rubenwardy_)
* httpfetch: Disable IPv6 here too if requested by settings (_sfan5_)

0.4.16 → 5.0.0
--------------

Released March 4th

  
Note: 5.0.0 is based on 0.4.16, not 0.4.17. 0.4.17 was created by backporting changes from the development branch of 5.0.0

### Highlights

* Add online content repository (games, mods, modpacks, texture packs)
* Add Carpathian mapgen
* Automatic jumping
* Android: Rewritten controls. Add joystick and modify up on-screen buttons
* Mods and games can be translated
* Rename 'subgame' to 'game'
* Modding: More node drawtypes: disconnected nodeboxes (more ways to create connected blocks), `plantlike_rooted` (for underwater plants)
* Modding: Custom player collision box
* Modding: A great deal of new map generator features
* Modding: Allow to rotate entities in all 3 axes

### New Version Scheme

Basically, the leading 0 has been dropped. The [version scheme](https://wiki.minetest.net/Version_number) was thus changed from

```
ZERO.MAJOR.MINOR.PATCH

```


(note: PATCH was left out when it was 0) to

```
MAJOR.MINOR.PATCH

```


.

This was chosen for a few reasons:

* Shows that we aim to keep inter-version compatibility (which has mostly been the case since early 0.4.x)
* Allows us to release patch/bug fix only releases without adding a silly 4th number
* Doesn't imply that this version is the first stable/finished version as much as a 1.0.0 does.

For some context, read [the issue that resulted in this change](https://github.com/minetest/minetest/issues/6073).

### Breaking changes and deprecations

As a major release, 5.0.0 will break some mods written for 0.4.x versions. We tried to keep the breakages as small as possible whilst fixing long standing issues.

* Minetest now uses C++11 instead of C++03, make sure you have a compatible system (Windows Vista, Debian 8, Ubuntu 16.04, CentOS 7, macOS 10.7, …)
* Breaks network compatibility with 0.4.x. 0.4.x clients won't be able to connect to 5.x servers and vice-versa. Fix: update clients and servers to 5.x
* Attachment and player positions have been shifted by 1 node, to allow support for custom player selection boxes. Fix: update default and player\_api, subtract `10` from any attachment positions, shift the origin of player models to the feet
* Formspec theming using prepended strings. This may cause wrong backgrounds to appear on formspecs. Fix: see [https://forum.luanti.org/viewtopic.php?f=18&t=20646](https://forum.luanti.org/viewtopic.php?f=18&t=20646)
* depends.txt and description.txt have been deprecated. Fix: use _description_, _depends_, and _optional\_depends_ in mod.conf, game.conf, or texture\_pack.conf instead
* modpack.txt has been deprecated. Fix: rename to or add _modpack.conf_.
* Use of deprecated methods such as _object:setpos()_ is now warned about. Fix: [replace them with correct functions](https://forum.luanti.org/viewtopic.php?f=18&t=20403)
* _player:get/set\_attribute()_ is now deprecated. Fix: use _player:get\_meta()_ instead
* _nodeupdate()_ was removed. Fix: replace with _minetest.check\_for\_falling_.
* Clouds API: changed speed param from 'y' to 'z'
* Player inventory list "hand" must now be manually initialized by mods (using _set\_size_)
* Some client-side scripting functions were removed (see below)

Note that a function being _deprecated_ means that it still exists, but it may give a warning when used and may be removed in future. Deprecations are necessary to improve the consistency and efficiency of our API

### Features

#### Games

* Load a texture pack from the 'textures' subfolder of a game (_red-001_)

#### Map generators

* Mapgen: Add Carpathian mapgen (_Vaughan Lapsley_)
* Mapgen flags: Add 'biomes' global mapgen flag (_paramat_)
* Dungeons: Add Y limits in all mapgens (_paramat_)
* Dungeons: Add setting to prevent projecting dungeons (_paramat_)
* Biomes: Add vertical biome blend (_paramat_)
* Mgv7 floatlands: Add exponent parameter (_paramat_)

#### User interface

* Add online content repository (mods, texture packs, mod packs, games) (_rubenwardy_)
* Rename 'subgame' to 'game' (_paramat_)
* Allow enter to select items from combobox's list (_basicer_)
* Formspecs: Use mouse wheel to pick up and deposit single items (_HybridDog_)
* Add player marker to both minimap types (_nanoproject_)
* Delete world dialogue: Move buttons to avoid double click deletion (_srifqi_)
* Add a refresh button to the server list (_ThomasMonroe314_)
* Main menu: Change tabs to 'Start Game' and 'Join Game' (_ThomasMonroe314_)
* Add password confirmation on new player registration (_srifqi_)
* Adjust default console height (_Ezhh_)
* Add coloured terminal output (_HybridDog_)
* Add setting to display the itemstring after the tooltip in the inventory (_DTA7_)
* Make world creation menu automatically generate a random world name (_lisacvuk_)
* Change “Use” key name to “Special” (_TeTpaAka_)
* Make number of maximum displayed chat messages configurable (_Esteban_)

#### Controls

* Automatic jumping (_bendeutsch_)
* Add pitch move mode, toggle with L key
* Android: Rewritten controls. Add joystick and modify up on-screen buttons (_srifqi_)
* More keys are changable in settings menu
* Make direct item selection keys freely bindable via minetest.conf (_Wuzzy_)

#### World / server

* Add setting for world start time, and change default to 5:15am (_JRottm_, _paramat_)
* Allow for getting world name and path separately on the command line (_Brian_)
* Add a server-sided way to remove color codes from incoming chat messages (_red-001_)
* Object limits: Allow objects to exist outside the set 'mapgen limit' (_paramat_)

#### Chat commands and privileges

* Add '/haspriv' chat command (_ClobberXD_)
* Add '/kill' chat command (_Wuzzy_)
* Remove 'zoom' privilege (zoom is now a player object property)
* Do not grant all privileges to the admin - changes game behavior (_lhofhansl_)

#### Graphics

* Fog effect when camera is inside cloud (_bendeutsch_)
* Camera: Add and improve arm inertia (_kilbith_)
* Update light decoding table size (_numberZero_)
* New lighting curve (_numberZero_)
* Add setting for near plane distance (_basicer_)
* Add Android drivers to the video\_driver drop-down menu (_Wayward1_)

#### Sounds

* Sounds: Add falling node sounds (_sofar_)
* Emit liquid sound if the player walks in liquid (_juhdanad_)
* Play damage sound on player death (_paramat_)
* Add mute setting (toggled by the mute key and in the volume menu) (_DTA7_)

#### Technical

* Add support for authentication in an SQLite database (_bendeutsch_)
* Add an optional readonly base database (_lhofhansl_)
* Add crossview support (_otdav33_)
* Optionally extend the active object in a players camera direction (_lhofhansl_)
* Implement ability to set client node dig prediction result (_sofar_)

#### Misc.

* Add check to pause game on lost window focus (_rubenwardy_)
* Load files from subfolders in texture packs (_numberZero_)
* Make HUD status messages translatable (_Wuzzy_)

### Modding

* Add on\_mods\_loaded callback (_nerzhul_)
* MetaDataRef: Add contains() and get() (_rubenwardy_)
* Allow dumping userdata (_HybridDog_)
* Hint at problematic code when logging deprecated calls (_sfan5_)
* Add minetest.rgba function that returns ColorString from RGBA or RGB values (_Gael-de-Sailly_)
* World config: Add modpack descriptions (_HybridDog_)
* get\_node\_drops: Make empty drop return empty table (_tenplus1_)
* Add core.remove\_detached\_inventory (_SmallJoker_)
* Add disable\_repair group to prevent tool repair (_Wuzzy_)
* clear\_craft: Return false if recipe not found, don't throw error (_paramat_)
* Fix string.split returning an empty table if string starts with sepearator (_pyrollo_)

#### Formspecs / HUD

* Formspecs: Add tooltip element for area (_rubenwardy_)
* Formspecs: Allow setting alpha value for the box\[\] element (_Thomas--S_)
* Formspecs: Add an auto vertical scrollbar to the textarea (_adelcoding1_)
* Formspecs: Add options to set background color and opacity (fullscreen mode + default mode) (_nerzhul_)
* Formspecs: textarea with scrollbar improvements (_adrido_)
* HUD: Make hud\_get return alignment, offset and size. (_lisacvuk_)

#### Server-side

##### Metadata

* Give games the ability to disallow specific mapgens (_Ezhh_)
* Load mod dependencies and description from mod.conf (_rubenwardy_)

##### User interface

* Add clientside translations. (_Ekdohibs_)
* Add formspec theming using prepended strings (_rubenwardy_)
* Zoom: Set zoom FOV per-player using a player object property (_paramat_)
* Zoom: Move enabling zoom to a new player object property (_paramat_)
* Minimap: Add new HUD flag for minimap radar mode (_paramat_)

##### Items

* Allow overriding tool capabilities through itemstack metadata (_raymoo_)
* Set placer to nil instead of a non-functional one in item\_OnPlace (_DTA7_)
* Overlays for wield and inventory images (_juhdanad_)
* Make dropped items colorable (_juhdanad_)
* Automatic item and node colorization (_juhdanad_)
* Add eat sound (_Wuzzy_)

##### Nodes

* Add slippery group for nodes (players/items slide) (_Wuzzy_)
* Connected Nodeboxes: Add 'disconnected' boxes (_Thomas--S_)
* Add callback to preserve node metadata as item metadata (_ashtrayoz_)
* Add 'plantlike\_rooted' drawtype (_numberZero_)

##### Objects/entities

* ObjectRef: Add add\_velocity() (_HybridDog_)
* Allow damage for attached objects, add attach/detach callbacks (_SmallJoker_)
* Optional alpha channel support for entities (_stujones11_)
* Add static\_save property to luaentites to not save them statically. (_orwell96_)
* Object properties: Add 'glow', disables light's effect if negative (_basicer_)
* core.get\_objects\_inside\_radius: Omit removed objects (_HybridDog_)
* Make entity selection and collision boxes independently settable (_stujones11_)
* Add set\_rotation/get\_rotation to rotate entities in all 3 axes

##### Players

* Customizeable max health and max breath for players (not persisted between server restarts) (_SmallJoker_)
* Add reasons to on\_dieplayer and on\_hpchange (_rubenwardy_)
* Add minetest.is\_player (_HybridDog_)
* Add on\_grant and on\_revoke callbacks (_rubenwardy_)
* Player eye height: Make this a settable player object property (_paramat_)
* Step height: Add as a player object property (_paramat_)
* Player collisionbox: Make settable (_TeTpaAka_)
* Add player inventory callbacks (_SmallJoker_)

##### Mapgen

* Biomes: Add 'get\_biome\_name(biome\_id)' API (_paramat_)
* Biomes: Add 'min\_pos'/'max\_pos' xyz biome limits (_paramat_)
* Biomes: Add decoration flags for underground decorations (_paramat_)
* Biomes: Add function to deregister single biomes (_zeuner_)
* Biomes / dungeons: Add biome-defined dungeon nodes (_paramat_)
* Biomes / cavegen: Add definable cave liquid for a biome (_paramat_)
* Biomes: Add 'get heat', 'get humidity', 'get biome data' APIs (_paramat_)
* Biomes/decorations/ores: Make relative to 'water\_level' setting (_paramat_)
* Place schematic (on vmanip): Enable use of 'place center' flags (_paramat_)
* Ores: Add stratum ore (_paramat_)
* Stratum ore: Add option for a constant thickness stratum (_paramat_)
* Stratum ore: Allow use with no noise for simple horizontal strata (_paramat_)
* Simple decorations: Add 'param2\_max' parameter for random param2 (_paramat_)
* Schematic decorations: Add 'place\_offset\_y' placement parameter (_paramat_)
* Decoration API: Add lightweight ability to have complete coverage (_paramat_)
* Mgv6: Remove incorrectly defined and unused 'volume nodes' (_paramat_)
* Mgv7: Add 'mount\_zero\_level' parameter (_paramat_)
* Mgv7: Add option to repeat surface biomes in floatlands (_paramat_)
* Mgvalleys: Make river depth variation and humidity drop optional (_paramat_)
* CavesRandomWalk: Make 'lava\_depth' a mapgen parameter (_paramat_)
* Gennotify: Add 'minetest.get\_decoration\_id' API (_paramat_)

##### World

* Spawn level: Add 'get\_spawn\_level(x, z)' API (_paramat_)
* Add minetest.bulk\_set\_node call + optimize Environment::set\_node call (_nerzhul_)
* Implement minetest.register\_can\_bypass\_userlimit (_nerzhul_)

##### Chat

* Make the server status message customizable (_SmallJoker_)
* Allow the join/leave message to be overridden by mods. (_red-001_)

##### Protection

* is\_area\_protected: Rename from intersects\_protection (_SmallJoker_)
* Intersects\_protection(): Move from Minetest Game to builtin (_paramat_)

##### Graphics and sounds

* Real global textures (_numberZero_)
* Clouds API: change speed from 'y' to 'z', ColorSpecs in Lua docs (_bendeutsch_)
* In-cloud fog: Strengthen effect when small view range is used (_lhofhansl_)
* Sound: Add pitch option (_Rui-Minetest_)

##### Utility features

* Allow 'default' parameter in 'settings:get\_bool' function (_Jordan Irwin_)
* Add \`on\_auth\_fail\` callback (_red-001_)
* Make core.auth\_table private and structure builtin/auth.lua (_sfan5_)
* Add sha1 to lua utils. (_basicer_)
* Remove nodeupdate and nodeupdate\_single (_Rui-Minetest_)
* Expose getPointedThing to Lua (_juhdanad_)
* Helper methods for hardware colorization (_juhdanad_)
* httpfetch: Enable gzip support (_sfan5_)
* Rename hasprivs command to haspriv (_ezhh_)

#### Client-side

* Add flavour limits controlled by server (_nerzhul_)
* Disallow exploitable clientside mod functions by default (_paramat_)
* Rename CSM flavours to restrictions (_SmallJoker_)
* Remove screenshot API (_red-001_)
* Don't Load the package library (_red-001_)
* Remove \`on\_connect\` callback (_red-001_)
* Add functions to create particles and particlespawners. (_red-001_)
* Don't load the IO library. (_red-001_)
* Add a way to get current locale from CSM (_lisacvuk_)
* Add callback on open inventory (_Dumbledor_)
* Implement mod communication channels (_nerzhul_)
* Create a filesystem abstraction layer for CSM and only allow accessing files that are scanned into it. (_red-001_)
* Add function to get player privileges (_red-001_)

### Bug fixes and small improvements

Also a big thanks to paramat, ClobberXD, pauloue, gituser2194, lhofhansl, ashtrayoz, Wuzzy, and Ezhh for their contributions to documentation, in no particular order.

#### Critical

* Fix crash caused by Lua error during startup (_red-001_)
* Pointed\_thing\_to\_face\_pos: Avoid crash when player is inside a node (_paramat_)
* Fix segfault in player migration and crash in log\_deprecated (_SmallJoker_)
* Fix crash guiConfirmRegistration quit menu (_Vincent Glize_)
* Fix built-in inventory list crash when size = 0 (_SmallJoker_)
* Fix a crash or random memory leak when resetting saved environment variable in test\_servermodmanager.cpp (_nerzhul_)
* Fix crash on can\_bypass\_userlimit returning non-boolean (_rubenwardy_)
* Fix error if setting menu\_last\_game is not a valid game (_nOOb3167_)
* Builtin: Fix handle\_node\_drops crash with nil digger (_SmallJoker_)
* Fix issue Minetest crash when custom font path is not exist (_srifqi_)
* Thread: fix a crash on Windows due to data race condition on Thread::m\_start\_finished\_mutex (_nerzhul_)
* Fix crash on revocation of removed privilege (_rubenwardy_)
* Fix crash when using --go in command line (_juozaspo_)
* Fix crash due to missing pointer validation (_nerzhul_)
* Fix get\_server\_status() segfault due to uninitialized m\_env (_rubenwardy_)

#### Build

* Fix many Android build issues (_nerzhul_)
* Fix i386 bit build at OpenBSD (_mazocomp_)
* Fix compile error in OpenBSD (_jcalve_)
* Fix MSVC compiling annoyances (_adrido_)
* directiontables: Fix MSVC compiler error (_adrido_)
* Fix MacOS builds (_Pavel Puchkin_)
* Travis-ci build: fix osx jpeg installation failure, git ambiguous argument error (caused by merging commits) and add a workaround for travis commit range bug (_juozaspo_)

#### System-specific

* Provide Xorg/net wm process ID (_thoughtjigs_)
* Make os.tempfolder work correctly for MinGW & MSVC (_nOOb3167_)
* Print error when HOME is not set (_Midgard_)
* MacOS: don't require X11 libraries during compilation (_D Tim Cummings_)
* Prevent Android from automatically locking display (_Wayward1_)
* Windows: Cpack wix installer (_adrido_)

#### Rendering

* Fix liquid bottoms not being rendered (_numberZero_)
* Fix liquid post effect colour behaviour in third person view (_red-001_)
* Fix dark liquids (_numberZero_)
* Use crack animation on all tile layers (_juhdanad_)
* Smoothed yaw rotation for objects (_SmallJoker_)
* Disable shaders GUI on unsupported drivers (_numberZero_)
* Fix missing ignore textures (_HybridDog_)
* Make sure color returns to normal after a damage flash (_lhofhansl_)
* Camera: Improve subpixel movement (_SmallJoker_)
* Camera: Fix wieldmesh glitch after teleporting (_kilbith_)
* upright\_sprite: Fix texture position for players (_SmallJoker_)
* Fix node-nodebox lighting difference in direct sunlight (_numberZero_)
* Fix ambient occlusion and dark lines at mapblock borders (_numberZero_)
* Don't recalculate statustext initial color every time & review fixes (_nerzhul_)
* Clear colors when reading property info. Set vertex colors on upright\_sprites. (_basicer_)
* Fix items turning black (_numberZero_)
* Fix dropped item look (_HybridDog_)
* Fix item and wield meshes (_numberZero_)
* Do not scale texture unless necessary. (_lhofhansl_)
* Avoid filtering low-res textures for animated meshes (incl. players) (_lhofhansl_)
* Reduce server FOV with forward speed (_lhofhansl_)
* ParticleSpawner::step cleanup and rotation fix (_SmallJoker_)
* Fix incorrect buffer size calculation on creation of HUD status messages (_rubenwardy_)
* Particles: Do not add digging particles for airlike nodes (_SmallJoker_)
* Fix animation frame\_speed and blend loosing precision (_sapier_)
* Fix undefined behaviour in arm movement when dividing by zero (_nerzhul_)
* Fix render order of overlays (_juhdanad_)
* Particles: Make collision with objects optional (_paramat_)
* Fix stretched stars bug, change render order (_Aspen_)
* Software inventorycube (_Vitality_)
* Light curve: Simplify and improve code, fix darkened daytime sky (_Vitality_)
* Smooth lighting: Fix light leaking through edge-connected corners (_DTA7_)
* Darkness detection: Reduce chance of false positives darkening the skybox (_lhofhansl_)
* Fix sky objects not rendering with OpenGL ES (_stujones11_)
* Night clouds: Boost brightness for a moonlit appearence (_paramat_)
* Night sky: Fix brightness threshold for applying night colours (_paramat_)

#### User interface

* Fix debug and info text being the wrong color (_rubenwardy_)
* Fix tooltip colors specified by formspec part (_rubenwardy_)
* Make RTT display (F5 information) working correctly again (_HybridDog_)
* Don't show Android edit dialog when tapping read-only field (_srifqi_)
* Make sounds stop playing when entering game or mainmenu (_nOOb3167_)
* Fix dancing text for formspec input fields (_numberZero_)
* Chat: Remove prompt history duplicates (_SmallJoker_)
* Statbars: fix incorrect half-images in non-standard orientations (_Ekdohibs_)
* Advanced settings: Add range check for float type (_srifqi_)
* Move the nametag back to the top of the player (_TeTpaAka_)
* Chat: Move chat text down to not overlap 3rd line of debug text (_paramat_)
* Fix console resize issue when changed game window (_Ezhh_, _Zeno-_)
* Android buttons: Inset 'rare controls', inset and resize 'gear icon' (_paramat_)
* Main menu: Clean up and improve advanced settings dialogues (_SmallJoker_)
* Escape special characters when searching the server list (_ChimneySwift_)

#### Formspecs

* Mitigate formspec exploits by verifying that the formspec was shown to the user by the server. (_red-001_)
* Make container\[\] support fractional offsets (_SmallJoker_)
* Remove accidental empty 'quit' field (_SmallJoker_)
* Unify textarea and field parsing functions, fix wrong fallback text (_SmallJoker_)
* Formspec verification: Fix show\_formspec inside callbacks (_SmallJoker_
* Fix wrong scrolling of formspec input fields (_numberZero_)
* Inventory: Restrict access from too far away (_SmallJoker_)
* Fix mousewheel behaviour in textarea (_shivajiva101_)
* Fallback to 'label' in readonly textarea\[\] (backwards compatible) (_SmallJoker_)
* Fix invalid background warning (_SmallJoker_)
* Fix text clipped by scrollbars (_random-geek_)

#### Performance

* Optimized MapBlock mesh generation (_lhofhansl_)
* Optimize ABM checks (_lhofhansl_)
* Fix bugs in networking which caused a performance loss (_lhofhansl_)
* Builtin auth handler: Speed up file writing (_SmallJoker_)
* Huge LBM lookup performance improvement on mapblock loading (_nerzhul_)
* Fix last performance-type-promotion-in-math-fn problems (_nerzhul_)
* Optimize a little bit isBlockInSight, adjustDist & collisions (_nerzhul_)
* Line\_of\_sight: Improve using VoxelLineIterator (_juhdanad_)
* Cache server config settings. (_lhofhansl_)
* Very little performance fix on correctBlockNodeIds (_nerzhul_)
* Don't search for locale folders if gettext is disabled (_adrido_)

#### Networking

* Use server's zoom fov for distant world loading. (_lhofhansl_)
* Fix ipv6\_server=true not accepting IPv4 connections on Windows (_sfan5_)
* Fix narrow/utf8 difference in incoming/outcoming messages (_numberZero_)
* Fix day\_night\_ratio\_do\_override not being initialised server-side (_rubenwardy_)
* Fix attached particle spawners far from spawn (_raymoo_)
* Server: affect bind\_addr on constructor instead of start() (_nerzhul_)
* Network: Fix logging into older worlds with base64 hashes (_SmallJoker_)
* Server: Calculate maximal total block sends dynamically (_SmallJoker_)
* Have the server send the player list to the client (_red-001_)

#### Chat commands and privileges

* Check if player exists on use of /privs (_ClobberXD_)
* Reduce block load glitches (_lhofhansl_)
* Make the /shutdown command work properly (_dopik_, _SmallJoker_)
* Prevent /spawnentity from spawning unknown entity (_Wuzzy_)

#### World

* Fix blocks written by VManip not being marked as modified (_sfan5_)
* Set range of blocks to retrieve per roundtrip to 2. (_lhofhansl_)
* Retrieve a small cone of blocks in the direction of the players velocity. (_lhofhansl_)

#### Map generator

* Change mapgen order to ores > dungeons > decorations (_paramat_)
* Biome API: Fix absent water decorations and dust, in deep water (_paramat_)
* Biome-defined dungeon nodes: Use faster biome calculation (_paramat_)
* Biomemap: Avoid empty biomemap entry to fix failing biome dust (_paramat_)
* Biomes: Fix vertical biome blend (_paramat_)
* Biome dust node: Only place on 'walkable' cubic non-liquid drawtypes (_paramat_)
* Biome generation: Fix layers of 'filler' nodes at biome y limits (_paramat_)
* Mgv5: Make spawn position search more reliable (_paramat_)
* Mgv6 mudflow: Avoid partially removed stacked decorations (_paramat_)
* Mgv7: Raise spawn point by 1 node for no mountain case (_paramat_)
* Mgv7: Avoid rivergen removing mod-placed nodes when overgenerating (_paramat_)
* Mgv7: Avoid divide-by-zero errors (_paramat_)
* Mgv7: Fix undefined 'float\_mount\_height' (_paramat_)
* Mgfractal: Improve spawning behaviour (_paramat_)
* Mgv5/v7/fractal: Add 'large\_cave\_depth' parameter to replace fixed value (_paramat_)
* Fix Mapgen Valleys getSpawnLevelAtPoint() (_Treer_)
* Vein ore: Fix bug caused by changing perlinmap Y size (_paramat_)
* Schematic decorations: Fix placement bug when centered and rotated (_paramat_)
* Simple decorations: Make 'place\_offset\_y' usable with simple decorations (_paramat_)
* Dungeons: Fix duplication of y limit parameters (_paramat_)
* Dungeons: Mostly fix missing stair nodes (_paramat_)
* Dungeons: Avoid generation in multiple liquid nodes and 'airlike' (_paramat_)
* Dungeons: Use biome 'node\_stone' if normal stone types not detected (_paramat_)
* Cavegen: Fix errors when getting biome outside mapchunk (_paramat_)
* Cavegen: Re-order generation to fix cavern bug (_paramat_)
* Cavegen: Avoid unsupported biome 'top' or 'filler' nodes (_paramat_)
* valleys mapgen: Fixed submarine valleys shape (_Gael-de-Sailly_)
* settingtypes.txt: Fix valleys dungeon ymax error (_paramat_)
* L-system: Fix leaves cutting through stems (_HybridDog_)

#### Items and nodes

* Pointed thing to face pos: Use 'eye height' object property (_paramat_)
* Ensure no item stack is being held before crafting (_Luis Cáceres_)
* core.rotate\_node: Run callbacks like with any regular placed node (_SmallJoker_)
* Don't try to craft a non-existent item (_Esteban_)
* Fix rotated node placement (_tenplus1_)
* Item drop: Tune to land exactly 2 nodes away with level view (_paramat_)
* Check item\_drop amount clientside (_rubenwardy_)
* Fix Android node selection distance (_juhdanad_)
* Safe digging and placing (_bendeutsch_)
* Fix for empty key/value when reading item string with wear but no metadata (_Jesse McDonald_)
* Inventory: Fix wrong stack size behaviour and item loss (_SmallJoker_)

#### Objects/entities

* Fix objects colliding with their children (_SmallJoker_)
* core.spawn\_falling\_node: Keep metadata (_SmallJoker_)
* Collision engine: Collide with 'ignore' nodes (_paramat_)
* falling.lua: Delete falling node entities on contact with 'ignore' (_paramat_)
* Position entity nametags relative to selection-box (_stujones11_)
* Damage: Remove damage ignore timer (_SmallJoker_)
* Item entities: Enable item collision detection for sudden movement (_DTA7_)
* Ease selection of entities behind nodes (_SmallJoker_)
* Object properties: Fix loss of custom selectionbox when it's not updated (_SmallJoker_)
* GenericCAO: Fix light position for non-players, remove deprecated initialisation code (_SmallJoker_)
* GenericCAO: Fix dark model below y = 0 (_paramat_)
* CAO footstep sounds: Reduce gain to balance volume (_paramat_)

#### Players

* Make player liquid speed independent of FPS (_paramat_)
* Run detach callbacks on player leave (_SmallJoker_)
* Localplayer: Fix disable\_jump effect and getStandingNodePos() (_SmallJoker_)
* Android stepheight: Only increase if 'touching ground' (_paramat_)
* Respect object property hp\_max field for players (_SmallJoker_)
* Do not add base position to player selection box (_stujones11_)
* Abort if static\_spawnpoint is an invalid setting instead of just giving an error log (_HybridDog_)
* Fix error not printed to console when no name is provided (_juozaspo_)
* Fix player coordinate rounding in collisionMoveSimple() (_JRottm_)
* Sneak: Stripped down version (_SmallJoker_)
* (Re)spawn players within 'mapgen\_limit' (_paramat_)
* Stop autoforward on BACKWARD key-press (_tukkek_)
* Apply physics overrides correctly during anticheat calculations (_sfan5_)

#### Modding

* Fix builtin Lua function os.tempfolder (_nOOb3167_)
* Fix isNan check for object:set\_yaw(..) (_nerzhul_)
* Fix LuaJIT include directory not being found (_rubenwardy_)
* Check argument types inside MetaDataRef Lua API (_sfan5_)
* Fix buffer parameter not working in LuaPerlinNoiseMap::l\_getMapSlice() (_pgimeno_)
* Fix naming conventions of noise userdata (_rubenwardy_)
* Fix rounding error in g/set\_node caused by truncation to float (_rubenwardy_)
* Vector fun
* CAO footstep sounds: Reduce gain to balance volume (_paramat_)aramat_)_
* Fix default item callbacks to work with nil users (_raymoo_)
* on\_death: Fix callback number of pushed arguments (_SmallJoker_)
* Fix core.wrap\_text and make its behaviour consistent with the docs (_sfan5_)
* Trigger on\_rightclick regardless on the formspec meta field (_SmallJoker_)
* LBM: use range based for and fixed a loop variable overloading in applyLBMs (_nerzhul_)
* Fix deserialization of ItemDefinition (_Rui-Minetest_)
* Plantlike meshoptions: Fix inverted random vertical offset (_numberZero_)
* Player hand list: require init by mods (_SmallJoker_)

#### Debug

* Fix missing logs from warningstream (or similar) (_HybridDog_)
* Fix off-by-one in log output line length (_pgimeno_)
* Profiler: Fix var args not being passed to callback register function (_rubenwardy_)

#### Internal / code quality

* Add a MSVC / Windows compatible snprintf function (_nOOb3167_)
* Fix memory leaks in mod storage (_nerzhul_, _red-001_)
* Fix rtt >= 0.0f assertion and free\_move crash (_SmallJoker_)
* Global new() or grab() to be managed in constructor only (_JDCodeIt_)
* Node resolver: Make error on fallback optional, disable for mapgen aliases (_paramat_)
* FOV: Raise lower limit to avoid zoom-loading of distant world (_paramat_)
* Fix many issues reported by clang-tidy (_nerzhul_)
* Fix various clang-tidy reported performance-type-promotion-in-math-fn (_nerzhul_)
* Selected ItemStack: Reduce black magic and improve the stack swapping behavior (_SmallJoker_)
* core.rotate\_node: Do not trigger after\_place\_node (_SmallJoker_)
* Sound: fix static initialization order dependency by not having one (_nOOb3167_)
* Fix various Client class functions not marked as override (virtual) (_nerzhul_)
* Guard sound manager initialization with "enable\_sound" (_nOOb3167_)
* Fix an alone if to be with a missing else (_nerzhul_)
* Drop texture file list cache (_numberZero_)
* Variable name fix + structure creation unrolling in lighting code (_nerzhul_)
* getv3intfield: Fix logic of return bool (_paramat_)
* Generate Notifier: Clear events once after all 'on generated' functions (_paramat_)
* Fix Wstringop-overflow warning from util/srp.cpp (_HybridDog_)
* Tool getDigParams: Fix selecting the best fitting time (_HybridDog_)
* Fix undefined behaviour on getting pointer to data in empty vector (_nOOb3167_)
* Use Irrlicht's mesh cache for animated meshes. (_lhofhansl_)
* Shut down mapgen threads before other shutdown tasks (_raymoo_)
* Allow zoom to actually show more data. (_lhofhansl_)
* Make use of safe file writing in auth handler (_sfan5_)
* Fix inventory drag drop flag (_asl97_)
* Fix strict\_protocol\_version\_checking functionality after ee9a442 (_SmallJoker_)
* Fix empty legacy meta being persisted (_rubenwardy_)
* Lint fix on localplayer.h (_nerzhul_)
* Sort box corners correctly (_Thomas--S_)
* Remove unused Map::getDayNightDiff + fix one undefined variable in mapblock.cpp (_nerzhul_)
* Check node updates whether the blocks are known (_SmallJoker_)
* Really delete things in fs::RecursiveDelete (_Vitality_)
* Disable HW stereo for IrrLicht 1.9 (_numberZero_)

#### Misc.

* Fix for translating empty strings (_minduser00_)
* Positional sound: Limit volume when closer than 1 node (_paramat_)
* Change the server description after a search (_Dumbledor_)
* Fix no sound bug (_Rui-Minetest_)

### Other / Misc

* Version scheme change: 0.5.0 -> 5.0.0 (_nerzhul_)
* Move ASCII art to std::cerr, to remove it from logs (_rubenwardy_)
* PlayerSettings struct for player movement code (_bendeutsch_)
* Client eventmanager refactor (_nerzhul_)
* Update mesh collector and move it to a separate file (_numberZero_)
* Add Voxelarea unittests (_nerzhul_)
* VoxelArea: add\_{x,y,z,p} must be static (_nerzhul_)
* Cleanup in flat lighting (_numberZero_)
* Node definition manager refactor (_juhdanad_)
* Move 'setlocale' from Lua to C++. (_red-001_)
* Rewrite rendering engine (_numberZero_)
* Improve the path select GUI (_red-001_)

Older versions (pre-5.0.0)
--------------------------

If you want to see older versions (older than 5.0.0), please go to [this page](/OldChangelog "OldChangelog").