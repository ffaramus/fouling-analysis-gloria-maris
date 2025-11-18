# Net Fouling Analysis in Marine Aquaculture  
### Image Processing Algorithm (Python – OpenCV)  
*Stage Gloria Maris Groupe, 2024 – François Faramus*

This repository contains a Python implementation of an image-processing pipeline designed to **quantify biological fouling on aquaculture nets** from underwater photographs.  
The work was carried out during a 3-month engineering internship at **Gloria Maris Groupe (Acquadea)**, a major Mediterranean marine fish farming company.

The objective was to reproduce and adapt the methodology from *Qiu et al. (2020) – Net Health State Estimation (NHSE)* and to build a functional tool capable of processing real farm images.

---

## Objective

Develop a reproducible workflow able to:

- Correct underwater image distortions  
- Enhance image clarity (dehazing)
- Segment biofouling areas  
- Detect and approximate the mesh grid  
- Estimate the **percentage of blocked net surface**  

The final output provides a synthetic visual + numerical summary of the analysed net section.

---

## Project Structure

fouling-analysis/
│
├── fouling_analysis.py          # Main analysis script (OpenCV)
├── rapport_stage_2A.pdf         # Full internship report (French)
└── README.md                    

---

## Methods & Algorithm

The algorithm follows the 6-step NHSE pipeline:

1. **User selection of region of interest (ROI)**  
2. **Perspective correction** (rectification of the selected mesh section)  
3. **Underwater image dehazing** (HSV channel enhancement)  
4. **K-means segmentation** of fouling vs. net vs. openings  
5. **Mesh structure detection**  
   - binary mask creation  
   - morphological operations (erosion/dilation)  
   - contour extraction  
   - bounding box approximation  
6. **Coverage estimation**  
   - local percentage per mesh  
   - mean blockage value  

The implementation is based mainly on **OpenCV**, **NumPy**, and classical image-processing techniques.

---

## Results

The algorithm was tested on **48 underwater images** from nets with different mesh sizes, materials (nylon, Dyneema), and fouling levels.

Good robustness to:  
- reflections  
- heterogeneous lighting  
- color variations of biofouling  
- curved net structures  

Limitations identified:  
- fish close to the net can be misclassified as fouling  
- very heavily fouled nets break the assumption of “at least one clean mesh”  
- strong water color gradients reduce segmentation accuracy  

These limitations and improvement paths are detailed in the report.

---
## Report

The full internship report (in French) describing the context, methods, tests and limitations is available here:

`rapport_stage_gloriamaris.pdf`

---

## Author

**François Faramus**  
AgroParisTech – Bioinformatics & Machine Learning  
📧 francois.faramus@agroparistech.fr  
GitHub: *your link here*

