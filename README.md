# GPT and BERT-based models for identifying protein-protein interactions 
This repository contains the code and resources for training and evaluating two types of Large Language Models (LLMs) models namely Generative Pretrained Transformer) (GPT) and Bidirectional Encoder Representations from Transformers (BERT) on the task of identifying Protein-Protein Interaction (PPI). 

## Repository Structure
Below is the structure of the repository explaining the main components:
* **Datasets/**: Contains the datasets used for training and validating the models.
* **Prompts/**: Stores text prompts that are used as inputs for the GPT models.
* **plots/**: Includes generated plots and figures from the models' performances and data analyses

## Key Notebooks:
* `BERT_For_PPI.ipynb` - This notebook implements a BERT-based model for predicting protein-protein interactions (PPI) from the datasets. The model uses a pre-trained BioBERT, PubMedBERT and SciBERT for fine-tuning on PPI tasks using 10 fold cross valiation.
* `GPT_PPI_Original_Sentence.ipynb` - Generates PPI pairs from original sentences of the datasets using GPT-3.5 and GPT-4 models. The code contains three different promt settings namely base prompt, with protein dictionary and with normalized protein dictionary.
* `GPT_PPI_Original_Sentence_Evaluation.ipynb` - Evaluates the performance of the GPT-generated PPI pairs from original sentences to assess the predictive capabilities of the model.
* `GPT_PPI_PROTEIN_10fold.ipynb` - This notebook uses PROTEIN masked input sentences for identifying PPI using GPT models, specifically focusing on the same 10 folds used by BERT based models.
* `GPT_PPI_PROTEIN_Nfold.ipynb` - Instead of 10 folds it implements N-folds while no fold has any repetitive sentences, improving the generalizability of the model's predictive power.
* `GPT_PPI_PROTEIN_1Sentence.ipynb` - Predicts PPI processing one sentence at a time as input to ensure focused evaluation.
* `10fold_PROTEIN_Postprocessing_and_evaluation.ipynb` - Post-processes and evaluates the results from the 10-fold PPI predictions from protein masked sentences.
* `Nfold_PROTEIN_Postprocessing_and_evaluation.ipynb` - Post-processes and evaluates the results from the N-fold PPI predictions.
* `PROTEIN_OneSentence_Postprocessing_and_evaluation.ipynb` - Post-processes and evaluates the performance of the GPT-generated PPI prediction from protein masked sentences, one at a time.


### Additional Files:
*	`.gitattributes`: Git attributes file for repository configuration.
* `LICENSE`: Defines the terms under which the software can be used.
* `README.md`: This file, providing an overview and instructions for the repository.


### Installation
To set up your environment to run the notebooks, you will need to install several Python packages for both BERT and GPT models. You can install all the necessary packages using the commands below:
#### For BERT Model:
```bash
pip install transformers keras==2.9.0 Keras-Preprocessing==1.1.2
```
#### For GPT Model and General Utilities:
```bash
pip install sacremoses numpy pandas torch matplotlib
```

### Additional Libraries:
The code also uses several built-in libraries like `datetime`, `random`, `re`, `io`, `csv`, `shutil`, and `itertools` which are generally available by default in the Python standard library.
Ensure you have a Python environment (like Anaconda) set up with Jupyter Notebook or JupyterLab to run the provided notebooks.

### Usage
* Clone this repository to your local machine or a preferred environment that supports Jupyter Notebooks.
* Place your OpenAI API key in a secure location and ensure it is accessible within the notebooks where required.
* For GPU acceleration (recommended for model training), ensure CUDA is installed and configured according to your GPU and PyTorch's requirements.
* Navigate to the desired notebook, such as `BERT_For_PPI.ipynb` for BERT-based PPI prediction or `GPT_PPI_Original_Sentence.ipynb` for GPT-based sentence generation.
* Run the cells in the notebook to train models, generate predictions, and evaluate results.

### Dataset
we employed three widely used datasets for PPI extraction: LLL (Nédellec, 2005), IEPA (Ding et al., 2002), and HPRD50 (Fundel et al., 2007). These gold-standard datasets offer a unique perspective and challenge in biomedical NLP research, particularly in PPI extraction. 

Table 1. Number of positive and negative pairs in the sentences of the three datasets.  
| Dataset | Number of Sentences | Positive Pairs | Negative Pairs | Total Pairs | Positive:Negative |
|---------|---------------------|----------------|----------------|-------------|-------------------|
| LLL     | 77                  | 164            | 166            | 330         | 1:1.0             |
| IEPA    | 486                 | 335            | 482            | 817         | 1:1.4             |
| HPRD50  | 145                 | 163            | 270            | 433         | 1:1.6             |

### Comparative Results
<p>
  <img src="plots/LLL.svg" alt="Evaluation result" width="400" height="320" style="display: inline-block; margin-right: 10px;"/>
  <img src="plots/IEPA.svg" alt="Evaluation result" width="400" height="320" style="display: inline-block; margin-right: 10px;"/>
  <img src="plots/HPRD50.svg" alt="Evaluation result" width="400" height="320" style="display: inline-block;"/>
</p>

### Contributing
We welcome contributions from the community. Please feel free to fork the repository, make improvements, and submit pull requests.

### License
This project is open-sourced under the GNU GENERAL PUBLIC LICENSE. See the LICENSE file for more information.

### References
- **Nédellec, C.** Learning language in logic-genic interaction extraction challenge. Proceedings of the 4th Learning Language in Logic Workshop (LLL05), 2005. Citeseer, pp. 1-7. [Available Online](https://citeseerx.ist.psu.edu/document?repid=rep1&type=pdf&doi=91e0ce446530b62c78495cdfcfd9190efb974fce)

- **Ding, J., Berleant, D., Nettleton, D., & Wurtele, E.** (2002). Mining MEDLINE: abstracts, sentences, or phrases? In Pacific Symposium on Biocomputing (pp. 326-337). [Available Online](https://pubmed.ncbi.nlm.nih.gov/11928487/)

- **Fundel, K., Küffner, R., & Zimmer, R.** (2007). RelEx--relation extraction using dependency parse trees. Bioinformatics, 23(3), pp. 365-371. [Available Online](https://academic.oup.com/bioinformatics/article/23/3/365/236564)

### Citation
If you use this project in your research, please cite:
```bibtex
@article{rehana2023evaluation,
  title={Evaluation of GPT and BERT-based models on identifying protein-protein interactions in biomedical text},
  author={Rehana, Hasin and Çam, Nur Bengisu and Basmaci, Mert and He, Yongqun and Özgür, Arzucan and Hur, Junguk},
  journal={arXiv preprint arXiv:2303.17728},
  year={2023}
}
```
