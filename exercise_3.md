# Exercise 3: Collecting basic measurements from your object

The goal of this exercise is to:
<ul>
  <li>Learn how to collect measurements from microCT data and surface models</li>
  <li>Understand the basics of placing 3D landmarks for geometric morphometric analysis</li>
</ul>

This exercise will focus on how to collect a variety of measurements (e.g., depth/width/thickness, curvature/angulation, area/volume) on both your original microCT stack and any models you created from the microCT data. You will learn how to take these measurements in multiple different programs, depending on your analytical needs. 

One major application of microCT data and/or 3D models more broadly is to perform shape analyses using the methods of geometric morphometrics. This technique employs two- (X,Y) or three-dimensional (X,Y,Z) landmarks to summarize and analyze the shape of an object compared to other similar objects or specimens. We will not go into the methods of geometric morphometrics here, or the philosophy and reasons behind where to place informative landmarks, but more details on these techniques are readily available and we encourage you to seek out prior publications with comparable data to those you are working with if you wish to implement these methods. 

### Collecting linear measurements in FIJI/ImageJ
First let’s open up the civil war femur stack in FIJI/ImageJ. Before you do anything, you will need to confirm that the scale of the data is properly set. If you have just imported the original DICOM dataset for this specimen then the scale should automatically be set. If you are importing a TIFF stack, you will most likely need to set the scale yourself. Remember that you can view the file properties by going to *Image>Show Info*. Look for the “voxel size” information and compare that against the metadata for your data. Refer to Exercise 1 if the voxel size is set to 1x1x1 (1 is the default import size for unscaled data). 

In some instances you may further want to set the scale before you collect any measurements. Navigate to *Analyze>Set Scale*. If there’s a scale bar somewhere in your image (for a 2D image) or if there is an object of known size in one of your slices, you can use the line tool to make a line and then tell FIJI how long the line is. However, in our case you should have the voxel size from the scan data; if the voxel sizes are properly set in your image stack properties you should be ready to go. Even with this it might be good to take a quick measurement to confirm that it makes sense in regard to how large the actual object is. After you set/confirm the scale, taking measurements is as simple as using the line tool and telling ImageJ to record the length of that line. Select the line tool from the main toolbar, place the endpoint of the line across the part of the slice you wish to measure, and then you can either record the length of the line from the readout on the tool bar or go to *Analyze>Measure* (Ctrl+M) and the measurement (and any additional measurements after that) will be placed into a table that can then be exported. Use a similar process to calculate areas (use the freehand selection or polygon tool) or angles. Your screen will look something like this as you set your scale and take measurements: 

![image](https://user-images.githubusercontent.com/90789390/184918300-ab201b55-1a82-4c80-bfed-e4dd3d4a8be1.png)

### Collecting linear measurements in 3D Slicer
Once we’ve segmented a structure that we’re interested in and we’ve created (exported) it to a model within 3D Slicer, basic measurements like surface area and the volume of the mesh can be found in the Information tab of the Models module (locate and navigate to this module using the magnifying glass or the dropdown menu at the top of the screen). For instance, if you wanted to know the volume of the Bird Effigy Whistling Pot, you could make a model of the segment of the inside space that you made in Exercise 2 and measure the volume of that segmented model. 

This module will look something like this:

![image](https://user-images.githubusercontent.com/90789390/184918461-2e433eda-957d-4a18-b66e-25ddc58f035d.png)

Linear measurements on a surface model can be made in the Markups module (locate and navigate to this module using the magnifying glass). There are a number of available tools in this module, including measuring linear distances, angles, or the length of a curve. For example if you wanted to know the diameter of the aperture of the Bird Effigy Whistling Pot, you could use the linear measurement tool (the icon is a ruler) to make two points in either the 3D or 3D views and the program would take a measurement between them. Similarly you could measure the circumference of the aperture by using either the open or closed curve markup tools. Or measure the angle of the base to the external walls using the angle markup tool. Make sure to expand the Measurements section of the menu and then click “Enabled” to see the relevant measurements. 

You can learn more about the Markups module at https://slicer.readthedocs.io/en/latest/user_guide/modules/markups.html 

For example, taking a measurement of the width or circumference of the mouth piece on the Bird Whistling Pot would look something like this:
![image](https://user-images.githubusercontent.com/90789390/184918562-9a1e9876-bba7-44dd-b9e1-b173b4540726.png)

### 3D Geometric Morphometrics (in 3D Slicer, Meshlab, and then 3D Slicer again)
Let’s say you are interested in analyzing the shape of the distal femur example dataset we have provided. To do this you may wish to apply a series of 3D landmarks on your model. However, the chances are high that your model is too large at this point to make this very easy. In other words, it has too many polygons for 3D Slicer’s Markups module to handle. There are two ways to reduce the polygon count: 1) creating a solid model where all internal spaces are filled and 2) mesh decimation (which we explained in Exercise 2). In this case, because we are looking at bone and because it was created from CT data, the dataset includes all of the internal anatomy and trabecular/spongy bone and associated air pockets. All of that internal structure makes the model exponentially larger than it needs to be if you are only interested in the exterior surface. 

First load the Civil War femur dataset into 3D Slicer following the instructions in Exercise 2. Make sure to use the Volume Rendering model to make your model visible and adjust the histogram via the Display>Shift slider. Now go to the Segment Editor module and use the Threshold tool to create a rough segmentation of the bone. We suggest starting with a threshold of around 150 to 175; this seems to select bone but does not select the slight bits of shadowing in some areas on the bone (e.g., the articular surfaces). Play around with this threshold value until you are happy. 

Now you will use the Margin function to grow and shrink the selection so that the internal spaces of the bone are filled. This function allows you to set the Margin size, which is the area by which you want the selection to grow or shrink. Set this so that the Margin size is about 1.00 mm, and make sure the Operation is set to Grow. Click Apply, and once this is done, scroll through the image stack; you should notice that many of the small trabecular spaces are now filled and that the selection has expanded out from the bone into the air surrounding the specimen. There will also be some remaining spaces inside the bone. You will probably want to perform one more Grow operation to make sure everything gets filled. Next, you will want to Shrink your selection by the same amount that you grew it, so the boundaries of your selection return to roughly match the outline of the bone. Your resulting data should now look something like this:

![image](https://user-images.githubusercontent.com/90789390/184918697-c6bf81f1-7fd3-4a30-a493-adde646843fc.png)

Scrolling through your image stack, you will notice that, though this Grow/Shrink operation mostly filled the internal structure of the bone, there are some holes remaining and the medullary cavity (the center hollow portion of the shaft of the bone) is not filled. 

From here you have three options: 1) use the Paint tool to manually fill the holes still present in the segmentation slice by slice; 2) use a combination of the Paint tool and the Fill Between Slices tool as demonstrated in Exercise 2, or 3) not worry too much and use the model you’ve just made using the Margins and Thresholding tools (though this will increase your model size a bit, this is still much better than including all of the small trabecular holes in your model). If you do want a filled model we suggest you use some combination of manual filling and Fill Between Slices. 

