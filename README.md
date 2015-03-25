# Cities: Skylines Mods

I'm starting to put up all of my *Cities: Skylines* stuff into a GitHub repo so that others can look at it.

## Modeling process

### Software used

* Modeling: [Maya 2014](http://www.autodesk.com/products/maya/overview). I also use the [Nightshade UV Editor](www.creativecrash.com/maya/script/nightshade-uv-editor) plugin to make UV editing easier.
* Texturing: (Adobe Photoshop CC 2014)[http://www.adobe.com/products/photoshop.html]
* Vector art (to be rasterized in Photoshop): [SketchApp](http://bohemiancoding.com/sketch/)
* Normal Mapping: [Crazybump](http://www.crazybump.com/)

### General workflow

#### Creating the model

The first thing I always do in Maya is check my units settings by going to *Window* -> *Settings/Preferences* -> *Preferences* and then go down to *Settings* and make sure that the units I'm working in are in *Meters*. 8 meters = 1 unit in Cities: Skylines.

I begin to model what I want in Maya, usually starting out by blocking out the big stuff first. I also don't necessarily build out everything as a single mesh--I build multiple meshes, then do UV mapping for each model, and then combine all meshes towards the end once the UV mapping is mostly done.  Otherwise, you're dealing with too many UV shells when trying to map everything. I always find it easier to separate everything out for these types of workflows.

I generally try to keep things as low-poly as possible, except for noticeable features that benefit from more detail.

#### UV mapping

I assign all meshes the same material, so when I update the diffuse texture it updates on all of the meshes. Since I keep my meshes separate, I do the UV mapping mesh-by-mesh. I create a new UV map for each mesh (usually using *Automatic mapping* with the following options: *Planes: 6*, *Optimize for: less distortion*, *Shell layout: Into square*, *Scale model: Uniform*.

I then move all of my UV shells off to the side (off of the main square) and do any sewing/manipulation before moving it back onto the map. This just keeps shells out of the way. Btw, a shell is just one or more polygons that are attached by UVs.

Keep in mind, I don't usually move all of the UVs shells onto the main UV square until I've started on the textures

**General UV Editing Tips**
A few tips when editing UVs:

1. Use the [Nightshade UV Editor](www.creativecrash.com/maya/script/nightshade-uv-editor). It lets you do things like stack UVs, flip/rotate shells, normalize texel density, all of that jazz.
2. Having trouble selecting UVs, especially when they're stacked on a formerly-connected seam? Select the face of the object, then in the window hit CTRL+MMB and select "To UVs". That will select *only* the UVs associated with that particular face.  You can do this with any parts of the object, like edges or vertices.
3. Keep in mind that UV maps wrap horizontally, so if you have a big and wide poly face that needs a tileable texture, you can have the texture fill the entire width of the texture map (keeping in mind the height). Then you can stretch a really wide poly beyond the limits of the UV box because the texture will just carry over.

#### Texturing

I generally do my textures in a single PSD file, with layer groups for each type of texture map (diffuse, specular, normal map, etc.) I am going to use with the model.  

**The diffuse map**
I always start on the diffuse texture map, because it's easy to see how it will look in Maya.  Since my model is--at this point--still broken down into multiple meshes, I just work on texturing the bigger meshes first (or whatever meshes require the most texture map real estate).

For each texture I add to the map, I try to work in increments of 64/128/256/512 pixels.  Ideally, no single texture is more than 256x256px (or 512x128, etc). That way I can still make sure I have room.

If there's any custom art (symbols, logos, text) I tend to do that in a vector app like SketchApp, and then import the files into Photoshop.

For small parts of the model (where detail wouldn't be easy to see), I tend to use a small block of solid color. That way I can just size down my UV shells to an almost zero size and fit them inside that block of color. They won't suffer from a blurry texture because it's just a solid color.

I then move from mesh to mesh and pick all textures I want to add, and have the textures in place in my diffuse map texture, that's when I start moving in all of the UVs into the main UV area, and check in Maya to see if the texture sizes I'm using provide enough or too much detail, and I tweak things accordingly.

Sometimes, I will export a FBX of the model right after I finish the diffuse map, because it's always good to see how the textures look in-game. That way if there are changes to make, I won't have to make changes to the other maps (normal, specular, etc.).

**The normal map**
When I'm done with the diffuse map, I tend to then work on the normal map. I create a layer group in Photoshop and flood it with this color: Red: 128, Green: 128, Blue: 255 (#8080ff). This is the "zero color" for normal maps (meaning that the material if considered flat).

With Crazybump you can import images/heightmaps straight from the clipboard. So what I do is I select the Photoshop layer from the diffuse texture, copy it to my clipboard, and paste it into Crazybump.  When I'm dealing with creating normal maps for textures that have a lot of detail that's not meant to translate into "bumpiness", I will often create my own heightmap to use as the source image for Crazybump. That way I have more control over what gets "relief" in the texture.

When I'm done with the normal map, I save it back to my clipboard and paste it into the Photoshop layer group for normal maps, right over where the diffuse texture was.

**The color map**

I just start with a blank black canvas, and paint white wherever I want color variations to appear (adjustable in the Asset Creator inside of Cities: Skylines).

**The specular map**

I always make sure to create a black fill layer as the background for the map.Sometimes I grab the specular map from Crazybump, and just modify that from there.  Other times, when I know how I want the specularity to behave, I just create it from scratch. 

**The illumination map**

I still don't quite know how important this is, especially since there's no "night time" mode in this game. But it's essentially the same process with the specular map: I start with a black fill layer, and then brighten areas that are meant to "emit light".

#### Wrapping up the process

When I'm done, I go to *Mesh* -> *Combine* to make sure that all my meshes are a single mesh. The final mesh should retain all of the UV coordinates created earlier.

### Texture sources

* http://www.cgtextures.com/ - Royalty-free textures.
* http://gametextures.com/ - Costs money, has less textures than cgtextures, but they're more refined at the very least.

## Making custom maps

### Software used

* Heightmaps: I use [WorldMachine](http://www.world-machine.com/) for generating realistic heightmaps for when I make maps.
