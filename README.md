# sparc_microct

This repository contains teaching materials designed to introduce university-level students to working with computed tomography (CT) data. It introduces terminology and metadata specific to CT scanning and data analysis and provides step-by-step instructions for four exercises that cover the basics of processing and interpreting CT data collected through the SPARC Project and/or at the MicroCT Imaging Consortium for Research and Outreach (MICRO) facility at the University of Arkansas. 

Portions of this exercise are adapted from: Kasten, M. (2020) Delving into the Boston Fingerprints Project Archive: A SPARC Teaching Resource. https://github.com/ropitz/sparc_teaching.  

Please cite this exercise as Claxton, A.G., Wilson, M., Terhune, C. (2022) Exploring microCT Applications in Archaeology: A SPARC Teaching Resource. 

[a relative link](exercise 1.md)


### **Introduction, Aims, and Learning Outcomes**
The use of computed tomography (CT) imaging in archaeological investigations has been an area of considerable growth in the last several decades. Archaeological applications of CT imaging can be broadly grouped into seven categories: digital autopsies of preserved human or animal remains, documentation of paleopathological conditions and/or trauma, virtually unfurling and reconstructing ancient scrolls or texts, examination of the contents of sealed vessels (e.g., ceramics or basketry), identification of raw materials used in artifact manufacture and/or the reconstruction of manufacturing techniques, archaeobotanical and/or microsedimentological analysis, and the documentation and verification of cultural heritage objects. You can learn more about the variety of archaeological applications of CT imaging here and here. 

Many of these applications have specifically utilized micro-computed tomography (i.e., microCT) imaging, which enables the visualization of structures in much greater detail than clinical or industrial CT scanning. CT and microCT imaging are particularly valuable because these techniques allow for the three-dimensional (3D) examination of both the external and internal structure of an object without damaging the object itself. 

In this lesson you will: 
Understand what microCT data is and how to download and store this data
Open and visualize microCT data
Interpret microCT data
Collect measurements from microCT data
Generate 3D models from microCT data

When you have completed this lesson you will be able to:
Understand how to download, visualize, and process microCT data
Become familiar with free open-source programs for visualizing and manipulating microCT data and 3D models
Understand the range of applications of microCT in archaeological investigations

### **Outputs**
As you work through these exercises, we encourage you to take notes and/or screenshots of your progress. This could be as simple as a Word document where you have pasted the screenshot or something more; that is up to you. After each exercise, you may want to reflect on the exercise and summarize your thoughts in a few sentences as a 'long caption' for your screenshot(s). This “guide” may be especially helpful if you are new to these methods or programs and hope to use them again in the future. 

### **Feedback**
Should you identify any errors with this tutorial or have any problems, please feel free to reach out to us at micro@uark.edu. 

## **BACKGROUND**

### Principles of CT Imaging
CT imaging relies on the same principles as x-ray imaging. However, while an x-ray you might get for a broken bone shows a two-dimensional (2D) image, the goal of CT imaging is to create a volumetric rendering of a 3D object. This means that a series of 2D x-ray projections (radiographs) are algorithmically combined to create a series of cross-sectional slices that, when stacked in order, provide a 3D image of the internal and external structure of an object. These 3D images are made up of many cubic volume elements called voxels (Figure 0-1). The smaller the voxel size, the better the resolution of the scan and the more easily smaller structures can be detected. 

Three basic structures are common to all x-ray and CT imaging equipment: the x-ray source, sample stage, and detector (Figure 0-2).  The object, sample, or item of interest is placed on the stage, which is situated between the x-ray source and the detector; as x-rays are produced, differences in the density of the materials being imaged attenuate (or stop) some x-rays from fully passing through the object, and those x-rays that remain are picked up by the detector, which essentially acts as digital x-ray film. The more dense a material the more likely it is to stop some or all x-rays from passing through it. 

CT imaging comes in all shapes and sizes. Many people will be familiar with clinical CT scanning, where an individual lays on a gantry (stage) and the x-ray source and detector rotate around the person or anatomical region being investigated. Clinical CT imaging usually has a resolution of around 1000 microns (or 1mm). In contrast, microCT imaging can produce datasets with resolutions between 1-100 microns. In other words, microCT imaging can produce image stacks with much smaller voxel sizes, which increases the ability of those scans to detect small structures. As a general rule of thumb, your voxel size should be between two to three times smaller than the detail of an object you are interested in visualizing (for example, for a 50 micron structure voxel sizes should be at least ~25 microns). 

