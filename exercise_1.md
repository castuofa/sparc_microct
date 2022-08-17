# Exercise 1: Loading and visualizing your data

The goal of this exercise is to: 
* Open and visualize microCT data
* Crop or convert your data to minimize file size
* Process your data to optimize visualization and analysis

Exercise 1 is focused on loading and visualizing your data. This may sound very basic but it can be a lot harder than it sounds. For this exercise, you will use two programs with slightly different capabilities and interfaces: FIJI/ImageJ and 3D Slicer. You can use any of the three example datasets provided for this exercise. Part of this exercise will also show you how to take a very large, 16-bit dataset and reduce the file size by converting to 8-bit, cropping your image stack, and downsampling your data (i.e., increase voxel size). 

*If you are working on a computer that does not have particularly high RAM or data storage, we recommend you start out with the downsampled data files (i.e., the 8-bit files) we have provided for you, rather than trying to load the full datasets.*

### Importing and processing your data in FIJI/ ImageJ
We will start in FIJI/ImageJ. After opening the program, click on Edit>Options>Memory & Threads. In the box that opens, change the maximum memory to at least 10,000 MB and leave the rest of the settings as they are. Click OK. Now click File>Import>Image Sequence, and navigate to the directory where you have your stack (it is best to only have one image stack per folder). Do not modify anything in the options window that follows yet. After a bit of loading, you should have an image stack you can scroll through with a slider. You can also scroll through it using your mouse wheel (holding Ctrl while scrolling will zoom in and out). Note that the slice number changes as you move through the stack, and this corresponds to the specific image in the folder containing your image stack. Also, note that it is unlikely that the object you're interested in takes up the whole view box. 

At this point your data are potentially unscaled (i.e., voxel size = 1). To view the voxel size of the data and determine whether your data are unscaled you will want to view the properties and file info for your dataset by going to Image>Show Info or Image>Show info…. This is particularly useful for DICOM image stacks where the metadata will also be imported into FIJI/ImageJ. If your information says that the voxel size is 1x1x1 pixel^3 then your data are unscaled. If you are unsure if the data are properly scaled, compare these dimensions with the voxel dimensions provided in the scan metadata. To properly scale your data to match the voxel size of the original scan go to Image>Properties and set the pixel width/height/depth to match the dimensions listed in the original metadata (in the case of our example data, the original metadata is the xtekct file; you can open this file with a text reader) (Figure 1-1). Make sure to set the units (in most cases this will be mm). 



### Decreasing the size of your data, saving your changes, adjusting, and editing
*It’s important to note that many of the following steps will overwrite the original files you have loaded into the program (though not your original saved data). In other words, there is no “undo” or back option for the changes you make in the FIJI/ImageJ. You may wish to first duplicate your image stack so that you have the ability to easily “undo” changes.*

#### Duplicating a stack
Because many changes made in FIJI cannot be undone, duplicating a stack before making such changes provides an “undo” opportunity. To do this, select Image>Duplicate… from the menu bar. The window that pops up will provide the option to “Duplicate stack”, which you will need to select in order to duplicate each image in the image stack (note, if you wish to duplicate only a section of the image stack, enter the range of images in the text box to duplicate just that portion of the stack). Click “OK”.

#### Cropping your data
One way to decrease the size of your image stack is to crop your dataset to just the object of interest. This allows you to remove any space in the scan surrounding the object (i.e., air or packaging) and/or to remove aspects of the object you are not interested in analyzing. 

First, if you notice there is a lot of empty space around your object you have the option to crop images in FIJI/ImageJ in the X and Y dimensions. To do this, select the rectangle tool and draw a polygon over your image stack. Scroll through the entire image stack (Z-dimension) to make sure your polygon encompasses everything you want it to; adjust where necessary. Once you are satisfied select Image>Crop. 

You may also wish to crop your stack in the Z dimension (i.e., if there are empty slices or objects not of interest at the top or bottom of the image stack). To do this, use the Delete Slice Range tool by selecting Image>Stacks>Delete Slice Range and then type in the inclusive range of slices that should be removed. If you want to remove slices at both the top and bottom of a stack you may need to use this tool multiple times. 

