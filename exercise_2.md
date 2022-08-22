# Exercise 2: Creating a 3D model of your object, inside and out

The goal of this exercise is to: 
<ul>
  <li>Learn how to segment your data to create a 3D model</li>
  <li>Exporting your segmented data and model</li>
  <li>Opening your 3D model in other programs</li>
  <li>Smooth and edit 3D surfaces </li>
</ul>

This exercise will focus on how to take your data from a set of TIFF images with a variety of different gray scale values (i.e., a volume) to a 3D model. This requires that you assign specific voxels to certain materials; this process is referred to as **segmentation**. For instance, the computer does not actually know that the lighter voxels are ceramic and the darker ones are empty space, it is only via our knowledge and context that we recognize that this is the case. 

In this exercise, you are going to use various tools in the Segment Editor module of 3D Slicer to create two 3D models of a ceramic vessel. You will specifically use Dataset 1, the Bird Effigy Whistling Pot; unless you have a higher-powered computer we recommend that you use the downsampled (8-bit) dataset (either that you downloaded from MorphoSource or that you created in Exercise 1). 

### Thresholding	
First, load your data into 3D Slicer. Navigate to the ImageStacks module and browse to the location of your files. Select one of the images, and make sure the voxel size is correct (see the Spacing information). If the voxel size is not accurate, refer to the metadata for your image stack and find the voxel size. Copy those values into the Spacing section (x, y, and z dimensions) 

Once your data is loaded, use the magnifying tool to navigate to the Segment Editor module. There are many different tools in this module and which ones you use will be a function of the materials you are working with and the kind of questions you’re interested in. Go ahead and rename your segmentation to something you will remember, by clicking the “Rename Current Segmentation” choice in the Segmentation drop-down menu. Click the Add button to add a few segments to your segmentation. You can rename the segments by double-clicking on the text. You will start with the threshold tool (you can see the names of these effect options in the left hand menu). This tool uses a volume-wide grayscale cutoff (or ‘threshold’) to define voxels in a segment. Start by telling it that any voxel with a value between 80 and 255 (for an 8-bit volume) is part of segment 1. As you change the slider, you should see a preview in the orthogonal slice viewers. What you will notice is that there doesn’t seem to be a value that consistently selects only clay across the whole volume. Too high and you are only selecting the most opaque clay, too low and you start selecting some of the artifacts surrounding the base of the vessel. So 60 seems to be a good compromise, though you may wish to apply a slightly different threshold depending on your goals. One thing to note here is that this threshold slightly overselects the ceramics in some places and under selects in others. Click Apply to add your selection to segment 1. If you want to see what the segment looks like, click the button named “Show 3D”. This can be improved upon. Note that it helps to turn off 3D view (by deselecting “Show 3D”) when you are segmenting; because image rendering in 3D requires so much computing power, segmenting will go faster with this setting off. Depending on your dataset size, it may take a moment for the 3D view to appear; when it does if you still have your volume rendering showing it may only barely overlap that gray volume rendering. You can turn off the volume rendering by going back to the Volume Rendering module and closing the eye button. 

You may notice in your slices that there are some small holes in the model that were not included in the thresholding. The best way to fill these is to use the Margin function to grow and shrink the selection so that the internal spaces of the object are filled. This function allows you to set the Margin size, which is the area by which you want the selection to grow or shrink. Set this so that the Margin size is about 1.00 mm, and make sure the Operation is set to Grow. Click Apply, and once this is done, scroll through the image stack; you should notice that many of the small spaces are now filled and that the selection has expanded out into the air surrounding the object. You may want to perform one more Grow operation to make sure everything gets filled. Next, you will want to Shrink your selection by the same amount that you grew it, so the boundaries of your selection return to roughly match the outline of the object.  Scrolling through your image stack, you will notice that, though this Grow/Shrink operation mostly filled the internal structure of the object, though there may some large holes remaining. 