However, much of the resolution of a particular scan depends on the size of the object being scanned and the equipment in use. MicroCT systems can be small and tabletop, medium to large cabinet-sized systems, or can be walk-in systems. Each of these different set-ups has its strengths and weaknesses. In contrast to clinical CT where the x-ray source and detector are rotated around the patient, most microCT systems operate with the object placed on a rotating stage that is situated between the x-ray source and detector. This stage can often be manipulated to best place the object in the path of the x-ray beam. During scanning, a hot filament (similar to a light bulb) generates an electron beam that is focused by a magnetic lens; these electrons then hit a target, where most of the energy of the electrons is dissipated as heat, and a small amount produce x-rays. These x-rays can have a variety of energies and properties, depending on the material that the target is made of and the energy (kilovolts [kV]) applied to the filament. Many microCT systems have a cone-beam design, meaning that after hitting the target the x-rays form a cone with the narrowest point at the target and the base of the cone at the detector. X-rays travel in a straight line via this cone and through the object of interest, and ultimately hit the detector. Variation in the density of the object is reflected on the detector through the generation of a histogram, which depicts the frequency of grayscale levels recorded in a given projection (or ultimately in the entire image stack). 

### Scan Parameters
A number of different scan parameters can typically be adjusted to produce the desired scan resolution, though some of these parameters will vary depending on the equipment in use. When reporting the results of analyses including CT data, multiple of these parameters should be included. Minimally this should include the system the scans were made on, the kV and microamps of the scan, the number of projections, and the voxel size of the reconstructed data. You may also wish to report exposure length, whether projection frames were averaged, if a minimize ring artifacts correction was employed while scanning, and whether a filter was used (and if so, the material and thickness of the filter).  

Some of these parameters include:

* Beam energy
  * Measured in kilovolts (kV)
  * Represents changes in the wavelength of the majority of the x-rays being produced; higher energies have shorter wavelengths (“hard” x-rays) and lower energies have longer wavelengths (“soft” x-rays). Higher energy x-rays are able to penetrate more dense materials. 
  * The beam energy is used to adjust how effectively a material is being penetrated by the x-rays

* Beam current
  * Microamps (μA) (not to be confused with milliamps= mA)
  * Represents the amount of electrons being produced by the filament
  * The beam current is used to adjust the image brightness (which represents how many x-rays are getting to the detector; i.e., flux)

* Geometric magnification
  * Measured as the source to detector distance divided by the source to sample distance (Figure 0-3). Objects positioned closer to the x-ray source will have higher geometric magnification (i.e., the “shadow” of the object will fully fill the detector panel). Moving the object closer to the x-ray source will also decrease the effective pixel size. 

* Effective pixel size (i.e., resolution)
  * Calculated using geometric magnification and the pixel size of the detector (which is fixed). For example, if the pixel size of the detector is 0.200 mm (as is the case for MICRO), and geometric magnification is 51, then effective pixel size is calculated as detector pixel size divided by geometric magnification (0.2/51= 0.003922 mm or 3.922 microns) (Figure 0-4). 

* Power
  * = current * energy; measured in watts (W)
  * Typically the power should be less than or equal to the effective pixel size; this will verify that the dominant factor in the defining resolution is the geometric magnification. 

* Exposure length
  * A measurement of the elapsed amount of time per projection. 
  * Where possible it is better to increase the exposure length. Longer exposures will allow for decreased power and noise during scanning, but will increase the total length of the scan. 

* Projections
  * The total number of images that will be produced during the length of the scan. Typically, more projections will increase scan quality as it is more likely to capture the entirety of the data. In other words, if projections are separated by too large of an angle then there will be missing data. 

* Frame averaging (aka frames per projection)
  * Helps increase the quality of the scan and decrease noise, since this essentially means that two or more duplicate projections are being averaged across the length of the scan. However, this option will also increase the length of the scan (e.g., 4 frames= 4x original scan length). 

* Filters
  * Filters may be added to the x-ray source for two reasons: 1) optimization of image gray levels and/or 2) reduce beam-hardening effects. Filters are simply pieces of metal in a variety of different thicknesses (e.g., 1 mm, 2 mm) and materials (e.g., copper, tin). The effect of using a filter is that the average energy of the x-ray beam is increased and lower energy x-rays are removed (for example, x-rays that may not have enough energy to penetrate the object). As a result of using filters, the minimum gray values will be increased (erasing lighter materials), but this will also provide better penetration for more dense materials. 


