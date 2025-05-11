

## City Location Identification from Satellite Images

**Technologies Used:** Python, OpenCV, K-Means Clustering
**Date:** April 2024

### Project Description

This project explores how urban areas can be detected from grayscale satellite images by analyzing pixel intensity patterns. The method is based on the assumption that urban structures appear as brighter regions in such imagery due to higher reflectance.

### What It Does

* Uses OpenCV to process and threshold grayscale satellite images, identifying bright pixel regions as potential city areas.
* Applies K-Means clustering (with the Elbow Method) to group spatially coherent urban zones.
* Calculates distances between cluster centroids to understand the spread and separation of urban regions.
* Outputs a clustered visualization of the image showing segmented urban-like regions.

### Highlights

* Simplified approach to region segmentation using only pixel intensity and clustering.
* Fully notebook-based implementation, easy to follow and customize.
* Compatible with different image resolutions and formats.

### How to Run

To run the notebook locally:

```bash
git clone https://github.com/yourusername/CityClustering.git
cd CityClustering
pip install opencv-python numpy matplotlib scikit-learn
jupyter notebook Clustering.ipynb
```

Then:

1. Upload or use one of the provided satellite images (e.g., `1.png`, `2.png`).
2. Run through the notebook cells step by step.
3. Visualize clustered urban regions.

### Project Structure

```
├── 1.png, 2.png, ...       # Sample satellite images
├── Clustering.ipynb        # Main notebook with implementation and output
├── Untitled.ipynb          # Scratch/unused notebook
├── README.md               # Project documentation
```


