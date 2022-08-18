# Background

## Principles of CT Imaging
CT imaging relies on the same principles as x-ray imaging. However, while an x-ray you might get for a broken bone shows a two-dimensional (2D) image, the goal of CT imaging is to create a volumetric rendering of a 3D object. This means that a series of 2D x-ray projections (radiographs) are algorithmically combined to create a series of cross-sectional slices that, when stacked in order, provide a 3D image of the internal and external structure of an object. These 3D images are made up of many cubic volume elements called voxels (Figure 0-1). The smaller the voxel size, the better the resolution of the scan and the more easily smaller structures can be detected. 

![image](https://user-images.githubusercontent.com/90789390/184699581-953bde85-7af5-469b-9c58-1e755e3ff104.png)
###### Figure 0-1. False-color volume rendering of a ceramic vessel illustrating selected slices of the corresponding image stack, and a hypothetical rendering of three-dimensional voxels that make up the image stack (voxel illustration from https://commons.wikimedia.org/wiki/File:Voxels.svg). 

Three basic structures are common to all x-ray and CT imaging equipment: the x-ray source, sample stage, and detector (Figure 0-2).  The object, sample, or item of interest is placed on the stage, which is situated between the x-ray source and the detector; as x-rays are produced, differences in the density of the materials being imaged attenuate (or stop) some x-rays from fully passing through the object, and those x-rays that remain are picked up by the detector, which essentially acts as digital x-ray film. The more dense a material the more likely it is to stop some or all x-rays from passing through it. 

CT imaging comes in all shapes and sizes. Many people will be familiar with clinical CT scanning, where an individual lays on a gantry (stage) and the x-ray source and detector rotate around the person or anatomical region being investigated. Clinical CT imaging usually has a resolution of around 1000 microns (or 1mm). In contrast, microCT imaging can produce datasets with resolutions between 1-100 microns. In other words, microCT imaging can produce image stacks with much smaller voxel sizes, which increases the ability of those scans to detect small structures. As a general rule of thumb, your voxel size should be between two to three times smaller than the detail of an object you are interested in visualizing (for example, for a 50 micron structure voxel sizes should be at least ~25 microns). 

However, much of the resolution of a particular scan depends on the size of the object being scanned and the equipment in use. MicroCT systems can be small and tabletop, medium to large cabinet-sized systems, or can be walk-in systems. Each of these different set-ups has its strengths and weaknesses. In contrast to clinical CT where the x-ray source and detector are rotated around the patient, most microCT systems operate with the object placed on a rotating stage that is situated between the x-ray source and detector. This stage can often be manipulated to best place the object in the path of the x-ray beam. During scanning, a hot filament (similar to a light bulb) generates an electron beam that is focused by a magnetic lens; these electrons then hit a target, where most of the energy of the electrons is dissipated as heat, and a small amount produce x-rays. These x-rays can have a variety of energies and properties, depending on the material that the target is made of and the energy (kilovolts [kV]) applied to the filament. Many microCT systems have a cone-beam design, meaning that after hitting the target the x-rays form a cone with the narrowest point at the target and the base of the cone at the detector. X-rays travel in a straight line via this cone and through the object of interest, and ultimately hit the detector. Variation in the density of the object is reflected on the detector through the generation of a histogram, which depicts the frequency of grayscale levels recorded in a given projection (or ultimately in the entire image stack). 

![image](https://user-images.githubusercontent.com/90789390/184700053-4e4e754c-8b7d-4631-a8f9-e7bfa25c143f.png)
###### Figure 0-2. Generalized schematic of a microCT system. Image source: Nikon Metrology. 

### Scan Parameters
A number of different scan parameters can typically be adjusted to produce the desired scan resolution, though some of these parameters will vary depending on the equipment in use. When reporting the results of analyses including CT data, multiple of these parameters should be included. Minimally this should include the system the scans were made on, the kV and microamps of the scan, the number of projections, and the voxel size of the reconstructed data. You may also wish to report exposure length, whether projection frames were averaged, if a minimize ring artifacts correction was employed while scanning, and whether a filter was used (and if so, the material and thickness of the filter).  

Some of these parameters include:

#### Beam energy
<ul>
  <li>Measured in kilovolts (kV)</li>
  <li>Represents changes in the wavelength of the majority of the x-rays being produced; higher energies have shorter wavelengths (“hard” x-rays) and lower energies have longer wavelengths (“soft” x-rays). Higher energy x-rays are able to penetrate more dense materials. </li>
  <li>The beam energy is used to adjust how effectively a material is being penetrated by the x-rays</li>
</ul>

#### Beam current
<ul>
  <li>Microamps (μA) (not to be confused with milliamps= mA)</li>
  <li>Represents the amount of electrons being produced by the filament</li>
  <li>The beam current is used to adjust the image brightness (which represents how many x-rays are getting to the detector; i.e., flux)</li>
</ul>

#### Geometric magnification
<ul>
  <li>Measured as the source to detector distance divided by the source to sample distance (Figure 0-3). Objects positioned closer to the x-ray source will have higher geometric magnification (i.e., the “shadow” of the object will fully fill the detector panel). Moving the object closer to the x-ray source will also decrease the effective pixel size. </li>
</ul>

![image](https://user-images.githubusercontent.com/90789390/184700314-4ee5de35-6089-455d-a803-79ddf197a5f1.png)
###### Figure 0-3. Schematic diagram showing the relationship between the source to detector distance and the source to sample distance (i.e., geometric magnification). Image source: Nikon Metrology.

#### Effective pixel size (i.e., resolution)
<ul>
  <li>Calculated using geometric magnification and the pixel size of the detector (which is fixed). For example, if the pixel size of the detector is 0.200 mm (as is the case for MICRO), and geometric magnification is 51, then effective pixel size is calculated as detector pixel size divided by geometric magnification (0.2/51= 0.003922 mm or 3.922 microns) (Figure 0-4). </li>
</ul>

![image](https://user-images.githubusercontent.com/90789390/184700347-66c9b28e-6475-4e08-903d-dd0945d10953.png)
###### Figure 0-4. Schematic diagram illustrating effective pixel size. Image source: Nikon Metrology.

#### Power
<ul>
  <li>= current * energy; measured in watts (W)</li>
  <li>Typically the power should be less than or equal to the effective pixel size; this will verify that the dominant factor in the defining resolution is the geometric magnification.</li>
</ul>

#### Exposure length
<ul>
  <li>A measurement of the elapsed amount of time per projection. </li>
  <li>Where possible it is better to increase the exposure length. Longer exposures will allow for decreased power and noise during scanning, but will increase the total length of the scan. </li>
</ul>

#### Projections
<ul>
  <li>The total number of images that will be produced during the length of the scan. Typically, more projections will increase scan quality as it is more likely to capture the entirety of the data. In other words, if projections are separated by too large of an angle then there will be missing data.</li>
</ul>

#### Frame averaging (aka frames per projection)
<ul>
  <li>Helps increase the quality of the scan and decrease noise, since this essentially means that two or more duplicate projections are being averaged across the length of the scan. However, this option will also increase the length of the scan (e.g., 4 frames= 4x original scan length). </li>
</ul>

#### Filters
<ul>
  <li>Filters may be added to the x-ray source for two reasons: 1) optimization of image gray levels and/or 2) reduce beam-hardening effects. Filters are simply pieces of metal in a variety of different thicknesses (e.g., 1 mm, 2 mm) and materials (e.g., copper, tin). The effect of using a filter is that the average energy of the x-ray beam is increased and lower energy x-rays are removed (for example, x-rays that may not have enough energy to penetrate the object). As a result of using filters, the minimum gray values will be increased (erasing lighter materials), but this will also provide better penetration for more dense materials. </li>
</ul>

All of these parameters combine to maximize grayscale values picked up by the detector. This range of values is represented graphically by a histogram (Figure 0-5). 
<ul>
  <li>Min GV- represents the most dense material and indicates how well the sample is being penetrated by the X-ray beams </li>
  <li>Max GV- represents the least dense material (usually the image background </li>
</ul>

![image](https://user-images.githubusercontent.com/90789390/184700380-18c49bd1-df35-4775-9175-d6d465055057.png)
###### Figure 0-5. Example histogram showing the range and number of gray scale values for a given object. Image source: Nikon Metrology.

### 8-bit vs. 16 bit Data
The number of grayscale values that a system can detect is a function of its “bit depth” (Figure 0-6). For example, medical CT scanners typically capture density differences as 8-bit images. This is actually 256 shades of grayscale from pure white to pure black. A bit is a 0 or a 1, so there are two states, and the 8 refers to how many 0’s and 1’s can be used to represent a single grayscale value. Thus, 8-bit images have 2^8 number of grayscale represented between pure white and pure black, and 2^8 = 256. This means that all of the density differences in an object have to be binned into just 256 grayscale values. On the other hand, micro-CT scanners typically capture density differences as 16-bit, which is 2^16 = 65,536. This means that 16-bit scanners can bin the density differences on an object into 65,536 grayscale values between pure white and pure black. The higher the bit depth, the more density detail of an object that the detector can capture.

![image](https://user-images.githubusercontent.com/90789390/184700433-94e7becf-1c1b-408c-8fc8-c2de7e699284.png)
###### Figure 0-6. Relationship between bit depth and number of gray levels. Image source: Nikon Metrology.

### Data Reconstruction and Imaging Artifacts
Following CT acquisition, the raw images (or projections) must be processed to “reconstruct” the data. This is typically done in software linked to the equipment (in the case of UArk MICRO, CT Pro 3D from Nikon). This software algorithmically locates the center of rotation from the object and then reconstructs the data into a 3D volume. The reconstruction software can also help correct some image artifacts, or may be the first time imaging artifacts are identified. 

Common types of image artifacts in microCT include:
<ul>
  <li>Noisy data often results from scans that are conducted when the beam current is not high enough. This causes a grainy appearance to otherwise homogenous structures (e.g., air) and can make identifying boundaries between materials with different densities more challenging. </li>
  <li>Ring artifacts are visible as concentric rings around the axis of rotation of the object. These tend to be more common in more homogeneous materials. </li>
  <li>Beam hardening artifacts occur when lower energy x-rays produced by the x-ray beam are absorbed when first contacting the object being scanned. This causes the appearance of a more dense “shell” of the object, when in fact this is not the case. </li>
  <li>Streak (or extinction) artifacts where denser materials (e.g., metal) may cast a shadow behind them where x-rays were not able to penetrate the material. </li>
  <li>Motion artifacts, where the object may have moved during scanning, often causing a failure in the ability for the software to find the center of axis of rotation of the object. </li>
</ul>

### Data Formats and Metadata
Once collected and reconstructed, the data can be exported in several different formats, the most common of which are DICOM and TIFF stacks. Both of these data types have corresponding metadata, that typically describes the voxel size and other scan parameters (e.g., the parameters listed above). The primary difference between these two data types is that DICOM datasets encode the metadata within them, where TIFF stacks do not (and therefore parameters like voxel size must be manually adjusted in subsequent analyses). Most CT scans that will be used in this lesson will be TIFF stacks, which are simply a sequence of images in .tif format. These stacks can sometimes be very large and will require a computer with lots of RAM and computing power. A general rule of thumb is that, in order to open and analyze your data, you need at least 3-4 times the amount of memory as the size of the volume or image stack. Depending on what you are trying to do, you may need considerably more memory. 

### CT data that is already available
There are many CT or microCT datasets that are already freely available for use in education and/or research. The repository with the most data at present and that is specifically formatted for sharing image stacks and 3D models is MorphoSource. Other repositories include Zenodo or tDAR (the Digital Archaeological Record). Data may also be shared by authors in association with publications (i.e., as supplementary data). 

### Generating your own CT data
If no relevant data for your research question already exists (or is not publicly accessible), you may instead be interested in conducting your own scanning. CT facilities are widely available, though the equipment present at these facilities may be more or less applicable depending on your needs. You should reach out to facilities you might be interested in working with to ask about pricing and to discuss your scanning needs. 

Some microCT facilities found in the US include:
<ul>
  <li>University of Arkansas MICRO (https://micro.uark.edu/)</li>
  <li>University of Texas High-Resolution Computed Tomography Facility (https://www.ctlab.geo.utexas.edu/)</li>
  <li>Duke University High Resolution X-ray Computed Tomography Scanner (https://smif.pratt.duke.edu/node/153)</li>
  <li>University of Minnesota X-ray Computed Tomography Facility (https://xraylab.esci.umn.edu/)</li>
  <li>University of Colorado Boulder (https://www.colorado.edu/facility/mimic/x-ray-microscope-micronano-computed-tomography)</li>
</ul>

### Software
There is a wide variety of software programs that can process and/or analyze microCT data or 3D models generated from CT data. Some of these have considerable flexibility but can be costly, while others are free but may be limited in their analytical capabilities. You should check with your institution to see if you already have access to any of the proprietary software listed here. 

Programs that can process microCT data and/or 3D models
<ul>
  <li>FIJI (formerly known as ImageJ) https://imagej.net/software/fiji/ </li>
  <li>3D Slicer/ SlicerMorphhttps://www.slicer.org/ </li>
  <li>R https://cran.r-project.org/ </li>
  <li>DragonFly https://www.theobjects.com/dragonfly/index.html and https://www.theobjects.com/dragonfly/get-non-commercial-licensing-program.html </li>
  <li>Matlab https://www.mathworks.com/products/matlab.html </li>
  <li>Avizo https://www.thermofisher.com/us/en/home/electron-microscopy/products/software-em-3d-vis/avizo-software.html </li>
  <li>VGStudioMax https://www.volumegraphics.com/ </li>
  <li>Mimics https://www.materialise.com/en/medical/mimics-innovation-suite/mimics </li>
  <li>Meshlab https://www.meshlab.net/ </li>
  <li>Checkpoint https://www.stratovan.com/products/checkpoint </li>
</ul>


What programs do you need to download for this tutorial?
<ul>
  <li>FIJI (aka ImageJ) https://imagej.net/software/fiji/ </li>
  <li>3D Slicer https://www.slicer.org/ </li>
  <li>Meshlab https://www.meshlab.net/ </li>
</ul>

We will focus here on using freely available programs such as FIJI/ImageJ, 3D Slicer, and Meshlab. Make sure to download and install the latest stable release of all three of these programs to the computer you will use to complete this tutorial. For FIJI and 3D Slicer you will also need to install a couple of additional extensions. In the 3D Slicer program’s opening screen, click Install Slicer Extensions and search for and install “SlicerMorph.” Install the BoneJ plugin for FIJI. It can be found here: https://imagej.net/plugins/bonej.

The image stacks you will be using (see below) will be smaller, downsampled versions of the original datasets, which should allow these data to be processed on a computer outfitted with relatively standard hardware. However, please note that many microCT image stacks can be upwards of 3-5 GB in size; opening and processing these image stacks may require increased computer memory (we suggest at least 64 GB) and an enhanced graphics card. 

All three of these programs should function on both Mac and PC systems. Our examples below will be illustrated on a PC system. If you run into inconsistent and/or unexpected behaviors with any of these programs operating on a different system, we encourage you to visit the help pages/tutorials for the programs. 

We strongly recommend you have a three-button mouse: i.e., a mouse that has a left button, a right button, and a scroll wheel. Multiple programs will be considerably easier to use with a mouse than just a laptop touchpad. If you have access to one, a graphics tablet is also helpful, but not necessary.

### Example Datasets
This repository will use three distinct example datasets to step you through each of the tutorials on data visualization, processing, and analysis. For the first two example datasets we have provided both the full (16-bit) dataset and a downsampled (8-bit) dataset that will be much easier to work with; we also provide an already generated ply model for the bird-effigy whistling pot. In addition, for the second dataset (the ceramic sherd), we have provided a cropped region of interest (ROI) image stack that will be used in Exercise 4. For the third dataset (the human femur from a US Civil War amputation) a single 8-bit DICOM file is available for download. 
<ul>
  <li>The first dataset is of a whole pottery vessel, specifically a bird-effigy whistling pot (filename= Bird Effigy Whistling Pot). This vessel was recovered from the north coast of Peru and is associated with the Moche culture. It dates to approximately 500 - 750 B.C.E. This ceramic vessel is currently housed in the University of Arkansas Museum collections in Fayetteville, Arkansas. This microCT scan was generated by the MICRO facility at the University of Arkansas.</li>
  <li>The second dataset is a ceramic sherd that was recovered from the central area of the "Kansanshi Smelting Area" in the Copperbelt of northern Zambia and dates to the Early Iron Age Phase II (late 7th-9th centuries). This sherd is provided courtesy of Kate De Luna, Georgetown University, Washington, DC. You have the option to examine both the whole sherd, and a cropped volume of the sherd that will be used in Exercise 4. This microCT scan was generated by the MICRO facility at the University of Arkansas as part of a SPARC grant.</li>
  <li>The third dataset is an amputated Civil War Era human distal femur with a gunshot wound. This individual (a Confederate soldier) was injured at the Battle of Antietam on September 17, 1862 and treated by Union surgeons, with the distal femur amputated on October 8, 1862. This dataset is provided courtesy of the National Museum of Health and Medicine. </li>
</ul>

The whole pottery vessel and ceramic sherd datasets can both be downloaded from the MorphoSource Project titled UArk MICRO Example CT Scans. For each of these, the downloaded data will include a TIFF stack and associated metadata file. We encourage you to save each dataset and the associated metadata in a separate folder, all in a larger folder named something like “SPARC MicroCT Tutorial”. Make sure to extract the relevant files before starting the exercises. 

The human femur dataset can be downloaded here. To download this data you will have to click on “Request Download”. Please provide the following text in your request: I am requesting permission to use this data in association with the University of Arkansas SPARC MicroCT Tutorial. Once granted permission for download, this data will be provided in a DICOM data format. As with the TIFF stacks, save this dataset in a separate folder (you will need to extract the data before analysis). Metadata for this dataset will be encoded in the DICOM file itself, but we also encourage you to create a word or text document that includes the “File Object Details” listed on this item’s MorphoSource page. This should especially include the X, Y, Z pixel spacing and slice thickness, which represent the voxel size, and the number of images in the set (aka number of projections). If you cannot find these data on the MorphoSource page, make sure to click the “show more” option to expand the image properties. 

## Further Reading
For a more comprehensive overview of CT imaging and CT imaging artifacts, including the physics involved, you may wish to read the following:
* [CT Scan. (2022, April) In Wikipedia](https://en.wikipedia.org/wiki/CT_scan). 
* [Withers, P.J., Bouman, C.J., Carmignato, S., Cnudde, V., Grimaldi, D., Hagen, C.K., Maire, E., Manley, M., Du Plessis, A., & Stock, S.R. (2021). X-ray computed tomography. Nature Reviews Methods Primers 1, 18](https://doi.org/10.1038/s43586-021-00015-4). 
* [CT Artifacts. (2022, February) In Radiopaedia](https://radiopaedia.org/articles/ct-artifacts). 
* [Boas F.E. & Fleischmann, D. (2012). CT artifacts: causes and reduction techniques. Imaging in Medicine 4(2), 229-240](https://www.openaccessjournals.com/articles/ct-artifacts-causes-and-reduction-techniques.html). 
* [Barrett, J.F. & Keat, N. (2004). Artifacts in CT: Recognition and Avoidance. Radiographics 24(6), 1679-1691](https://pubs.rsna.org/doi/10.1148/rg.246045065).     

## Next Up
### [Exercise 1: Loading and visualizing your data](/exercise1final.md)
