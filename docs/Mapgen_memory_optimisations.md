# Mapgen memory optimisations
This page intends to list all possible optimisation techniques that can be used when writing a mapgen in Lua.

*This page is based on paramat's [forum topic](https://forum.minetest.net/viewtopic.php?t=16043).*

Lua map generators can use excessive memory if they are not using these 3 optimisations. Not using these optimizations can eventually lead to OOM (out-of-memory) errors because the Lua mapgen wasted way too much memory. Applying this advice is **strongly recommended**, and should make OOM errors much less likely. But there is no guarantee this will fix all OOM errors, your mapgen might still use excessive memory for other reasons, or the computer just has very limited memory.

[toc]

## Only create perlin noise objects once
The noise object is created by `minetest.get_perlin_map()`. It has to be created inside `register_on_generated()` to be usable, but only needs to be created once, many mapgen mods create it for every mapchunk, this consumes memory unnecessarily.

Localise the noise object outside `register_on_generated()` and initialise it to `nil`. See the code below for how to create it once only. The creation of the perlin noise tables with `get_3d_map_flat()` etc. is done per mapchunk

```lua
-- Initialize noise objects to nil
local nobj_terrain = nil
local nobj_biome = nil

-- ...
-- On generated function
minetest.register_on_generated(function(minp, maxp, seed)
	-- ...
	nobj_terrain = nobj_terrain or minetest.get_perlin_map(np_terrain, chulens3d)
	nobj_biome = nobj_biome or minetest.get_perlin_map(np_biome, chulens2d)

	nobj_terrain:get_3d_map_flat(minpos3d, nvals_terrain)
	nobj_biome:get2d_map_flat(minpos2d, nvals_biome)
	-- ...
end)
```

## Re-use a single perlin noise table
The Lua table that stores the noise values for a mapchunk is big, especially for 3D noise (80^3^ = 512000 values). Many Lua mapgens are creating a new table for every mapchunk, while the previous tables are only cleared out slowly by garbage collection, resulting in a large and unnecessary memory use.

A `buffer` parameter was added in 0.4.13 to avoid this, a single table is re-used by overwriting the former values.

```
For each of the functions with an optional `buffer` parameter:  If `buffer` is not `nil`, this table will be used to store the result instead of creating a new table.

#### Methods
* `get_2d_map_flat(pos, buffer)`: returns a flat `<size.x * size.y>` element array of 2D noise with values starting at `pos={x=,y=}` ``\
* `get_3d_map_flat(pos, buffer)`: Same as `get_2d_map_flat`, but 3D noise
```

Localise the noise buffer outside `register_on_generated()` Use the `buffer` parameter in `get_3d_map_flat()` etc.

```lua
-- Localise noise buffers
local nvals_terrain = {}
local nvals_biome = {}
-- ...
-- On generated function
minetest.register_on_generated(function(minp, maxp, seed)
	-- ...
	nobj_terrain:get3d_map_flat(minpos3d, nvals_terrain)
	nobj_biome:get2d_map_flat(minpos2d, nvals_biome)
	-- ...
end)
```

## Re-use data tables
The Lua table that stores the node content IDs for a mapchunk plus the mapblock shell is big (112^3^ = 1404928 values). Many Lua mapgens are creating a new table for every mapchunk, while the previous tables are only cleared out slowly by garbage collection, resulting in a large and unnecessary memory use.

Localise the data buffer outside `register_on_generated()`. Use the buffer in `get_data()` or `get_param2_data()`.

```lua
-- Localise data buffer
local data = {}

-- On generated function
minetest.register_on_generated(function(minp, maxp, seed)
	-- ...
	local vm, emin, emax = minetest.get_mapgen_object("voxelmanip")
	local area = VoxelArea:new{MinEdge = emin, MaxEdge = emax}
	vm:get_data(data)
	-- ...
end)
```

## Conserve VoxelArea:index calls
What the `:index` method of [[VoxelArea]] does is convert the position provided with XYZ coordinates into the corresponding table index in the data table. This method is fast, but obviously not instant, doing some amount of calculations every time.

In order to conserve the amount of calls to `:index`, you can take advantage of the fact incrementing the index will move you on the X-axis:

```lua
for z = minp.z, maxp.z do
    for y = minp.y, maxp.y do
        local vi = area:index(minp.x, y, z)
        for x = minp.x, maxp.x do
            -- code here

            vi = vi + 1
        end
    end
end
```

This will significantly cut down on the amount of index calls required by the main mapgen loop.
