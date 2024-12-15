---
title: Mapgen Parameters
aliases:
- /Mapgen_Parameters
---

# Mapgen Parameters
All map generator algorithms have a few common parameters, plus any mapgen-specific options such as noise parameters or threshhold values.

Mapgen parameter source precedence
----------------------------------

There are several sources which the map generator may retrieve parameters from. In order from highest precedence to lowest they are:

* Hard-coded
* Lua mods
* map\_meta.txt
* Game-specific config file
* Global config file
* Default settings (set in defaultsettings.cpp)
* Default object constructor values

List of mapgen parameters
-------------------------

Mapgen name
-----------

The name of the map generator algorithm being used. Currently supported:



* Mapgen name: v5
  * Developer responsible: missing info
  * Description: Description needed
* Mapgen name: v6
  * Developer responsible: kwolekr, celeron55
  * Description: The current default map generator.  Uses an improved Mapgen v2 algorithm for base terrain; terrain is generated entirely using 2D Perlin noise.
* Mapgen name: v7
  * Developer responsible: kwolekr
  * Description: The next generation map generator with an emphasis on generating interesting and playable terrain.  Has full support for the internal biome infrastructure and uses a mixture of 2D and both positive and negative 3D noise for terrain.
* Mapgen name: valleys
  * Developer responsible: missing info
  * Description: Description needed
* Mapgen name: carpathian
  * Developer responsible: missing info
  * Description: Description needed
* Mapgen name: fractal
  * Developer responsible: missing info
  * Description: Generates maps based on Mandelbrot fractal series
* Mapgen name: flat
  * Developer responsible: missing info
  * Description: Generates completely flat world. Replaces the flat flag in mg_flags. Caves, dungeons, decorations, and biomes need to be explicitly excluded to make a flat and empty world.
* Mapgen name: singlenode
  * Developer responsible: celeron55
  * Description: Places only a single node everywhere, namely the one aliased to mapgen_singlenode (by default air).  Intended to be used by mods that perform total mapgen takeovers.


example: `mg_name = v7`

Seed
----

A 64-bit unsigned integer value. At this time, only the lower 32 bits are currently used for randomization.
example: `seed = 1246106421`

Water level
-----------

The y coordinate at which water starts being placed, for mapgens that do place water.
This is also the position at which blocks are assumed to be underground if no block above is present, and thus is not given sunlight.
example: `water_level = 1`

Mapgen Limit
------------

Limit of map generation, in nodes, in all 6 directions from (0, 0, 0).

* Only mapchunks completely within the mapgen limit are generated.
* Value is stored per-world.
* type: int min: 0 max: 31000


example : `mapgen_limit = 4500`

Flags parameter
---------------

The flags parameter is a set of booleans indicating whether or not a certain option is enabled. Global flags applying to all map generators are listed in [mg\_flags](/mg_flags "mg flags"). Other map generator-specific flags are shown below.
Like all other config and Lua flag fields, they are represented as a comma-delimited string. E.g. the flag string "trees, caves, flat" would direct the Mapgen to create flat terrain with trees and caves.
An exhaustive list of currently recognized Mapgen flags:



* Lua/config flag name: mgv5_spflags
  * Defaults: caverns
  * Allowed values: caverns, nocaverns
* Lua/config flag name: mgv6_spflags
  * Defaults: jungles,biomeblend,mudflow,snowbiomes,trees
  * Allowed values: jungles, biomeblend, mudflow, snowbiomes, flat, trees, nojungles, nobiomeblend, nomudflow, nosnowbiomes, noflat, notrees
* Lua/config flag name: mgv7_spflags
  * Defaults: mountains,ridges,nofloatlands,caverns
  * Allowed values: mountains, ridges, floatlands, caverns, nomountains, noridges, nofloatlands, nocaverns
* Lua/config flag name: mgcarpathian_spflags
  * Defaults: caverns
  * Allowed values: caverns, nocaverns
* Lua/config flag name: mgflat_spflags
  * Defaults: nolakes,nohills
  * Allowed values: lakes, hills, nolakes, nohills
* Lua/config flag name: mgvalleys_spflags
  * Defaults: altitude_chill,humid_rivers,vary_river_depth,altitude_dry
  * Allowed values: altitude_chill, noaltitude_chill, humid_rivers, nohumid_rivers, vary_river_depth, novary_river_depth, altitude_dry, noaltitude_dry


Other fine-tuning parameters are available for each map generator, and can be found in lua\_api.md.

Chunk size
----------

The side length (in MapBlocks) of the cubic area that is generated at once. Default is 5; larger values take longer to generate but blocks generate quicker on average and could produce larger, more intricate caves and dungeons.
Don't mess around with this if you don't know what you're doing! This parameter cannot be modified through the Lua API.

