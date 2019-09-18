# The Privacy Policy Landscape After The GDPR
Dataset and source code for the paper [The Privacy Policy Landscape After the GDPR](https://arxiv.org/pdf/1809.08396.pdf)


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
before running the code. 

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
