# City Clustering from Bright Image Pixels

A notebook demonstration that finds bright pixels in four small images, groups their coordinates with a custom K-means implementation, and marks the resulting cluster centers. The notebook calls these centers “cities”; they are **image-space estimates**, not verified geographic locations.

The project was created in April 2024. It includes two cluster-count approaches, elbow and silhouette, in the same notebook.

## Quick start

With Python and Jupyter installed, run from the repository root:

```bash
git clone https://github.com/kanchanpotdar/CityClustering.git
cd CityClustering
python -m pip install jupyter numpy Pillow matplotlib
jupyter notebook Clustering.ipynb
```

Open the notebook and run its cells **in order**. It reads `1.png` through `4.png` from the current working directory. The repository has no dependency lockfile; these packages are derived from the notebook imports, and the setup has not been tested in a fresh environment.

## What the notebook does

1. Converts each RGBA sample image to grayscale.
2. Selects bright pixels as `(row, column)` coordinates. The elbow section selects pixels equal to 255; the later silhouette section selects pixels above 200.
3. Runs a hand-written K-means routine on those coordinates. Initial centroids are random.
4. Chooses a cluster count up to 10. The first section plots within-cluster sum of squares and uses a second-difference heuristic for its elbow choice. The later section calculates a custom silhouette score and selects the highest-scoring count from 2 to 10.
5. Plots the source image with red crosses at cluster centers, prints center coordinates, and prints pairwise Euclidean distances between centers.

The two sections redefine some functions, so cell order matters. Their thresholds and selection rules differ; their results need not match. Random initialization can also change centers and selected counts between runs.

## Files

| Path | Role |
| --- | --- |
| [`Clustering.ipynb`](Clustering.ipynb) | Main notebook with elbow and silhouette workflows and saved example outputs. |
| [`1.png`](1.png), [`2.png`](2.png), [`3.png`](3.png), [`4.png`](4.png) | Four included 64×64 RGBA sample images. |
| [`Untitled.ipynb`](Untitled.ipynb) | Additional exploratory implementations. |
| [`Clustering-checkpoint.ipynb`](Clustering-checkpoint.ipynb), [`Untitled-checkpoint.ipynb`](Untitled-checkpoint.ipynb) | Committed notebook checkpoints. |
| [`python-what-a-variable-is/`](python-what-a-variable-is/) | Separate Python exercise, unrelated to the image clustering workflow. |

## Interpreting the results

Center coordinates use image rows and columns; the plotted horizontal position is the **column**, and the vertical position is the **row**. Pairwise distances are measured in **pixels**, not kilometers. The charts and printed matrices are produced inside the notebook; it does not write a result file.

The committed notebook contains saved runs, but there is no labeled city-location dataset, accuracy measure, or comparison against geographic ground truth. Bright-pixel clustering alone cannot confirm that a cluster corresponds to an urban area. The included images are small examples; behavior on other imagery has not been established here.

## Limitations

- Input paths, thresholds, and the maximum cluster count are hard-coded in notebook cells.
- K-means requires enough selected pixels for the requested number of clusters; blank or low-brightness images may fail.
- The custom implementations do not fix a random seed or provide an automated test suite.
- The notebook is an experiment, not a geospatial pipeline or a packaged API.
