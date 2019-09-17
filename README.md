# The Privacy Policy Landscape After The GDPR
Dataset and source code for the paper [The Privacy Policy Landscape After the GDPR](https://arxiv.org/pdf/1809.08396.pdf)


## Running the code
The code can be conveniently run using the jupyter notebook `GDPR_ANALYSIS_MAIN.ipynb`. It has several sections corresponding to the sections in the paper.

### Issue with loading Spacy Language Model
If you encounter an error while loading the language model in spacy during the execution of the command 
```
pv = PassiveVoice()
```
please download the appropriate model using the command 
```
python -m spacy download en_core_web_lg
``` 
and rerun the code. 

## Citation
If you wish to use our dataset in your research, please cite our PETS 2020 paper.
```
@inproceedings{linden2020gdpr,
  title = {The Privacy Policy Landscape After the GDPR},
  author = {Thomas Linden and Rishabh Khandelwal and Hamza Harkous, and Kassem Fawaz},
  booktitle = {ArXiv preprint arXiv:1809.08396},
  year = {2019}
}
```
