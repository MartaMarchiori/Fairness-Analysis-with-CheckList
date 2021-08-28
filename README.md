# Fine-Grained Fairness Analysis ofAbusive Language Detection Systems with CheckList

This folder contains the project carried out during the internship at FBK, concerning the application of the tool CheckList (Ribeiro et al., 2020) in order to evaluate systems of Hate Speech detection, using representative datasets for this task, with a particular focus on fairness.  

### 1) Evaluation_Datasets, folder 
These synthetic datasets concerns the Hate Speech Detection task. The data are in English and are divided in three categories, dealing with bias towards different targets. For each of the category, one dataset is created through the Jupiter notebook called "1_NLP Tests with CheckList + Creating Synthetic Dataset.ipynb".
- sexism.csv for misogyny, gender, sexual orientation
- racism.csv for ethnicity, nationality and religion
- ableism.csv for disability and old people 
- all_synthetic_dataset.csv contains them all 

As these data have been synthetically created with CheckList, they are freely usable. 
The labels refers to the task of Hate-Speech Detection, i.e.
- 0 for non-hateful content 
- 1 for hateful content

### 2) Suite, folder
We developed one suite having different capabilities tested: the suite is saved with the extension .pkl and with the extension .txt. 
The suite is created through the Jupiter notebook "1_NLP Tests with CheckList + Creating Synthetic Dataset.ipynb": **the core of this work partially relies on the examples and the tutorials released by CheckList authors for the task of Sentiment Analysis**. New capabilities -with respect to the ones in the released- have been added and the lexicons and templates have been expanded and declined especially with a focus on unintended model biases with respect to sexism, racism and ableism. 

The other notebook, "2_Tests_Executions.ipynb", reports the code to run the suite, where we can also explore the results (Important: The visual summary is implemented by the authors as ipywidgets and don't work on Colab or JupyterLab; in Jupyter notebooks instead is available and working - You can see an example in the image Visual Summary).

The output will be:
1. results_suite_NLP_Tests.csv summarizing the stats obtained through the tests;
2. misclassified_records.csv containing the wrong labeled records, in case you want to explore them further or conduct additional training on them. 

### 3) Prediction file example, folder


### 4) Report_Marchiori_CheckList, document 
Describing the results and the analyses 

### 5) Slide_Marchiori_CheckList, presentation 
Summarizing the project 

## TO RUN THE SUITE AND TEST YOUR OWN MODEL:
Compute the predictions for NLP_Tests.txt file, saving them in a file where each line has 4 numbers: the prediction (0 for hateful, 1 for neutral, 2 for non-hateful) and the prediction probabilities for (negative, neutral, positive). Since the task of Hate-Speech Detection doesn't compute the neutral label, you can put in the neutral probability always 0 (the tests created do not include the neutral label, for the same reason).

Then, in the Tests' Executions notebook, update the pred_path with this file and run all.

Take a look at the folder "Prediction file example" where you can find the notebook "Using_BERT_as_Hate_Speech_Classifier.ipynb", that produce the output ("output_NLP_Tests") in the format needed.  

#### EXAMPLE: 
```suite_path = '*insert the path of the suite NLP_Tests.pkl*'

suite = TestSuite.from_file(suite_path)

pred_path = '*insert the path to the file where you saved the predictions for the txt file associated with the suite*'

suite.run_from_file(pred_path, overwrite=True)

suite.summary()

```

## Publication

> Marta Marchiori Manerba and Sara Tonelli. Fine-Grained Fairness Analysis ofAbusive Language Detection Systems with CheckListn, Workshop on Online Abuse and Harms (5th WOAH!), 2021

Bibtex for citations:

```@inproceedings{manerba-tonelli-2021-fine,
    title = "Fine-Grained Fairness Analysis of Abusive Language Detection Systems with {C}heck{L}ist",
    author = "Manerba, Marta Marchiori  and
      Tonelli, Sara",
    booktitle = "Proceedings of the 5th Workshop on Online Abuse and Harms (WOAH 2021)",
    month = aug,
    year = "2021",
    address = "Online",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2021.woah-1.9",
    doi = "10.18653/v1/2021.woah-1.9",
    pages = "81--91",
}```