Your end result should look something like this:
![image](https://user-images.githubusercontent.com/90789390/184916685-032bfb2e-a3b5-49dd-934d-c9590f946272.png)

### Draw, Fill Between Spaces, Logical Operations
Instead of using the Margins function to fill in the base of this model, the other option is to manually fill in the base or any other parts of the model you would like to adjust. First, you may wish to change your view to zoom in on a single orientation; to change your views use the button on the top menu bar just left of the cursor icon. Select “Red slice only” and slide down to the base of the object. You will notice that the surface of the base interior is not level, it has ridges. Additionally, the threshold we chose does not fully select the base of this object. 

![image](https://user-images.githubusercontent.com/90789390/184916794-c5d860af-acb5-4d20-928d-a23ec7c5a8e0.png)

Change your view to “Green slice only”. One way to fill in the base is to make another segment and manually add the voxels you would like to be included in the segmentation. It is best to use a new segment (and make sure to allow overlap) for the base; you can always combine the segments later. Depending on your preference you may wish to use either the Paint or Draw tools (both work particularly well paired with a graphics tablet). The Paint tool allows you to use your cursor to paint the voxels you would like added to the segment. With the Draw tool, you will use the cursor to outline the edges of the area you would like added; once you have outlined the area you want, right click to accept that area (this may take a moment). Use the “Undo” button at the bottom of the menu if you make a mistake.  

Unfortunately, the Draw and Paint tools only work on a single slice. So you will need to use one or both of these tools to outline the edges of the base every ~5-10 frames. You can then use the “Fill between slices” tool to interpolate the segment between the drawn frames. 

As you draw in frames, your screen should look something like this:
![image](https://user-images.githubusercontent.com/90789390/184916864-ddee60f6-ae38-46d6-a06f-5902548fab03.png)

Click on the “Fill between slices” tool and at the bottom of the left hand menu click “Initialize” to see a preview of the interpolation (this might take a moment to process). Scroll through the slices between those you manually filled and confirm that the interpolation worked properly. If you are happy with it, click “Apply.”

Now select the “Logical Operations” tool. Select your main segment up top (where all of your segments are listed) and the base segment as your modifier (in the Logical Operations tool options at the bottom). Use the Add operation, and click “Apply.” You should now have a complete 3D model of the bird-whistle pot with the original segmentation from the threshold and your manually segmented base added together.

Remember- segmentation is a bit of an art. It can take some time to develop the skills to segment complex objects quickly. We encourage you to review the 3D Slicer help regarding Image Segmentation regarding tips and tricks for this process. 

### Paint, Islands
What if you want a 3D representation of the inside of the pot? For this you will create two new segments – a red one and a blue one. The red will be your stoppers – these will allow you to isolate the inside of the pot from the outside. There are five major holes in this object and each will need to be plugged. In the red view, select your red stopper segment and slide all the way to the top of the cylinder. Then, using the paint tool, make a circle that will stop up the opening. Be sure to overlap your main body segment. Now, in the green view, navigate to the head. You have to stop up the “eyes” and “mouth” of the bird. Again, you will use the Paint tool but make it a sphere brush, and navigate through the slices until the entire hole is stopped up. Repeat this process for any other holes. 

As you stopper up the holes, your screen should look something like this:
![image](https://user-images.githubusercontent.com/90789390/184916959-3a6aefec-7cad-4980-88ed-e4e06c8b33f3.png)

Now select your blue inside segment and navigate to the “Islands” tool. Check “Add selected island” and then click in the empty space inside the pot. If you have successfully isolated the inside, the internal cavity should be segmented out. If it doesn’t work, double-check to make sure there are no small openings somewhere else. It might help to slightly grow your main body segment by a pixel or two using the Margins tool. You should now have a 3D model of the inside of the pot! This technique can be easily translated to bones if you wanted to, for example, make an endocast of a skull.


The space inside the pot should look something like this:
![image](https://user-images.githubusercontent.com/90789390/184917059-2f573ffb-a5d1-4d40-9067-9cbe787551d0.png)

If you want to 3D print your model having a lot of empty space and extra surface area will slow down the print considerably and increase the probability of failure. You will want a solid model of the whole bird-whistle pot. If you’ve already segmented out the inside space of the pot, this is quite easy to do. Simply use the Logical operations tool as above, adding the clay surface and the inside space together to create a model that includes both the ceramic of the pot and the space inside the pot. 

### Wrap Solidify
Another option for creating a solid 3D model or creating a model from the internal structure of an object is to use the “Wrap Solidify” tool. This tool allows you to take a model with lots of holes in the surface and turn it into a simple solid object. It uses a combination of shrinkwrapping, projection, and solidification algorithms. However, it can be very computationally intense and take a while for your computer to process. Also, the Wrap Solidify tool will sometimes leave unwanted artifacts between slices that you will have to manually remove. Whether you use this or the above method to create a solid model will depend on your priorities and needs for your specific project. 

If needing a solid model of the whole object, select the “Outer surface” option for region in the Wrap Solidify tool menu. If you want to create something like an endocast, select the “Largest cavity” option. It’s probably best to have the tool output to a new segment. The advanced options are something you might need to play with to make the output look better. Hover your cursor over them to see details. Use this function with caution as it can be very computationally intensive!

### Smoothing and Exporting your 3D model
Once you have a model that you are happy with you will want to smooth your model to even out any rough surfaces. This can be accomplished using the Smoothing tool in the Segment Editor. In this case, you do not need to smooth that much because most of your segmentation is accomplished using various thresholding tools. Your 3D model looks pretty good. We recommend starting with a fairly small Kernel size and the Median smoothing method. If your model still seems jagged, you can always increase the values and do it again. Keep in mind that, at this stage, the model will always have a slight “terraced” appearance close-up. Also note that the larger your model the longer this smoothing function will take to process. 

You can export your 3D model to an .stl or .obj file using the Segment Editor module. Make visible which segment or segments you wish to export. Then click on the drop down arrow beside the “Segmentations…” button and select “Export to files…”. Navigate to the destination folder for the model and make sure to select the file format you prefer. 

It might also be useful to export your segmentations to a model within 3D Slicer. This allows us to work with and manipulate the meshes without opening another program. In the same drop down you found the “Export to files…” option, select “Import/Export nodes…”. Make sure your output type is Models, and click Export. If you navigate to the Data module, you can see that there are a bunch of new meshes that were based on your segments. 

### Opening and Decimating Models in Meshlab
It’s very possible that the model you’ve just created in 3D Slicer is either large or still needs a bit of editing to finalize. To address both of these issues, we recommend opening your exported model in Meshlab. Opening your exported model in Meshlab is simple: either you can select File>Import Mesh, or you can click and drag a model from where you have it saved in your files into the main viewer window. However, depending on the size and level of detail in your model it might take a while to load. Once it does load, take note of some of the information along the bottom of the screen. It should tell you how many vertices and faces there are in your model. For faster load times and less lag, you can reduce the number of vertices and faces, at the cost of some detail. You can do this by specifying a target number of faces or a percentage reduction in faces you would like. This process is referred to as Decimation. To do this go to Filters>Remeshing, Simplification etc…>Simplification: Quadric Edge Collapse Decimation. You can specify the target number of faces; what number you put in really depends on how much model quality you want to trade for ease of use. Generally with microCT data (or even surface scanner data) it is possible to very heavily decimate your model and still retain a considerable amount of detail. We encourage you to play around with different decimation thresholds and examine the results. 

Your mesh might also have other problems, and it will probably be helpful to familiarize yourself with some of the tools in the Filters>Cleaning and Repairing menu. For example, removing duplicate faces and vertices is a good idea, as is removing unreferenced vertices. Probably the most important will be Remove Isolated Pieces. You might have been unable to segment out some of the floaty bits (the technical term) in 3D Slicer, but you should be able to get rid of them in Meshlab. You can define the minimum number of faces in an isolated piece that you want to keep.  

Make sure to properly save your edited 3D model. To do so go to *File>Export Mesh…* or *File>Export Mesh As…* (use the latter if you would like to change your file format and/or retain your original file). 

## Next Up
### [Exercise 3: Collecting basic measurements from your object](/exercise_3.md)
