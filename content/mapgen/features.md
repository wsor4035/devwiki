---
title: Map generator features
aliases:
- "/Map_generator_features"
---

# Map generator features

This page shows the various special features which [map generators](/mapgen "Map generator") have and explains how to use them.

{{< notice note >}}
This page doesn't list all available mapgen features. For a full reference, search for `mg_flags` and `mg*_spflags` in [minetest.conf.example](https://github.com/minetest/minetest/blob/master/minetest.conf.example) instead.
{{< /notice >}}

## Features shared between all mapgens except singlenode

### Dungeons

Setting `mg_flags`, `dungeons` flag (enabled by default)

* Dungeons are hollow underground structures. Many pathways and stairs connect a complex system of rooms.
* The nodes used by dungeons are defined in biome definitions.
* Screenshot of a cobblestone dungeon in Minetest Game:  
  ![](/images/mapgen/1200px-Dungeon_0.4.7.jpg)

### Decorations

Setting `mg_flags`, `decorations` flag (enabled by default)

* Decorations are additional structures placed on top of the surface. These are registered by games and mods using the decoration API.
* Decorations can be small plants such as grass, flowers, cacti, or they can even be entire trees or buildings.
* This flag doesn't affect mapgen v6 trees (see [Mapgen v6](/mapgen/#v6)).

### Caves

Setting `mg_flags`, `caves` flag (enabled by default)

* Caves are air pockets found underground at any height. Caves can be very small hollow places or can be very complex interconnected tunnel systems. Cave entrances can commonly found on the surface. The cave style greatly varies between the different map generators.
* There is a "cave liquids" system that results in some caves being flooded. Biome definitions can specify the liquid nodes to be used.
* Screenshot of a cave in Minetest Game:  
  ![](/images/mapgen/Minetest_Game_underground.jpg)
* Screenshot of a cave flooded with water in Minetest Game:  
  ![](/images/mapgen/Underground_water_lake.jpg)
* Screenshot of a cave flooded with lava in Minetest Game:  
  ![](/images/mapgen/1200px-Lava_lake_0.4.7.jpg)

## Features shared between fewer mapgens

### Caverns

This enables the creation of caves with very large rooms, also called caverns.

Caverns depend on caves being enabled. Caverns are shared between:

* v5: Setting `mgv5_spflags`, `caverns` flag (enabled by default)
* v7: Setting `mgv7_spflags`, `caverns` flag (enabled by default)
* carpathian: Setting `mgcarpathian_spflags`, `caverns` flag (enabled by default)
* flat: Setting `mgflat_spflags`, `caverns` flag (disabled by default)
* valleys: Always enabled

## Mapgen `v7` features

### Mountains

Setting `mgv7_spflags`, `mountains` flag (enabled by default)

### Rivers

Setting `mgv7_spflags`, `ridges` flag (enabled by default)

* Enables rivers at sea level. They aggressively cut through the terrain and sometimes create canyon-like structures. Since these rivers can make the terrain quite difficult to navigate, it can be useful to disable them.
* Screenshot of a river in Minetest Game:  
  ![](/images/mapgen/Mapgen_v7_ridge.jpg)

### Floatlands (experimental)

Setting `mgv7_spflags`, `floatlands` flag (disabled by default)

* Floatlands are large chunks of land generated in the sky, by default from Y=1024 to Y=4096. They are experimental and subject to change.
* For more information, see the ["Warning: Rewrite of Mapgen V7 floatlands"](https://forum.luanti.org/viewtopic.php?f=18&t=23764) forum thread by paramat.
* Screenshot of floatlands in Minetest Game:  
  ![](/images/mapgen/Minetest_Game_floatland_coniferous_forest.jpg)


## Mapgen `v6` features

### Trees

Setting `mgv6_spflags`, `trees` flag (enabled by default)

* Enables v6's hardcoded decorations: regular trees, apple trees, jungle trees and jungle grass in jungles and pine trees in taiga biomes (see [Mapgen v6](/mapgen/#v6)). 
* Screenshot of v6 trees in Minetest Game:  
  ![](/images/mapgen/Mapgen_v6_0_4_9.jpg)

### Snow biomes

Setting `mgv6_spflags`, `snowbiomes` flag (enabled by default)

* Enables the Tundra and Taiga biomes. This also automatically enables the jungles setting.
* Screenshot of v6 snow biome in Minetest Game:  
  ![](/images/mapgen/1200px-Snow_pines.jpg)

### Jungle biomes

Setting `mgv6_spflags`, `jungles` flag (enabled by default)

* Enables the Jungle biome which includes jungle trees and jungle grass.
* Screenshot of v6 jungle biome in Minetest Game:  
  ![](/images/mapgen/1200px-Jungle_0.4.7.jpg)

### Biome blending

Setting `mgv6_spflags`, `biomeblend` flag (enabled by default)

* Enables a smooth transition between biomes.
* Screenshot of a v6 biome transition in Minetest Game:  
  ![](/images/mapgen/Mapgen_v6_biomeblend.jpg)

### Mud flow

Setting `mgv6_spflags`, `mudflow` flag (enabled by default)

* Enables soil erosion. It moves dirt that sits on the edge of vertical drops and moves it to the base of that drop.

### Flat

Setting `mgv6_spflags`, `flat` flag (disabled by default)

* Will generate a flat world in the v6 style with lakes, trees and caves. You should prefer using the `flat` map generator instead.

### Temples

Setting `mgv6_spflags`, `temples` flag (enabled by default)

* Enables generation of larger dungeons called desert temples in v6 desert biomes.
* If disabled, normal dungeons are generated instead.
* Screenshot of a desert temple in Minetest Game:  
  ![](/images/mapgen/1200px-Desert_dungeon_desert_stone.jpg)

## Mapgen `flat` features

This mapgen has support for lakes and hills which are disabled by default.

### Hills

Setting `mgflat_spflags`, `hills` flag (disabled by default)

* Increases the terrain height at some points to form hills. These hills become quite big sometimes.
* Screenshot of a hill in Minetest Game:  
  ![](/images/mapgen/Mapgen_flat_hills.jpg)

### Lakes

Setting `mgflat_spflags`, `lakes` flag (disabled by default)

* Lowers the terrain at some points to form lakes. These lakes can become quite large sometimes.
* Screenshot of a lake in Minetest Game:  
  ![image](/images/mapgen/Mapgen_flat_lakes.jpg)