#### Convert your data from 16-bit to 8-bit
Another way to decrease the file size is to reduce the amount of information contained in each pixel. Usually unprocessed scans are 16-bit, which means that each pixel can have one up to 2^16 different values (~65K shades of gray). You can reduce that to 8-bit simply by clicking Image>Type>8-bit. Downsampling your data this way will cut your file size roughly in half but you will lose considerable resolution in the data. 

#### Resizing your image stack
Another option for decreasing image stack size is to resize your image stack by selecting Image>Scale… When the control box appears, you can either select the number of pixels or scale by a percentage of the original pixel dimensions (X/Y/Z). Note that the depth (i.e., the number of images) will not automatically change when the X (width) and Y (height) dimensions are changed. If you wish to scale your image stack so all of your voxels remain isotropic (i.e., equal in all three dimensions), this value will also need to be adjusted to be proportional to the change in the width and height (i.e., decrease all values by the same percentage). Resizing effectively averages across pixels/voxels and will also decrease the resolution of your data. 

#### Editing images in an image stack
If there are small inclusions or artifacts included in only a few image slices, these artifacts can be removed manually by using the selection tools on the menu bar (rectangle, oval, polygon, freehand etc.). To select the region of the image you wish to remove and then selecting Ctrl + X. If multiple images are affected, you will have to scroll sequentially through the images selecting and deleting regions of interest.

#### Adjusting the histogram
Another option that you can take advantage of in FIJI/ImageJ is to adjust the range of grayscale values in your scan; this will help to make fine gradations in values more obvious. For instance, the empty space around the object might actually have a range of values between 0-40 (in an 8-bit image; this information can be found at the bottom of the FIJI/ImageJ menu bar as “value=” as you cursor over the image) but it might be more useful if you could tell FIJI/ImageJ to essentially condense those values to 0-10 and widen the range that is occupied by your object. Currently, this is best done in FIJI/ImageJ by navigating to Image>Adjust>Brightness/Contrast. Utilize the “Auto” and “Reset” buttons or manually adjust the “Minimum,” “Maximum,” “Brightness,” and “Contrast” sliders until you are happy with the grayscale image. Scroll through the stack to ensure that there are no extremely white or extremely black regions. If you find these, then continue to adjust options in the Brightness and Contrast window until satisfied. When the entire stack looks good, click “Apply”. Remember that once you accept these changes they will write over the dataset you originally imported into FIJI (though not your original saved data). 

#### Thresholding data
In some instances you may wish to identify all pixels over or under a certain threshold (e.g., when selecting all bone in a specimen). This can be accomplished in ImageJ via Image>Adjust>Threshold.
If you wish to apply this threshold to the entire image stack, in the first options box select “Stack histogram” and “Dark background”. Click “Auto” or use the sliders until the background is completely red and your material of interest is in white. Make sure to scroll through the slides to confirm that all of the images have segmented properly; note that if the quality of the scan is not great, the Auto function may not work. Once you are satisfied that you have adequately separated the material of interest from all other materials, click “Apply”. Then in the second options box Deselect “Calculate threshold for each image” (no boxes should be checked). Click “OK”. The resulting image stack should show your material of interest in white and all other pixels in black.

#### Saving the new stack
At any point in time you can save the image stack you are working on by selecting File>Save as>Image Sequence… from the menu bar. Choose your format (TIFF is a non-compressed image format, which is preferred to maintain grayscale value integrity). Name the stack as you wish—the name will be assigned to every image in the stack, followed by a number indicating that image’s specific sequence within the stack. We recommend that you add one or more hyphens (“-“) or underscores (“­_”) after the end of the file name so that the appended number sequence is visually spaced from the sample name. Find the directory for saving the modified stack—we recommend that you create a new folder in this directory and name it appropriately. Select “Open”, which will cause the stack to save.

If you do accidentally save your images in the same folder as another image stack, you should be able to separate them by clicking on the “Date modified” organizer in the window and sorting your files this way. 

#### Saving a stack as a video
In some instances, you may wish to provide a video that scrolls through your dataset. To do this, select File>Save as>AVI… from the menu bar. Select compression options if desired. Choose frame rate (note, all frames will be saved, but the total time length of the video will be determined by number of slices (frames) that are viewed per second when playing the video—7 is default; large numbers create shorter, faster videos; lower numbers create longer, slower videos). Click “OK”. Name the file as appropriate and choose the location for saving. Click “Save”.

