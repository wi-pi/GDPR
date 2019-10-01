# The Privacy Policy Landscape After The GDPR
This repository contains the datasets as well as most of the analysis code from a large scale study of privacy policies before and after the GDPR. 

The paper: [The Privacy Policy Landscape After the GDPR](https://arxiv.org/pdf/1809.08396.pdf)

## About the Code
The bulk of the analysis code is all located in `GDPR_ANALYSIS_MAIN.ipynb`. If you are not familiar with Jupyter Notebook files, then checkout [https://jupyter.org/index.html](https://jupyter.org/index.html). 
- Additionally, the analysis of the user study results is found in a Jupyter Notebook at `/user_study/results_analysis.ipynb`. 
  
The datasets are each organized a little differently, corresponding to their various applications in our study. Here is some in-depth explanation of the sets in the order of their use in the study.  
- `/raw_html`: Contains time-series of raw-html for our sets of _EU_ and _Global_ privacy policies. A  single policy's time-series (for example the policy was from the `EU` set and had pid `3362`) could be found at `/raw_html/EU/3362`. Each element of the timeseries is a directory with its name being the timestamp of the policy's snapshot. So `/raw_html/EU/3362/20160101142306` would hold the snapshot from January 1st, 2016 at 14:23:06 (the locale here is that of the __Wayback Machine__). To get the raw document of the element, traverse to the bottom directory and open the page.
- `/text_data`: Contains the time-series of text extracted from the `/raw_html` directory. A single policy's time-series of text data can be found at `/text_data/set/pid`. Thus, an example policy from the `EU` set with pid `655`  can be found at `/text_data/EU/655`. Each element is a text file with its name corresponding to the time the snapshot is taken, now condensed to just year and month, so `/text_data/EU/655/201612.txt` corresponds to December 2016. 
- `/polisis_outputs`: contains the output files of Polisis's privacy policy analysis for our analyzed policies. A single policy's post-GDPR analysis is located at `/polisis_outputs/set/post_data/pid.json`. Thus, an example policy from the `EU` set with pid `1205`  can be found at `/polisis_outputs/EU/post_data/1205.json`. 
- `/polisis_queries`: contains the 3 sets of query-scores explained in our study. To access all scores for a single set (_e.g._ the specificity scores for the EU set) open `/polisis_queries/specificity/EU.json`


## Running the code
The code can be conveniently run using the jupyter notebook `GDPR_ANALYSIS_MAIN.ipynb`. It has several sections corresponding to the sections in the paper.

### Loading the Spacy Language Model
In order to run the below command from the notebook
```
pv = PassiveVoice()
```
please download the appropriate model using the command 
```
python -m spacy download en_core_web_lg
``` 
before running the code. All other dependencies are listed in `requirements.txt`. 

## Citation
If you wish to use our dataset in your research, please cite our PETS 2020 paper.
```
@inproceedings{linden2020gdpr,
  title = {The Privacy Policy Landscape After the GDPR},
  author = {Thomas Linden and Rishabh Khandelwal and Hamza Harkous, and Kassem Fawaz},
  booktitle = {Privacy Enhancing Technologies 2020 (PETS 2020)},
  year = {2020}
}
```
