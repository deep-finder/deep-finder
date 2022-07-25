[THIS IS CURRENTLY ONLY A FORK OF [deep-finder](https://gitlab.inria.fr/serpico/deep-finder) DEDICATED TO [napari-deepinder](https://github.com/deep-finder/napari-deepfinder)]

# Deep Finder

The code in this repository is described in [this pre-print](https://www.biorxiv.org/content/10.1101/2020.04.15.042747v1). This paper has been submitted to Nature Methods and has now been [published](https://doi.org/10.1038/s41592-021-01275-4).

__To reviewers__: you can follow our [tutorial](https://deepfinder.readthedocs.io/en/latest/tutorial.html) to reproduce segmentations from our paper.

__Disclaimer:__ DeepFinder is still in its early stages, any feedback is welcome for enhancing the user experience.

__News__: (29/01/20) A first version of the GUI is now available in folder pyqt/. [More information...](###Using the GUI) 

__News__: (01/06/22) A first version of the [Napari](https://napari.org) GUI (Napari plugin) is available here: https://github.com/deep-finder/napari-deepfinder.

## Contents
- [System requirements](##System requirements)
- [Installation guide](##Installation guide)
- [Instructions for use](##Instructions for use)
- [Documentation](https://deepfinder.readthedocs.io/en/latest/)
- [Google group](https://groups.google.com/g/deepfinder)

## System requirements
__Deep Finder__ has been implemented using __Python 3__ (_Python >= 3.8 is required_) and is based on the __Keras__ package. It has been tested on Linux (Debian 10), and should also work on Mac OSX as well as Windows.

The algorithm needs an __Nvidia GPU__ and __CUDA__ to run at reasonable speed (in particular for training). The present code has been tested on Tesla K80 and M40 GPUs. For running on other GPUs, some parameter values (e.g. patch and batch sizes) may need to be changed to adapt to available memory.

```diff
- If above conditions are not met, we cannot guarantee the functionality of our code at this time.
```

### Package dependencies
Deep Finder depends on following packages. The package versions for which our software has been tested are displayed in brackets:
```
tensorflow     (2.8.2)
keras          (2.8.0)
h5py           (3.6.0)
lxml           (4.8.0)
mrcfile        (1.3.0)
scikit-learn   (1.0.2)     
scikit-image   (0.19.2)  
matplotlib     (3.5.2)
PyQt5          (5.15.6)
pyqtgraph      (0.12.4)
openpyxl       (3.0.9)
scipy          (1.7.3)
numpy
pycm
```


## Installation guide
Before installation, you need a python environment on your machine. If this is not the case, we advise installing [Miniconda](https://docs.conda.io/en/latest/miniconda.html).

### NEW easy installation process
In your python environment, do:
```
pip install deepfinder_em
```

### Legacy installation method
You need to download the present repository. Next, open a terminal, place yourself in your deep-finder folder and run:
```
cd /path/to/deep-finder/
pip install -r requirements.txt
```
Also, in order for Keras to work with your Nvidia GPU, you need to install CUDA. For more details about installing Keras and CUDA, please see [Keras installation instructions](https://keras.io/#installation).

Once these steps have been achieved, the user should be able to run Deep Finder.

## Instructions for use
### Using the scripts
Instructions for using Deep Finder are contained in folder examples/. The scripts contain comments on how the toolbox should be used. To run a script, first place yourself in its folder. For example, to run the target generation script:
```
cd examples/training/
python step1_generate_target.py
```

### Using the GUI
#### NEW GUI!
You can use a new GUI that has been developed for deepfinder as a [Napari](https://napari.org) plugin, you can find more information on https://github.com/deep-finder/napari-deepfinder.

#### New method (when downloaded and installed directly via pip)
6 different commands (GUIs) are available by directly typing the command in the python environment (`display`, `annotate`, `generate_target`, `train`, `segment`, `cluster`)
In your environment, write the following command for example to run the target generation GUI:
```generate_target```

#### Legacy method
The GUI (Graphical User Interface) is launchable from folder bin/, and should be more intuitive for those who are not used to work with script. Currently, 6 GUIs are available (tomogram display, tomogram annotation, target generation, training, segmentation, clustering) and allow the same functionalities as the scripts in example/. To run a GUI, first open a terminal. For example, to run the target generation GUI:
```
/path/to/deepfinder/bin/generate_target
```

![Training GUI](./images/gui_segment.png)


__Notes:__ 
- working examples are contained in examples/analyze/, where Deep Finder processes the test tomogram from the [SHREC'19 challenge](http://www2.projects.science.uu.nl/shrec/cryo-et/2019/). 
- The script in examples/training/ will fail because the training data is not included in this Gitlab. 
- The evaluation script (examples/analyze/step3_launch_evaluation.py) is the one used in SHREC'19, which needs additional packages (pathlib and pycm, can be installed with pip). The performance of Deep Finder has been evaluated by an independent group, and the result of this evaluation has been published in Gubins & al., "SHREC'19 track: Classification in cryo-electron tomograms".
