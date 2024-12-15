---
title: Objects
aliases:
- /Engine/Objects
---

# Engine/Objects
In Luanti, an object is a moving thing in the world. The two types of objects are players and entities.

A static object is one that is saved in a mapblock, and an active object is one that is currently loaded and updating in the environment.

ActiveObjects
-------------

ActiveObjects aka objects are objects in the environment, consisting of roughly everything that is not part of the voxel world (=Map).

`SAO = ServerActiveObject CAO = ClientActiveObject`

`serverobject.{h,cpp} clientobject.{h,cpp} content_sao.{h,cpp} content_cao.{h,cpp}`

All objects have a server- and a client-side counterpart. The server-side object types that currently exist are

* TestSAO (a small test thing)
* ItemSAO (old item; not used)
* LuaEntitySAO (all entities defined in Lua; basically everything other than the players), and
* PlayerSAO (the player objects which enable standard object interaction for players. Players also have a ServerRemotePlayer or something like that which handles the things in which players are different to other objects).

Client-side objects:

* TestCAO (obvious)
* ItemCAO (obvious)
* GenericCAO (everything else; LuaEntitySAOs and PlayerSAOs register as this on the client-side. This enables them to have the exact same capabilities in terms of looks, client-side interaction and stuff.)

If eg. implementing meshes to go through the regular Lua->server->client pipeline, one'll want to implement them in GenericCAO, through ObjectProperties. ObjectProperties should contain the filename of the mesh (which should be transferred like images), and possibly some small additional information.

All the players on the server have an associated PlayerSAO object, of which generally all will appear on clients as GenericCAO client-side objects.

The CAO of each player also exists on the player's clients itself, just like the other players. It is always hidden and is used for nothing. It doesn't cause any considerable overhead and filtering it out server-side would make the systems messier. On a client, the local player is a separate thing (a LocalPlayer, added to the environment in Client::Client(); it is similar to the ServerRemotePlayers mentioned earlier).