---
title: Map generator
aliases:
- "/Map_generator"
- "/Map-Database"
bookCollapseSection: true
---

# Map generator

The **map generator** (“mapgen” for short) is the [Luanti](https://wiki.luanti.org/Luanti "Luanti") component that generates the [map](https://wiki.luanti.org/Maps "Maps"). This page concentrates on terrain generation. For the biomes (block surface, vegetation and such), head over to [Biomes](https://wiki.luanti.org/Biomes "Biomes").

Introduction
------------

This complex program, integrated into the game, can generate procedurally the [map](https://wiki.luanti.org/Maps "Maps"), which is the world the player evolves in. It is based on Perlin noises, functions which allow associating to each point a random yet consistent value.

Generators
----------

There is a number of different map generators. It is possible to choose between them when creating a [map](https://wiki.luanti.org/Maps "Maps"). Some [mods](https://wiki.luanti.org/Mods "Mods") may change them radically, also all map generators allow for a lot of configuration in the advanced settings menu.

All map generators have biomes. In all map generators except v6 these biomes can be defined by [mods](https://wiki.luanti.org/Mods "Mods") using the Biome API. The v6 map generator is special because its biomes are completely predefined and can't be changed trivially.

**Important**: **v5 and v6 are not legacy map generators.** “v5”, “v6” and “v7” are names, not version numbers. _All_ mapgens included in Luanti are officially supported and updated.

### Overview

These are the available mapgens described in brief:

*   **v5**: Unrealistic yet interesting landscape with frequent floating blobs and extreme terrain overhangs, and deep oceans. The weirdness has an appeal to some
*   **v6**: Simple hills, cliffs and plateaus, rather flat and small-scale mapgen, no terrain overhangs, predefined biomes
*   **v7**: Very widespread landscape, tall mountains with overhanging terrain and far plains. Frequent large water canals at sea level
*   **carpathian**: Complex and realistic mountains with multiple variants, sometimes reaching extreme heights, separated by oceans and far-reaching low and mostly flat plains
*   **valleys**: Many hills, mountains and valleys containing [river water](https://wiki.luanti.org/River_Water "River Water") flowing downhill
*   **flat**: A perfectly flat world, but with caves, biomes and decorations
*   **fractal**: Map is based on a fractal of your choice; highly configurable
*   **singlenode**: Empty world

#### Gallery

Here are examples of landscapes generated with the different map generators (using [Minetest Game](https://wiki.luanti.org/Games/Minetest_Game "Games/Minetest Game")):

*   [![](/images/mapgen/Mapgen_v5.jpg)](/images/mapgen/Mapgen_v5.jpg)

    v5

*   [![](/images/mapgen/Mapgen_v6.jpg)](/images/mapgen/Mapgen_v6.jpg)

    v6

*   [![](/images/mapgen/Mapgen_v7.jpg)](/images/mapgen/Mapgen_v7.jpg)

    v7

*   [![](/images/mapgen/Mapgen_carpathian.jpg)](/images/mapgen/Mapgen_carpathian.jpg)

    carpathian

*   [![](/images/mapgen/Mapgen_valleys.jpg)](/images/mapgen/Mapgen_valleys.jpg)

    valleys

*   [![](/images/mapgen/Mapgen_flat.jpg)](/images/mapgen/Mapgen_flat.jpg)

    flat

*   [![](/images/mapgen/Mapgen_fractals_fractal_1.jpg)](/images/mapgen/Mapgen_fractals_fractal_1.jpg)

    fractal

*   [![](/images/mapgen/Mapgen_singlenode.jpg)](/images/mapgen/Mapgen_singlenode.jpg)

    singlenode


### Description

All map generators described in full detail.

To learn more about detailed configuration, see [Map generator features](https://wiki.luanti.org/Map_generator_features "Map generator features"). To learn more about the history of the map generators, see [Map Generator Evolution](https://wiki.luanti.org/Map_Generator_Evolution "Map Generator Evolution").

#### v5

Notable for its unique and somewhat strange terrain shape and occasional floating islands which often look like blobs. Extreme overhanging terrain is not uncommon and the landscape is sometimes realistic, sometimes strange and challenging. The oceans can sometimes reach extreme depths as well. While the landscape is not exactly realistic, this mapgen is intentionally included in Luanti because its uniqueness and weirdness also has a special appeal to some.

Like most map generators, v5 generates many caves in the underground. The caves are often tight but may be broad at times. They can sometimes be very long, deep and tricky to explore and form a complex tunnel system. Deep in the underground, there is a low chance to encounter giant caves. Like in most other mapgens, [lava](https://wiki.luanti.org/Lava "Lava") and [water](https://wiki.luanti.org/Water "Water") lakes may appear as lakes in the underground, but lava starts to appear very deep at Y=-273 or below.

The biomes have to defined by [mods](https://wiki.luanti.org/Mods "Mods") first, otherwise it will be a [stone](https://wiki.luanti.org/Stone "Stone")\-only landscape. The same is true for all other mapgens except v6.

Landscapes are based on 3D Perlin noise.

#### v6

Notable for rather flat and simple hills and cliffs. The landscape is rather simple, the hills don't extend above Y=47 and there are no natural terrain overhangs (ignoring caves). The weirdness of v5 is eliminated.

The caves are simple, short and tight and have little variation, but they are frequent. Larger caves only generate for underground water and lava lakes. There are no giant caves. This is the only map generator in which [lava](https://wiki.luanti.org/Lava "Lava") is already generated below Y=-32, much higher than in the other mapgens.

This is the only map generator with predefined biomes: Grassland, forest, jungle, desert, taiga, tundra. Four species of [trees](https://wiki.luanti.org/Trees "Trees") are generated: Regular tree, apple tree, jungle tree and pine tree. The biomes can't be modified by mods. Because of the nature of v6, the biomes are much simpler than in the other map generators, and a couple of blocks found in the other map generators can't be found in v6 maps (for example: [Silver Sand](https://wiki.luanti.org/Silver_Sand "Silver Sand"), [Acacia Tree](https://wiki.luanti.org/Acacia_Tree "Acacia Tree"), [Orange Coral](https://wiki.luanti.org/Coral "Coral")).

Other unique features include: Large patches of dirt and sand in the underground, rare gravel fields on the surface and a setting to generate a flat map in v6 style.

Generated entirely using 2D Perlin noise.

v6 mapgen is officially stable.[\[1\]](#cite_note-stability-1)

#### v7

Generates a very large-scale environment with large biomes and plains. One of the most unique features in this map generator are the broad and deep water canals (called “ridges”) at sea level, but they can be disabled. Like in v5, the biome have to be defined by mods first. This mapgen also has the unique feature of supporting floating islands high in the sky (→[Map generator features](https://wiki.luanti.org/Map_generator_features "Map generator features")), but they are disabled by default.

The generated caves are broad, often have lots of space and are often very long and complex and like to branch off. Sudden drops are not unusual. Deep in the underground, giant caves may form (like in v5).

Uses 2D and 3D Perlin noise. It mapgen the default selection since version 0.4.15.

v7 mapgen is officially stable, with the exception of floatlands.[\[1\]](#cite_note-stability-1)

#### carpathian

Vast and relatively flat plains, rolling hills and complex, realistic mountain ranges dominate the landscape. Mountains come in several forms. In mountain ranges, ridges and terraced mountains can form. Rarely there are extremely big mountains and rarely there are fjords.

#### valleys

Generates a landscape featuring many hills, mountains and valleys. The valleys often contain rivers with [river water](https://wiki.luanti.org/River_Water "River Water"). The rivers are very different than in v7, since they are not at ocean level and actually flow downhill. Another unique feature of this mapgen is the altitude chill. The biome temperature falls with the height which means that at high elevations, cold biomes are much more likely.

The caves are similar to those of v7, but they tend to be much larger on average.

#### flat

Generates a perfectly flat world (ignoring structures and caves) with biomes. It can be configured to add occasional hills and lakes.

The generated caves are practically identical to those of v7.

#### fractal

Generates a map based on a fractal. It creates by far the weirdest terrain shapes, but its results are mostly predictable.

By default, a map based on the Mandelbrot set is generated. It is possible to choose one of many fractals which are based on the Mandelbrot and Julia set, which is chosen in the advanced settings menu (technical setting name “`mgfractal_fractal`”). Changing this setting will yield wildly different results; if you want to make most of this mapgen, make sure to play around with the advanced settings a bit.

The generated caves are practically identical to those of v7.

#### singlenode

Generates an empty world.

To be precise: By default, this produces a world with only [air](https://wiki.luanti.org/Air "Air") everywhere. For games it is possible to replace the air with a different block.

It is intended to be used for mapgen mods which define their own map generation from scratch. This mapgen is not really usable if left unmodified because it is impossible to place blocks in mid-air without the use of mods.

Singlenode mapgen is officially stable.[\[1\]](#cite_note-stability-1)

See also
--------

*   [Map generator/settings](https://wiki.luanti.org/Map_generator/settings "Map generator/settings")
*   [Map generator features](https://wiki.luanti.org/Map_generator_features "Map generator features")
*   [Biomes](https://wiki.luanti.org/Biomes "Biomes")
*   [Map Generator Evolution](https://wiki.luanti.org/Map_Generator_Evolution "Map Generator Evolution")

References
----------

1.  ↑ [1.0](#cite_ref-stability_1-0) [1.1](#cite_ref-stability_1-1) [1.2](#cite_ref-stability_1-2) [Stability of each mapgen](https://forum.minetest.net/viewtopic.php?f=18&t=19132)