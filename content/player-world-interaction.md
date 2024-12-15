---
title: Player-World interaction
aliases:
- /Player-World_Interaction
---

# Player-World Interaction

Digging a node
--------------

Preconditions are a node somewhere in the map.
This node is pointable, has a selection box and can be dug by the hand or the tool the player is wielding.
The player has interact priv and the tool has a tool range that the node can be pointed.
The node is not stuck somewhere the player can't point it.

*   First look at the node, it becomes pointed\_thing.

Note that on android the node is pointed without looking (referring to the cross position) at it.

*   Then LMB is pressed down while holding an item which does not have on\_use.

If LMB wasn't released before, a click happens, which causes a punch event.

The client send a punch event (client->interact(4, pointed), see game.cpp:3657 (28.02.2017)).

On server side the punch event is passed to mods, see on\_punch and the deprecated register\_on\_punchnode.

Then the client sends the digging start event to the server (interact(0, pointed), game.cpp:3948).

The server uses this information for anticheat measurements.

*   Now continue looking at the node, i.e. keep pointing it, and hold down LMB.

Periodically client-side: Crack animation is updated, digging particles are spawned (if not disabled in the settings) and the node dig sound is played.

The dig sound is either the "dig" field in the "sounds" table in the nodedef

or, if it's not present, the client uses the sound "default\_dig\_${groupname}" (file name extension omitted here), where $groupname is one of the groups the node has, see (game.cpp:4001), and gain is set to 0.5.

The default\_dig\_ thing should be banned from source code in my opinion.

*   Some time later, when the digging time elapsed,

the client sends a digging completion event to the server (interact(2, pointed), game.cpp:4018),

the node disappears client-side,

more particles are spawned (if enabled) and

the dug sound is played.

*   Now the server recieves the digging completion event.

Anticheat probably, e.g due to lag, thinks the player dug the node too fast.

dug\_too\_fast cheat is passed to mods, see register\_on\_cheat, and digging aborts.

If the nodedef has a can\_dig function, it's executed and probably stops the digging.

The on\_dig function in the nodedef is called now.

The default on\_dig function problably removes the node:

The on\_destruct is executed, air is set and after\_destruct is executed.

And probably (the same probably as before) it then calls the after\_dig\_node function in the nodedef if present.