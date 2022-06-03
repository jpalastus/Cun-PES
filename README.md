# Cun-PES
Code sharing repository associated with the manuscript *Theoretical Framework based on Molecular Dynamics and Data Mining Analyses to the Study of the Potential Energy Surfaces of Finite-size Particles* (under submission and peer-reviewing process).

## Authors

João Paulo A. de Mendonça<sup>a</sup>, Tuanan C. Lourenço<sup>a</sup>, Felipe V. Calderan<sup>b</sup>, Marcos G. Quiles<sup>b</sup>, Juarez L. F. Da Silva<sup>a</sup>

<sup> a </sup>*São Carlos Institute of Chemistry, University of São Paulo, P.O. Box 780, 13560-970, São Carlos, SP, Brazil*
<sup> b </sup>*Institute of Science and Technology, Federal University of São Paulo, São José Dos Campos, SP, Brazil*

## Manuscript Abstract

*Nanoclusters are remarkably promising for the capture and activation of small molecules for fuel production or for the use as a precursor for other chemicals of high commercial value. Since this process occurs under a wide variety of experimental conditions, full comprehension of the stability and phase transitions that these systems can undergo is detrimental to the development of successful technological applications. In this work, we proposed a theoretical framework to explore the potential energy surface and configuration space of nanoclusters to map the most important morphologies presented by those systems and the phase transitions between them. To do so, a fully automated process was developed that combined global optimization techniques, classical molecular dynamics, and unsupervised machine learning. To showcase these capabilities of the approach, we explored the example of copper nanoclusters Cu_n where n = 13, 38, 55, 75, 98, 102, 147. We not only reported a graphical potential energy surface for each size, but also explored the topology of the configurations space via structural and thermodynamic analysis. The effect of size on the PES and the critical temperature for solid-liquid phase transitions was also reported, highlighting the impact of magic numbers on those quantities.*

## Project Files

### 00_lmkmeans.py

**In the original context:** Use k-means with energy and silhouette criteria to cluster all local minima visited in BHMC process (obtained from GOTNANO inhouse global optimization code).

**I/O information:** Requires a strutured input composed of a folder of XYZ files and a 2 columns ASCII file with file names (column 0) and  respective Potential Energies (column 1).

### 01_tsne.py

**In the original oontext:** Apply t-SNE on MD data to plot a 2D projection of the data, potential energy surface and 2D density of samples estimation.

**I/O information:** Also requires the transformation of MD data in a struturizes repository of structures and energies, following the same format as the one for **00_lmkmeans.py**. This script also outputs XYZ coordinates, where X and Y are 2D coordinates of the t-SNE projection of the MD data and Z is the energy data.

### 02_treat_tsne.py

**In the original oontext:** Cluster t-SNE data with DBSCAN and remove the noise using kNN. This produces an output containing the id and label of each element, post-kNN and a treated t-SNE plot.

**I/O information:** This code is supposed to be run after **01_tsne.py**, using its inputs and outputs. 

### libs/xyz_files.py

Small set of tools to work with XYZ files to be imported in the other Python codes. 

### run.sh

Bash Script that executes all the necessary files. It runs over the consolidated input exemplified in **example_settings.ini**.

## Install dependencies

To install the necessary dependencies, execute:
```
pip3 install -r requirements.txt
```

## Run the program

When running the program for the first time, make sure that **run.sh** is executable with:
```
chmod +x run.sh
```

After configuring the program inside a **settings.ini** (see **example_settings.ini**) file, run:
```
./run.sh everything settings.ini
```
