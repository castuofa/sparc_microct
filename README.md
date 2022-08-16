# sparc_microct

This repository contains teaching materials designed to introduce university-level students to working with computed tomography (CT) data. It introduces terminology and metadata specific to CT scanning and data analysis and provides step-by-step instructions for four exercises that cover the basics of processing and interpreting CT data collected through the SPARC Project and/or at the MicroCT Imaging Consortium for Research and Outreach (MICRO) facility at the University of Arkansas. 

Portions of this exercise are adapted from: Kasten, M. (2020) Delving into the Boston Fingerprints Project Archive: A SPARC Teaching Resource. https://github.com/ropitz/sparc_teaching.  

Please cite this exercise as Claxton, A.G., Wilson, M., Terhune, C. (2022) Exploring microCT Applications in Archaeology: A SPARC Teaching Resource. 


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




