---
aliases:
- "/Map_generator_features"
---

# Map generator features

This article shows the various special features which [map generators](/Mapgen "Map generator") have and explains how to use them.

Shared features
---------------

These map generator features are shared by multiple map generators: v5, v6, v7, valleys, flat and fractal. All of these are enabled by default.



* Name: Cobblestone dungeon
  * Blocks: Cobblestone, Mossy Cobblestone, Cobblestone Stair, Air
  * Setting: mg_flags=dungeons
  * Default?: Yes
  * Description: Dungeons are hollow underground structures made of a mixture of cobblestone and mossy cobblestone. Many pathways and cobblestone stairs connect a complex system of rooms.
  * Images: Cobblestone dungeon, as of 0.4.7
* Name: Desert stone dungeon
  * Blocks: Desert Stone, Desert Stone Stair, Air
  * Setting: mg_flags=dungeons
  * Default?: Yes
  * Description: Desert stone dungeons are similar to cobblestone dungeons, but they have larger rooms and longer stairways which also may go diagonally. They are made out of desert stone and their stairways made from desert stone stairs. These dungeons appear inside desert stone. In Minetest Game, desert dungeons can thus be found in deserts.
  * Images: Desert stone dungeon, as of 0.4.13
* Name: Sandstone dungeon
  * Blocks: Sandstone Brick, Sandstone Block Stair, Air
  * Setting: mg_flags=dungeons
  * Default?: No
  * Description: Sandstone dungeons are identical to desert stone dungeons in shape. They are made out of sandstone bricks and may have stairways made out of sandstone block stairs. These dungeons appear inside sandstone. In Minetest Game, sandstone dungeons can thus be found in sandstone deserts. In the v6 map generator, no sandstone dungeons are generated because of the lack of sandstone.
  * Images: Sandstone dungeon, as of 0.4.13
* Name: Decorations
  * Blocks: (depends)
  * Setting: mg_flags=decorations
  * Default?: Yes
  * Description: Decorations are additional structures placed by mods on top of the surface. Decorations can be small plants such as grass, flowers, cacti, or they can even be entire trees or buildings.The v6 mapgen is an exception here, because regular trees, apple trees, jungle trees and pine trees and jungle grass are generated the map generator itself and are not considered decorations and are thus not affected by this setting. But mods can still add additional decorations on top of that. See also: Biomes#v6
  * Images: 
* Name: Caves
  * Blocks: Air
  * Setting: mg_flags=caves
  * Default?: Yes
  * Description: Caves are air pockets found underground at any height. Caves can be very small hollow places or can be very complex interconnected tunnel systems. Cave entrances can commonly found on the surface. The cave style greatly varies between the different map generators.
  * Images: Cave in Minetest Game 5.0.0
* Name: Underground lava lakes
  * Blocks: Lava, Ores, Air
  * Setting: mg_flags=caves
  * Default?: Yes
  * Description: These lakes are caverns flooded with lava. Ores are very common around these lakes (see screenshot). However, often these caverns are not linked to, and it is very difficult to reach them. Lava lakes are a subset of caves and only appear when caves are used. See Lava more more information.
  * Images: A lava lake in v6, as of Minetest 0.4.7
* Name: Underground water lakes
  * Blocks: Water, Air
  * Setting: mg_flags=caves
  * Default?: Yes
  * Description: Like lava lakes, these lakes are caverns flooded with water and can appear at any height. Water lakes are a subset of caves and only appear when caves are used.
  * Images: A water lake in v7, as of Minetest 0.4.15


v7
--



* Name: Mountains
  * Setting: mgv7_spflags=mountains
  * Default?: Yes
  * Description: Enables mountains.
  * Images: 
* Name: Rivers
  * Setting: mgv7_spflags=ridges
  * Default?: Yes
  * Description: Enables rivers at sea level. They which aggressively cut through the terrain and sometimes create canyon-like structures. Since these rivers can make the terrain quite difficult to navigate, it may make sense to disable them.
  * Images: Typical ridge in v7, Minetest Game
* Name: Floatlands (experimental)
  * Setting: mgv7_spflags=floatlands
  * Default?: No
  * Description: With this setting, large chunks of land will be created in the sky at a height at Y=1280 or above. The terrain is a bit different than on the surface, but the biomes are more or less the same. This setting is experimental and subject to change. (Floatlands have been removed from Minetest 5.2 and will be added back in 5.3.)
  * Images: Minetest Game floatlands in 5.0.0
* Name: Caverns
  * Setting: mgv7_spflags=caverns
  * Default?: Yes
  * Description: This enables the creation of caves with very large rooms, also called caverns. There's typically no lava or water in or near them.
  * Images: 


v6
--

V6 features are configured via map generator flags with the setting `mgv6_spflags`.



* Name: Trees
  * Flags: trees
  * Default?: Yes
  * Description: Enables regular trees, apple trees, jungle trees and jungle grass in jungles and pine trees in taiga biomes.
  * Images: A forest of regular trees in 0.4.9
* Name: Snow biomes
  * Flags: snowbiomes
  * Default?: Yes
  * Description: Enables the Tundra and Taiga biomes. This also automatically enables the jungles setting
  * Images: Pine trees in a snowy region, as of 0.4.13
* Name: Jungle biomes
  * Flags: jungles
  * Default?: Yes
  * Description: Adds the Jungle biome which includes jungle trees and jungle grass
  * Images: Jungle biome as of 0.4.7
* Name: Biome blending
  * Flags: biomeblend
  * Default?: Yes
  * Description: Enables a smooth transition between biomes.
  * Images: Biome blending in action between plains and a desert
* Name: Mud flow
  * Flags: mudflow
  * Default?: Yes
  * Description: The “mudflow” parameter adds soil erosion. It moves dirt that sits on the edge of vertical drops and moves it to the base of that drop.
  * Images: 
* Name: Flat
  * Flags: flat
  * Default?: No
  * Description: Will generate a flat world in the v6 style with lakes, trees and caves. Note that this is a bit different than the “flat” map generator
  * Images: 


flat
----

This mapgen has support for lakes and hills which are disabled by default.



* Name: Hills
  * Setting: mgflat_spflags=hills
  * Default?: No
  * Description: Increases the terrain height at some points to form hills. These hills become quite big sometimes.
  * Images: Hill in the flat mapgen
* Name: Lakes
  * Setting: mgflat_spflags=lakes
  * Default?: No
  * Description: Lowers the terrain at some points to form lakes. These lakes can become quite large sometimes.
  * Images: Small lake in the flat mapgen


See also
--------

*   [How to emulate mapgen v6 using a customised mapgen v7](https://wiki.luanti.org/How_to_emulate_mapgen_v6_using_a_customised_mapgen_v7 "How to emulate mapgen v6 using a customised mapgen v7")