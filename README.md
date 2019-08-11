# Perception Neuron motion files processing

*author: Ondrej Tupa*

Programming language: python

This repository documents **bvh** and **calc** files processing obtained from the Perception Neuron system.
 
There are codes focusing on data loading, preprocessing, processing and classification.

### Installation:

Clone this repository using git or download. <br/>

git clone link:<br/>
[https://github.com/onachija/PN.git]


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
/data/FEAT/<br/>

ORIGINAL FILES LOCATION:<br/>
BVH FILES in /data/PN chuze/<br/>
CALC FILES in /data/CALC/<br/>
Excel data overview in /data/PN chuze/ as _'PN chuze.xlsx'_



### Usage

1) load_bvh_files.ipynb:<br/>
load BVH file, transform BVH file to numpy file (_/data/PN chuze processed/_ - not used at this moment), get T_sampling
2) create/update_excel_data_overview.ipynb:<br/>
create / update _'/data/PN chuze/Overview.csv'_ + _'/data/PN chuze/PN ataxie.csv'_
3) read_calc_files.ipynb:<br/>
read all calc from _/data/CALC/_ folder and save useful **parts** based on the excel table to _/data/CALC_SEG/_ as csv files 
4) split2straight.ipynb:<br/>
read csv files from folder _/data/CALC_SEG_, check local extreme in x and y direction and save straight **segments** to _/data/CALC_STRAIGHT/_
5) straight_two_steps.ipynb<br/>
process all **segments** : check for local extreme in z-direction of corpus/left and right foot to find number of steps, 
create csv file with overview of segment start and end and number of steps in this **segment** as SEGMENTS.csv
6) Classifier_SVM.ipynb<br/>
first preliminary results