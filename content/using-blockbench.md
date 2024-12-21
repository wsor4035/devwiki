---
title: Using Blockbench
---

# Using Blockbench
Blockbench is a 3D modelling software designed for making low-poly and voxel models, making it suitable for making Luanti models. As Blockbench supports exporting to .obj it is very easy to create static models and export them directly into Luanti.

It is also possible to use Blockbench for making nodeboxes for Luanti, as well as making animated models that can be directly exported as GLTF in Luanti 5.10 and newer.

## Static models
When opening Blockbench and creating a new model it will ask you about the model type. Pick generic model, which has no limitations and allows you to export to .obj for use with Luanti:

![](/images/using_blockbench/generic_model.webp)

Once created, you are now in the editor which allows you to start modelling. Create some cubes, resize them and move them around, or create meshes where you can manipulate individual vertices.

In terms of scale and the origin, the origin in Blockbench is the same as the origin in Luanti. So e.g. for a cube model mimicking a full node, the cube would have the position of (-8,-8,-8), size of (16,16,16) and centred around the origin:

![](/images/using_blockbench/full_block.webp)

The default scale in Blockbench when exporting to .obj is 16, which means that 16 Blockbench units equal 1 meter inside of Luanti. You can change this scale in Settings -> Export -> Model Export Scale.

Once you have a model, go to File -> Export -> Export OBJ Model to export it.

![](/images/using_blockbench/export.webp)

Once exported into your mod's models folder, it will also place a .mtl file along with any textures next to the exported model. The .mtl file is usually used to map a model's textures, but Luanti does not use this file and can be safely removed.

![](/images/using_blockbench/files.webp)

Luanti is able to load textures from the models folder, but if you want to keep all textures in the `textures` folder instead you can delete those too.

Since Luanti does not use .mtl files for loading model materials, you need to specify them in the code. For example, for a node with the mesh drawtype you specify the model textures in the tiles table:

```lua
core.register_node(":test:red_block", {
	description = "Red block",
	tiles = { "test_block_red.png" },
	drawtype = "mesh",
	mesh = "test_block.obj"
})
```

Even if you have exported your model into an .obj file, **make sure to save a .bbproject project file too!** While Blockbench can import an existing .obj model, some amount of data gets lost during this process. It's best to save a project file and check it into Git such that you or someone else can come back to edit the model at a later date if necessary.

## Nodeboxes
Luanti has a rather basic built-in model format for nodes consisting of a list of cubes called nodeboxes.

There is no direct nodebox export option in Blockbench, but as it allows you to add, move and scale cubes it is easy to use it to visualise a nodebox and manually convert it into nodebox coordinates.

You can also use the [objtonodebox](https://github.com/regulus79/objtonodebox) Python script which can take an .obj model and convert it into a nodebox definition. Simply export your nodebox to .obj from Blockbench and run it through the `convert.py` script.

## Animated models
Blockbench supports rigging models if you select the Animate tab in the top right corner. These animations are kept when exporting to GLTF. As of 5.10 Luanti now supports GLTF models with animations, which makes it possible to export an animated model directly from Blockbench into Luanti.

*(Insert more detailed instructions on doing animated models with Blockbench here)*

Older versions of Luanti only supported the .b3d and .x model formats for animated models. These are both very ancient model formats that Blockbench cannot export natively, so you would need to go via Blender to make animated models for Luanti as it is the only modern 3D modeling software with a functioning B3D exporter. See [Using Blender](https://wiki.luanti.org/Using_Blender) on the Luanti Wiki for more information.
