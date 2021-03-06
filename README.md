# The Privacy Policy Landscape After The GDPR

This repository contains the datasets as well as most of the analysis code from the large scale study of privacy policies before and after the GDPR.

The paper: [The Privacy Policy Landscape After the GDPR](https://arxiv.org/pdf/1809.08396.pdf)

[Data Download Link](https://uwmadison.box.com/s/v6girx83x0krai1k45vnn41w21brn4hi)

## Environment Setup

### Virtual environment Setup via Anaconda

[Anaconda](https://www.anaconda.com/) is a scientific Python installation which ships with various packages. Anaconda works on most systems without root access. It can be installed by following [instructions](https://docs.anaconda.com/anaconda/install/) provided in the docs.

To setup a working virtual environment, pleasee follow the instructions given below:

``` bash
  conda create -n gdpr_analysis python=3.7.1
  conda activate gdpr_analysis
  conda env update --file  environment_gdpr.yml
```

This installs and sets up all the components needed for the analysis. To open the jupyter notebook, execute `jupyter notebook` from the terminal which will open a new browser tab. If you are not familiar with Jupyter Notebook files, then checkout [https://jupyter.org/index.html](https://jupyter.org/index.html).

### Loading the Spacy Language Model

In order to run the below command from the notebook

```python
pv = PassiveVoice()
```

please download the appropriate model using the command

``` bash
python -m spacy download en_core_web_lg
```

before running the code in the virtual environment.
  
## DataSets
Dataset used in the paper can be downloaded from [here](https://uwmadison.box.com/s/v6girx83x0krai1k45vnn41w21brn4hi). Upon downloading the tar file, it can decompressed using `tar -xf gdpr_data.tar` which will create the folder `GDPR_Data` which contains the raw HTMLs, the textual data that we extracted and the output of Polisis (which contains the annotated version of the privacy policies generated using [Polisis](https://arxiv.org/pdf/1802.02561.pdf)). This annotated version of the policies is used for automated analysis (coverage, compliance and specificity) as discussed in the paper. This is done using structured querying on top of the annotated policies. The output of querying process is present in `/polisis_queries/`.

To organize the data, each policy url is assigned a unique Policy ID (PID). All the files and and data associated with policy url is stored with this PID. Files `eu_dataframe_with_url.csv` and `global_dataframe_with_url.csv` contains this the mapping between policy urls and PIDs, along with the pre-GDPR and post-GDPR timestamps for each policy. As discussed in the paper, the pre-GDPR and post-GDPR timestamps are chosen by comparing the text of the policy in the timeseries. In particular, we define, for each policy, the *key-change date* as the closest month to the enforcement date of the GDPR that exhibited a significant change. The pre-GDPR snapshot of the policy is the first stable version of the policy before the key-change date with a timestamp preceding May 2018. For post-GDPR snapshot, we used the most recent snapshot taken after May 2018. This distinction is used to measure how the evolution of policies was affected by GDPR using the automated analysis. An in-depth explanation of the sets in the order of their use in the study is given below:

- `/GDPR_Data/raw_html`: Contains time-series of raw-html for our sets of _EU_ and _Global_ privacy policies. A single policy's time-series of HTML pages can be found at `/raw_html/<set>/<pid></pid>`, where `<set>` is either `EU` or `Global` and `pid` is the unique ID assigned to a given domain. Thus, an example policy from the `EU` set with pid `3362`) could be found at `/raw_html/EU/3362`. Each element of the timeseries is a directory with its name being the timestamp of the policy's snapshot. So `/raw_html/EU/3362/20160101142306` would hold the snapshot from January 1st, 2016 at 14:23:06 (the locale here is that of the __Wayback Machine__). To get the raw document of the element, traverse to the bottom directory and open the page.
- `/GDPR_Data/text_data`: Contains the time-series of text extracted from the `/raw_html` directory. A single policy's time-series of text data can be found at `/text_data/<set>/<pid></pid>`, where `<set>` is either `EU` or `Global` and `pid` is the unique ID assigned to a given domain. Thus, an example policy from the `EU` set with pid `655`  can be found at `/text_data/EU/655`. Each element is a text file with its name corresponding to the time the snapshot is taken, now condensed to just year and month, so `/text_data/EU/655/201612.txt` corresponds to December 2016.
- `/GDPR_Data/polisis_outputs`: contains the output files of Polisis's privacy policy analysis for our analyzed policies. A single policy's post-GDPR analysis is located at `/polisis_outputs/set/post_data/pid.json`. Thus, an example policy from the `EU` set with pid `1205`  can be found at `/polisis_outputs/EU/post_data/1205.json`. The detailed structure is as follows:

```bash
/GDPR_Data/polisis_outputs
    /Global > /pre_data > [.json files containing annotated policies]
    /Global > /post_data > [.json files containing annotated policies]
    /EU > /pre_data > [.json files containing annotated policies]
    /EU > /post_data > [.json files containing annotated policies]
```

- `/polisis_queries`: contains the 3 sets of query-scores explained in our study. To access all scores for a single set (_e.g._ the specificity scores for the EU set) open `/polisis_queries/specificity/EU.json`. The detailed structure is as follows:

```bash
/polisis_queries
    /coverage > /location.json > pid > source: [strings]
    /compliance > /location.json > pid > query > source: {count: int}
    /specificity > /location.json > pid > query > source: {S: int, S_a: int}
```

## Running the code

The bulk of the analysis code is all located in `GDPR_ANALYSIS_MAIN.ipynb`. Additionally, the analysis of the user study results is found in a Jupyter Notebook at `/user_study/results_analysis.ipynb`.

The code can be conveniently run using the jupyter notebook `GDPR_ANALYSIS_MAIN.ipynb`. It has several sections corresponding to the sections in the paper.

## Citation

In case you use our datasets in your research, please cite our PETS 2020 paper.
```
@inproceedings{linden2020gdpr,
  title = {The Privacy Policy Landscape After the GDPR},
  author = {Thomas Linden and Rishabh Khandelwal and Hamza Harkous, and Kassem Fawaz},
  booktitle = {Privacy Enhancing Technologies 2020 (PETS 2020)},
  year = {2020}
}
```
