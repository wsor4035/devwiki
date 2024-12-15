---
title: Map generator features
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
  * ![image](/images/mapgen/1200px-Dungeon_0.4.7.jpg)
* Name: Desert stone dungeon
  * Blocks: Desert Stone, Desert Stone Stair, Air
  * Setting: mg_flags=dungeons
  * Default?: Yes
  * Description: Desert stone dungeons are similar to cobblestone dungeons, but they have larger rooms and longer stairways which also may go diagonally. They are made out of desert stone and their stairways made from desert stone stairs. These dungeons appear inside desert stone. In Minetest Game, desert dungeons can thus be found in deserts.
  * ![image](/images/mapgen/1200px-Desert_dungeon_desert_stone.jpg)
* Name: Sandstone dungeon
  * Blocks: Sandstone Brick, Sandstone Block Stair, Air
  * Setting: mg_flags=dungeons
  * Default?: No
  * Description: Sandstone dungeons are identical to desert stone dungeons in shape. They are made out of sandstone bricks and may have stairways made out of sandstone block stairs. These dungeons appear inside sandstone. In Minetest Game, sandstone dungeons can thus be found in sandstone deserts. In the v6 map generator, no sandstone dungeons are generated because of the lack of sandstone.
  * ![image](/images/mapgen/1200px-Desert_dungeon_sandstone.jpg)
* Name: Decorations
  * Blocks: (depends)
  * Setting: mg_flags=decorations
  * Default?: Yes
  * Description: Decorations are additional structures placed by mods on top of the surface. Decorations can be small plants such as grass, flowers, cacti, or they can even be entire trees or buildings.The v6 mapgen is an exception here, because regular trees, apple trees, jungle trees and pine trees and jungle grass are generated the map generator itself and are not considered decorations and are thus not affected by this setting. But mods can still add additional decorations on top of that. See also: Biomes#v6
  *
* Name: Caves
  * Blocks: Air
  * Setting: mg_flags=caves
  * Default?: Yes
  * Description: Caves are air pockets found underground at any height. Caves can be very small hollow places or can be very complex interconnected tunnel systems. Cave entrances can commonly found on the surface. The cave style greatly varies between the different map generators.
  * ![image](/images/mapgen/Minetest_Game_underground.jpg)
* Name: Underground lava lakes
  * Blocks: Lava, Ores, Air
  * Setting: mg_flags=caves
  * Default?: Yes
  * Description: These lakes are caverns flooded with lava. Ores are very common around these lakes (see screenshot). However, often these caverns are not linked to, and it is very difficult to reach them. Lava lakes are a subset of caves and only appear when caves are used. See Lava more more information.
  * ![image](/images/mapgen/1200px-Lava_lake_0.4.7.jpg)
* Name: Underground water lakes
  * Blocks: Water, Air
  * Setting: mg_flags=caves
  * Default?: Yes
  * Description: Like lava lakes, these lakes are caverns flooded with water and can appear at any height. Water lakes are a subset of caves and only appear when caves are used.
  * ![image](/images/mapgen/Underground_water_lake.jpg)


v7
--



* Name: Mountains
  * Setting: mgv7_spflags=mountains
  * Default?: Yes
  * Description: Enables mountains.
  *
* Name: Rivers
  * Setting: mgv7_spflags=ridges
  * Default?: Yes
  * Description: Enables rivers at sea level. They which aggressively cut through the terrain and sometimes create canyon-like structures. Since these rivers can make the terrain quite difficult to navigate, it may make sense to disable them.
  * ![image](/images/mapgen/Mapgen_v7_ridge.jpg)
* Name: Floatlands (experimental)
  * Setting: mgv7_spflags=floatlands
  * Default?: No
  * Description: With this setting, large chunks of land will be created in the sky at a height at Y=1280 or above. The terrain is a bit different than on the surface, but the biomes are more or less the same. This setting is experimental and subject to change. (Floatlands have been removed from Minetest 5.2 and will be added back in 5.3.)
  * ![image](/images/mapgen/Minetest_Game_floatland_coniferous_forest.jpg)
* Name: Caverns
  * Setting: mgv7_spflags=caverns
  * Default?: Yes
  * Description: This enables the creation of caves with very large rooms, also called caverns. There's typically no lava or water in or near them.
  *


v6
--

V6 features are configured via map generator flags with the setting `mgv6_spflags`.



* Name: Trees
  * Flags: trees
  * Default?: Yes
  * Description: Enables regular trees, apple trees, jungle trees and jungle grass in jungles and pine trees in taiga biomes.
  * ![image](/images/mapgen/Mapgen_v6_0_4_9.jpg)
* Name: Snow biomes
  * Flags: snowbiomes
  * Default?: Yes
  * Description: Enables the Tundra and Taiga biomes. This also automatically enables the jungles setting
  * ![image](/images/mapgen/1200px-Snow_pines.jpg)
* Name: Jungle biomes
  * Flags: jungles
  * Default?: Yes
  * Description: Adds the Jungle biome which includes jungle trees and jungle grass
  * ![image](/images/mapgen/1200px-Jungle_0.4.7.jpg)
* Name: Biome blending
  * Flags: biomeblend
  * Default?: Yes
  * Description: Enables a smooth transition between biomes.
  * ![image](/images/mapgen/Mapgen_v6_biomeblend.jpg)
* Name: Mud flow
  * Flags: mudflow
  * Default?: Yes
  * Description: The “mudflow” parameter adds soil erosion. It moves dirt that sits on the edge of vertical drops and moves it to the base of that drop.
  *
* Name: Flat
  * Flags: flat
  * Default?: No
  * Description: Will generate a flat world in the v6 style with lakes, trees and caves. Note that this is a bit different than the “flat” map generator
  *


flat
----

This mapgen has support for lakes and hills which are disabled by default.



* Name: Hills
  * Setting: mgflat_spflags=hills
  * Default?: No
  * Description: Increases the terrain height at some points to form hills. These hills become quite big sometimes.
  * ![image](/images/mapgen/Mapgen_flat_hills.jpg)
* Name: Lakes
  * Setting: mgflat_spflags=lakes
  * Default?: No
  * Description: Lowers the terrain at some points to form lakes. These lakes can become quite large sometimes.
  * ![image](/images/mapgen/Mapgen_flat_lakes.jpg)


See also
--------

*   [How to emulate mapgen v6 using a customised mapgen v7](/How_to_emulate_mapgen_v6_using_a_customised_mapgen_v7 "How to emulate mapgen v6 using a customised mapgen v7")