#### Converting a DICOM to a TIFF stack in ImageJ
If the data you are working with are currently in DICOM format and you would like to convert them to a TIFF stack, you can easily do so in ImageJ. First, open an image sequence as you did in the instructions above; you will use the same options as with a TIFF stack. If you view the properties for your imported DICOM file, you will see that the voxel information should be correctly scaled. We suggest you record the voxel information in a separate file so that you have these data handy if you need to scale your TIFF stack later. Then follow the directions for saving an image stack above; make sure to select the TIFF file format option. 


### Opening and processing your data in 3D Slicer
The program 3D Slicer is comprised of modules that have different functions. These modules are accessed in a drop-down menu on the top menu bar. The most commonly used modules should be easily visible; others will be in subfolders. If you cannot find a module, you can always search for it using the little magnifying glass icon next to the drop-down menu. We recommend that you at least briefly familiarize yourself with the 3D Slicer interface by visiting https://slicer.readthedocs.io/en/latest/user_guide/user_interface.html 

#### Loading your data into 3D Slicer
3D Slicer can work with both TIFF stacks and DICOM files but the process to open each is slightly different. 

To open a DICOM file click the “Load DICOM Data” icon on the Welcome screen. Then select the button on the left hand side of the screen that says “Import DICOM files”. Navigate to the folder where your files are stored but do not enter the folder. Click on the folder and then “Import” (as with ImageJ we recommend that all files for an image stack be in a single folder, without any other files in that folder). You will now see files loaded into your DICOM database. Click on the file you wish to load in the “Patient name” section and then select “Load” at the bottom of the screen. 

To open a TIFF stack, you will use the “ImageStacks” Module. Click on the magnifying glass next to Modules on the top menu, search for ImageStacks,  and then select the “Switch to module” button at the bottom. Click on the “Browse…” button and navigate to the dataset you want to load and click “Open”. At this point your data are not yet loaded, but you should now see the size and spacing information for your data listed in the left hand menu. Double-check the given spacing against the known voxel size that should be reported in your sample’s metadata (all three spacing values should be the same number). If your datastack is >2GB, you might need to downsample the image before fully loading the image stack. In other words, you are going to make the voxels bigger to make the overall data smaller and easier to handle. This can be done in the same screen by selecting "half resolution," which will effectively double your voxel size. Take note of the new output spacing for measurement and reporting purposes. Click "Load files." 

Opening a surface model is even more straightforward. The simplest option is to click and drag your surface model (typically a .ply or .stl file) into the viewer window. Alternatively, click the “Load Data” button on the Welcome screen, select “Choose File(s) to Add” in the pop up window, and then click “OK”. 

#### Viewing your data
You should now see three orthogonal views of your object on the bottom of the screen (red, green, and yellow views), but no 3D representation in the top viewer. To show a 3D volume, use the magnifying glass tool to locate and navigate to the Volume Rendering module. In this module’s tool bar on the left-hand side you will see a line that says “Volume” with an eye symbol next to it. Click on the eye (it should open) and you will then see a staticky-looking box in the 3D window (you may need to zoom out or rotate in this view). Under Display, slide the Shift slider over until the box resolves into something that looks like your object. This tool is essentially changing the grayscale values that are and are not visible in the 3D view. You can rotate and translate your object by left clicking and dragging on the 3D representation, and clicking and dragging the scroll wheel. Zoom in using the scroll wheel. You can also use the mouse wheel to quickly scroll through your orthogonal views on the bottom of the screen. If you hold Ctrl while scrolling, the view will zoom in and out. Play around with this.

In the top left hand corner of the 3D viewer, you will see a couple of small buttons; these are the 3D viewer display options (Figure 1-2). Play around with these options as well to change your background color, turn on/off axis labels, or set the viewpoint direction. 


#### Saving your new image stack
To save your new volume, Click the SAVE button in the toolbar of the 3D Slicer screen. Use the Change directory for selected files button to navigate to your SPARC data. Create a new folder to store all the various files that might get associated with the project. We recommend creating a new folder named something like “3D Slicer files” in the folder where your SPARC data are stored (do not save this in the same folder that your image stack is in). There will be at least three files for you to save: a volume NNRD file, a segmentation NNRD file, and a scene MRML file. There will likely be other files that need to be saved; just make sure they are all in the same directory. It might take a second for all of these files to save. Once these are saved and you close 3D Slicer, you can easily pick up where you left off by opening the MRML file again in 3D Slicer. 



