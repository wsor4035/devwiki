# LuaJIT
LuaJIT is a just-in-time compiler for Lua, which implements the language as it was in the reference Lua 5.1 implementation (referred to as PUC Lua to distinguish it) albeit with some additions and differences (see [LuaJIT differences](/LuaJIT_differences/)).

More often than not, unless you have compiled Luanti from source without LuaJIT, Luanti will use LuaJIT as its Lua runtime. The official Windows, Android and most packaged Linux builds should be compiled with LuaJIT enabled. To confirm what Lua runtime Luanti is built with you can open a terminal and run `./luanti --version`.

If you are using LuaJIT the result would look something like this:

```
$ ./luanti --version
[...]
Using LuaJIT 2.1.1702233742
```

If you are using PUC Lua the result would look something like this:

```
$ ./luanti --version
[...]
Using Lua 5.1.5
```

When building from source, Luanti will always use LuaJIT if it is found on the system. This usually means having the development package for it installed. If LuaJIT is not found or if `-DENABLE_LUAJIT=FALSE` is explicitly passed then Luanti will fall back to the vendored PUC Lua 5.1.