If you opt to use the Paint and Fill Between Slices option (2) then start by creating a new segment. Then start near the cut end of the bone and use the Paint tool to manually select the open cavity inside the bone. Note that you can change the Paint brush sphere size to make selection a bit quicker. Scroll down (toward the articular surface of the bone) a few slices and do the same thing. Now use the Fill Between Slices tool to connect the slices you’ve selected. Initialize, and see what the preview looks like. If it looks good and there is no segment peeking out of the bone then go ahead and hit Apply. Next use the Logical Operators function to combine your two segments as described in Exercise 2. 

If you find that there are small bits of segmentation that do not match the bone contour (i.e., there are bits of selection outside the bone you’d like to remove) you can use the Erase function and, moving through the stack slice by slice, remove those portions you do not wish to be in the final model. 

For example, this image shows a bit of extra material selected on the very top margin of the slice:
![image](https://user-images.githubusercontent.com/90789390/184918759-01183e36-cde8-4795-88b2-acf1f7fc4b18.png)

Now export your model as an .stl or .obj file (*Segmentations…>Export to files…*). Save this file to your computer, and then open this model in MeshLab. Note that the thresholding from 3D Slicer also included some floating points in the model. You can delete these floating bits by using the “Select faces in a rectangular region” and then “Delete selected faces and vertices”. Follow the instructions for cleaning and decimating your mesh in Exercise 2; we suggest decimating down to about 500K faces. Make sure to save your now much smaller model. 

Next return to 3D Slicer and import your new, smaller, femur mesh. You can use the Load Data  function on the main 3D Slicer screen and select your mesh file (these will usually be in .stl, .obj, or .ply format). Now, navigate to the Markups module. There are a lot of different functionalities here but let's say you are interested in the curve of the medial border of the patellar surface (that’s the border between the smooth part where your patella goes and the rest of the bone; see the figure below for reference). 

Place 5-8 points along this border using the Open Curve tool. You can then tell the module to resample that line using any number of points, which will make a more accurate curve along the surface. For example: 
![image](https://user-images.githubusercontent.com/90789390/184918819-55f496fd-978c-49a3-ad99-1db26ae43cef.png)
![image](https://user-images.githubusercontent.com/90789390/184918865-da70982d-e465-42d5-827d-12367b8fd54a.png)

You can also place fixed landmarks in the Markups module. To do this, use the “CreateFiducial Markups” tool (depending on the version of 3D Slicer you are using this might alternatively be named “Create Point List”) and then click on your model to place a point. In order to keep placing points that are associated with the same node (which is important if you want to create semilandmarks) you need to click “Place a control point” (up near the camera icons) (see the figure below to located these tools/options). 

![image](https://user-images.githubusercontent.com/90789390/184918933-6b7b093d-07d2-4921-b7eb-977e7b20c89a.png)

Points in the same node should have similar naming conventions, usually starting with F or F_1. So the first point in the F node will be F-1. The next one is F-2, and so on. Subsequent nodes will be named F_1 and points in that node named F_1-1, F_1-2, etc. The names of the nodes will be listed in the Node toolbox, the names of the points will be next to the points in the 3D viewer and you can see a list of the points in the “Control Points” drop down menu . If you want to adjust the position of an existing landmark, simply use the cursor tool and click and drag the point on the model; to delete a landmark just click on the landmark and use the delete button on your keyboard or right click on the landmark (this also gives you the option to rename landmarks. 

Once you’ve placed at least 4-5 points in the same node, navigate to the Create SemiLMPatches module. In Parameters, select your model and the corresponding landmark set (in this case it is F_1). Now you tell the module which three points in the set you want to create a patch of semi-landmarks. For example, this image shows a patch of landmarks placed over the distal end of the femur. 

![image](https://user-images.githubusercontent.com/90789390/184918987-558f2811-2286-477b-8c16-0dfb081a35ac.png)

Much more work with landmarks and semilandmarks is beyond the scope of the tutorial here, but we encourage you to take advantage of the documentation for the Markups module (https://slicer.readthedocs.io/en/latest/user_guide/modules/markups.html) and the SlicerMorph (https://slicermorph.github.io/) extension that is specifically designed for geometric morphometric analyses.

## Next Up
### [Exercise 4: Analyzing the internal structure of your object](/exercise_4.md)
