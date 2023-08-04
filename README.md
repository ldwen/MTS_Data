# MTS datasets for anomaly detection. (With data feature annotation and anomaly type annotation)

In order to enhance research and development efforts, we have made the labeled datasets available, comprising of two
privately collected datasets from partner companies as well as six publicly accessible datasets.

## Datasets

Detailed information of the eight datasets is shown below.

|Dataset   | \#Entities | \#Metrics | \#Train | \#Test | Anomalies (\%) |
|----------|----------|----------|----------|-----------|----------|
|D1        | 26         | 49        | 14400   | 23040  | 0.05 |
|SMD       | 28         | 38        | 28479   | 28479  | 0.04 |
|ASD       | 12         | 19        | 8640    | 4320   | 0.05 |
|SMAP      | 54         | 25        | 2818    | 7331   | 0.13 |
|MSL       | 27         | 55        | 4308    | 6100   | 0.11 |
|SWaT      | 1          | 51        | 496800  | 449919 | 0.12 |
|WADI      | 1          | 123       | 1048571 | 172801 | 0.06 |

These datasets with anomaly labels can be downloaded
from [GoogleDrive](https://drive.google.com/drive/folders/1iHPTA3KpQ6SjhRnQO37d0pqXTMJ4L0Mx?usp=drive_link)

For each dataset, there is a ``XXX-train.json`` and a ``XXX-test.json``. For each file, the format is as follows:

| Key      | Values                                                                  |
|----------|-------------------------------------------------------------------------|
| 'data'   | a list of length ``#entities``, each item is ``#metrics * #timepoints`` |
|  'label' | a list of length ``#entities``,each item is `` #timepoints``            |

## Data Feature Annotation

We label three key features that influence the performance of anomaly detection algorithms: smoothness, periodicity,
and periodic metric pattern correlation. The annotation results are palced in ``DataFeatureAnnotation``. For each
dataset, the format is as follows:

| Entity  Index (omitted) | *_Periodicity_*  | *_Smoothness_* | _Metric\_Pattern\_Correlation_ |
|-------------------------|------------------|----------------|--------------------------------|
| 0                       | xx               | xx             | xx                             |
| 1                       | xx               | xx             | xx                             |
| ...                     | xx               | xx             | xx                             |
| n                       | xx               | xx             | xx                             |


## Anomaly Type Annotation
Based on existing research and empirical analysis,  we classify anomalies into six main types: global anomaly, contextual anomaly, pattern anomaly, frequency anomaly, trend anomaly, and others.
We code the each anomaly type into a integer:

| Anomaly type | Value |
|--------------|-------|
| Global       | 2     |
| Contextual   | 6     |
| Pattern      | 3     |
| Frequency    | 4     |
| Trend        | 5     |
| Others       | 1     |
The annotation results are palced in ``AnomalyTypeAnnotation``. 
The annotation of each dataset is stored as a JSON format file.
Each file is a contains #entities list, and each list is of length #timepoints.
For each time point, the value is the anomaly type of the corresponding time point and '0' denotes normal data.
