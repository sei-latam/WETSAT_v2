<h1 align="center">

  [![Typing SVG](https://readme-typing-svg.herokuapp.com?font=Fira+Code&size=20&pause=500&color=1D8CF7FF&center=true&vCenter=true&multiline=true&width=550&height=80&lines=Welcome+to+WetSAT-ML;By+Stockholm+Environment+Institute+(SEI))](https://git.io/typing-svg) 
</h1>

<div align="center">
<table>
<tr>
<!-- Imagen izquierda -->
<td>
<img src="https://github.com/CarlosMendez1997Sei/WETSAT/blob/main/WETSAT-ML_icon.png" alt="Logo WetSAT-ML" width="120">
</td>
<!-- Texto central -->
<td align="center" style="vertical-align: middle; padding-left: 18px; padding-right: 18px; text-align: center;">
<!-- Título en Markdown dentro del HTML -->
<h1 style="margin-bottom: 6px; text-align: center;">
WetSAT-ML Version 1.0
</h1>
<!-- Frase original abajo --> <span style="font-size: 18px;">
<strong>W</strong>etlands flooding <strong>e</strong>xtent and
<strong>t</strong>rends using <strong>SAT</strong>ellite data and
<strong>M</strong>achine <strong>L</strong>earning Version 1.0</span>
</td>
<!-- Imagen derecha -->
<td>
<img src="https://github.com/CarlosMendez1997Sei/WETSAT/blob/main/LOGO_SEI.png" alt="Logo SEI" width="120">
</td>
</tr>
</table>
</div>

# 🛰️ WetSAT-ML Version 1.0 Documentation

## General Summary

<h4 align="justify">
WetSAT-ML (Wetlands flooding extent and trends using SATellite data and Machine Learning) version 1.0, It consists of an open-source algorithm integrated with platforms such as: 
Google Earth Engine, <img src="https://images.icon-icons.com/1508/PNG/512/googleearth-engine_104576.png" alt="HTML" width="20" height="20"/>
Google Colab, <img src="https://uxwing.com/wp-content/themes/uxwing/download/brands-and-social-media/google-colab-icon.png" alt="HTML" width="20" height="20" />
and  Scikit Learn <img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="HTML" width="20" height="20" />
.The tool processes radar satellite data from the Sentinel-1 mission to generate wetland flooding extent maps, water permanence maps, and quantify key hydrological parameters, including flooded area time series, hydroperiods, and intra- and inter-annual wetland area trends. The algorithm will use machine learning models to characterize the scattering behavior of the radar signal for different wetland flooding conditions, enabling a pixel-level water detection in the satellite images.

<h2 align="left">
  
Master Script Code from Google Colab </a> <a href="https://colab.research.google.com/github/CarlosMendez1997Sei/WETSAT_v2/blob/main/2_Modelling_WETSAT_Google_Colab/Master_WETSAT.ipynb" target="_blank" rel="noreferrer"> 
<img width="20" height="20" alt="image" src="https://uxwing.com/wp-content/themes/uxwing/download/brands-and-social-media/google-colab-icon.png" />
</h2>
  
```html
https://colab.research.google.com/github/CarlosMendez1997Sei/WETSAT_v2/blob/main/2_Modelling_WETSAT_Google_Colab/Wetsat_Geoprocessing.ipynb
```


The tool WetSAT-ML allow users to:

- Generate wetland flooding extent maps.
- Produce water permanence maps.
- Extract flooded area time series.
- Quantify intra-annual and inter-annual wetland hydrological trends.

<div class="figure" style="text-align: left">
  
<p class="caption"> WetSAT-ML methodology workflow for generating wetland flooding extent and trends using Sentinel-1 data and machine learning.</p>

<img src="https://github.com/sei-latam/WETSAT_v2/blob/a252d357545534f72b7f2fd8fce593a733a47749/WetSAT_Design_Official.png" alt="Figure 1. WetSAT-ML methodology workflow for generating wetland flooding extent and trends using Sentinel-1 data and machine learning." width="100%"/>

</div>

## Repository Structure 📁

```html
WETSAT_v2/
├── 0_Original_Files/
│   ├── aoi1/
│   └── aoi2/
│       ├── sigma_dB/
│       │   ├── VH/
│       │   ├── VV/
│       │   └── PR_index/
│       └── points_AOI2_BDE.shp
├── models/
└── README.md
```
## (1.0) Installation of packages and libraries ⚙️

<h2 align="left">
  
![Static Badge](https://img.shields.io/badge/Google_Colab-darkorange) </a> <a href="https://colab.research.google.com/" target="_blank" rel="noreferrer"><img width="40" height="40" alt="image" src="https://uxwing.com/wp-content/themes/uxwing/download/brands-and-social-media/google-colab-icon.png" />
</h2>

```Python
###################################### Artificial Intelligence Frameworks #####################################################
!pip install scikit-learn
###################################### Data, Geoprocessing and Graphics libraries #####################################################
!pip install rasterio
!pip install matplotlib
!pip install numpy
!pip install contextily
!pip install geopandas

## Geoprocessing packages
import rasterio
from rasterio.features import rasterize
import numpy as np
import geopandas as gpd
import pandas as pd
import matplotlib.pyplot as plt
import matplotlib.colors as mcolors
import gc  # Garbage collector to free memory
import os
import contextily as ctx
from shapely.geometry import box
import seaborn as sns
import joblib
import urllib.request
import warnings
from google.colab import files
from google.colab import data_table
```

## (2.0) 🗺️ Images preparation (VV,VH and PR)
Input Data:
- VH and VV SAR images (.tif)
- Compute PR Index
```python
(PR = VH - VV)
```

## (3.0) 🗺️ Labels and Marks preparation
Input Data:
- Import shapefile points with labels and marks 
- Reproject shapefile to match raster CRS
- Filter points within raster bounds
- Extract pixel values at labeled points


## (4.0) Connect Google Colab/GitHub

### Option 1: Import manually Areas Of Interest (AOI) <img src="https://cdn-icons-png.flaticon.com/512/25/25231.png" alt="github" width="40" height="40"/> 
```html
https://github.com/sei-latam/WETSAT_v2/tree/main/0_Original_Files/aoi1
https://github.com/sei-latam/WETSAT_v2/tree/main/0_Original_Files/aoi2
```

### Option 2: Clone the repository of GitHub

HTTPS
```html
https://github.com/sei-latam/WETSAT_v2.git
```
GitHub SSH
```html
git@github.com:sei-latam/WETSAT_v2.git
```
GitHub CLI
```html
gh repo clone sei-latam/WETSAT_v2
```


<h2 align="left">
  
![Static Badge](https://img.shields.io/badge/ScikitLearn-blue) </a><a href="https://scikit-learn.org/" target="_blank" rel="noreferrer"><img src="https://upload.wikimedia.org/wikipedia/commons/0/05/Scikit_learn_logo_small.svg" alt="scikit_learn" width="40" height="40"/> 
</h2>

## (5.0) Import the Random Forest Model and dependences of Machine Learning 🧠

```Python
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import GridSearchCV
from sklearn.model_selection import train_test_split
from sklearn.metrics import classification_report, confusion_matrix, accuracy_score
from sklearn.impute import SimpleImputer
from sklearn.multioutput import MultiOutputClassifier
from sklearn.preprocessing import LabelEncoder
from sklearn.exceptions import UndefinedMetricWarning
from sklearn.base import BaseEstimator, TransformerMixin
from sklearn.pipeline import Pipeline
```

## (6.0) Prepare the Random Forest Model 🔠

- Prepare Training Data (70%)
- Prepare Validation Data (30%)
- Store Data in pickle (.pkl) formats, for example ----> joblib.dump(le, "/models/label_encoder.pkl")
- Display Data

## 7.0 and 8.0: Training Random Forest Model 🌲

- Train a Random Forest classifier with hyperparameter tuning:
- Save the best model in pickle (.pkl) format, for example ----> joblib.dump(best_model, "/models/modelo_random_forest.pkl")
```Python
param_grid = {
    'n_estimators': [100, 200],
    'max_depth': [10, 20, None],
    'min_samples_split': [2, 5],
    'min_samples_leaf': [1, 2],
    'max_features': ['sqrt', 'log2']
}
```

## 9.0 Evaluate the Random Forest Model 📊
- Accuracy score
- Best hyperparameters
- Confusion matrix
- Classification report

## 10.0 Classification Wetlands and Maps 🧪 (you can to classify actual or news AOI's)

- Import the pickle files previously created (model, encoders and labels)
- Add news images (VV, VH and PR), if you don't have PR index, you can to recalculate the PR index following the equation (PR = VH - VV)
- Upload the model and make predictions


## 11.0 and 12.0 Transform predicted values (categorical and numerical) to legend and export images

- Use encoder label to transform values (optional) 📌
- Export to raster (.tif) images in AOI selected, for example -----> Classification_labels_XX.tif
- Open the raster images predicted in Open Source GIS, for example QGIS

</h4>

## Versions and releases

Version in `R`

```HTML
https://github.com/sei-latam/WETSAT
```

Version `1.0`

```HTML
https://github.com/sei-latam/WETSAT_v2
```

## Citations and References

For WetSAT-ML citations and references, please use the following structure:

Palomino-Ángel, S., Méndez, C., Zamora, D., Santos, T., Prasad, S., and Piman, T. (2025). WetSAT-ML: Wetlands flooding extent and trends using SATellite data and Machine Learning (Version 1.0) [Data System]. Stockholm Environment Institute (SEI). 
https://github.com/sei-latam/WETSAT_v2.

## License

GNU AFFERO GENERAL PUBLIC LICENSE
Version 3, 19 November 2007

Copyright (C) 2007 Free Software Foundation, Inc. <https://fsf.org/>
Everyone is permitted to copy and distribute verbatim copies
of this license document, but changing it is not allowed.

