Most of the time Luanti is built with LuaJIT which aims to be faster than the reference Lua 5.1 implemention (referred to as "PUC Lua") due to its JIT compiler. However it is also possible that Luanti is built with PUC Lua 5.1, if Luanti cannot find LuaJIT when building or when explicitly built with `-DENABLE_LUAJIT=OFF`.

There are some reasons one would want to use PUC Lua over LuaJIT such as for stability reasons or if someone is on an obscure architecture that doesn't have a LuaJIT compiler available yet. As such, you should always support both implementations in your mods and be aware of some of the pitfalls that can cause crashes with a mod developed on LuaJIT being run with PUC Lua.

## Goto
LuaJIT implements the `goto` statement along with labels that can be jumped to as an extension to the language. This is not available in PUC Lua, so you shouldn't use `goto` in your mods.

## math.random() argument order independence
LuaJIT is less strict about the order of arguments passed to `math.random`. If you pass a min value that is larger than the max value, it will switch these around. For instance `math.random(3,1)` will swap around the ranges and generate the same random values `math.random(1,3)` would generate.

In PUC Lua doing this will throw an error "bad argument #2 to 'random' (interval is empty)", so make sure you clamp or otherwise make sure that the min value is lower or equal to the max value, swapping them yourself if necessary.

## More...
An exhaustive list of the extensions to the Lua language that LuaJIT provides can be found on [LuaJIT.org's extensions page](https://luajit.org/extensions.html).

## For older versions of Luanti
Since 5.5.0 the [bitop](https://bitop.luajit.org/index.html) library is included when building Luanti with PUC Lua so if your mod targets Luanti 5.5+ it is safe to use the bitop library. This has always been available on LuaJIT, but you cannot rely on it being available on Luanti 5.4 and earlier.
