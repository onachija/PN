# Perception Neuron motion files processing

*author: Ondrej Tupa*

Programming language: python

This repository documents **bvh** and **calc** files processing obtained from the Perception Neuron system.
 
There are codes focusing on data loading, preprocessing, processing and classification.

### Installation:

Clone this repository or download. <br/>

<code>git clone https://github.com/onachija/PN.git</code>


### Data:

Due to medical data sensitivity not shareable...<br/>

Folder structure:<br/>
/bin<br/>
/notebooks<br/>
/data<br/>
<br/>
/data/PN chuze/<br/>
/data/PN chuze_processed/<br/>
/data/CALC/<br/>
/data/CALC_SEG/<br/>
/data/CALC_STRAIGHT/<br/>
/data/CALC_STRAIGHT_CLEAN/<br/>
/data/FEAT/<br/>

ORIGINAL FILES LOCATION:<br/>
BVH FILES in /data/PN chuze/<br/>
CALC FILES in /data/CALC/<br/>
Excel data overview in /data/PN chuze/ as _'PN chuze.xlsx'_



### Usage

#### DATA INPUT
1) load_bvh_files.ipynb:<br/>
load BVH file, transform BVH file to numpy file (_/data/PN chuze processed/_ - not used at this moment), get T_sampling
2) create/update_excel_data_overview.ipynb:<br/>
create / update _'/data/PN chuze/Overview.csv'_ + _'/data/PN chuze/PN ataxie.csv'_
3) read_calc_files.ipynb:<br/>
read all calc from _/data/CALC/_ folder and save useful **parts** based on the excel table to _/data/CALC_SEG/_ as csv files

#### PREPROCESSING 
4) split2straight.ipynb:<br/>
read csv files from folder _/data/CALC_SEG_, check local extreme in x and y direction and save straight **segments** to _/data/CALC_STRAIGHT/_
5) straight_contact_clean.ipynb 
read csv files from folder _/data/CALC_STRAIGHT_, check min and max step duration [0.2 s < step < 2 s] and save straight clean **segments** to _/data/CALC_STRAIGHT_CLEAN/_

#### FEATURE EXTRACTION
6) straight_two_steps.ipynb<br/>
process all **segments** in _/data/CALC_STRAIGHT_CLEAN/_ : check for local extreme in z-direction of corpus/left and right foot to find number of steps, | NOW: using contactL and cotnactR only.| 
Create csv file with File, IndexStart, IndexEnd, SegLen, TimeLen, StepsR/L, StepFreqR/L, Direction etc. to _data/STRAIGHT_STEP_FREQ_CLEAN.csv_
7) features_from_steps.ipynb <br/>
process all **segments** in _/data/CALC_STRAIGHT_CLEAN/_ and use STRAIGHT_STEP_FREQ_CLEAN.csv to create
_data/FEATURES.csv_
8) features_in_energy_bands.ipynb add energy to _FEATURES.csv_

#### CLASSIFICATION
9) data_overview_simple_classifier_SVM:<br/>preliminary classification on detected steps using step frequency only
10) dim_reduction_and_classification.ipynb:<br/> multiple techniques of dimensionality reduction and classification on _data/FEATURES.csv_


#### GRID-SEARCH + CROSS-VALIDATION
11) classiffication_cross_validation.ipynb::<br/> grid search and few cross-validation methods for multiple classifiers, input:_data/FEATURES.csv_
