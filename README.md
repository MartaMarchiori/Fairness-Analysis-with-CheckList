# Explainability and Fairness analysis for abusive language detection systems with CheckList

References: 
>[Beyond Accuracy: Behavioral Testing of NLP models with CheckList](http://homes.cs.washington.edu/~marcotcr/acl20_checklist.pdf)  
> Marco Tulio Ribeiro, Tongshuang Wu, Carlos Guestrin, Sameer Singh
> Association for Computational Linguistics (ACL), 2020

This folder contains the project carried out during the internship at FBK, concerning the application of the tool CheckList (Ribeiro et al., 2020) in order to evaluate systems of Hate Speech detection, using representative datasets for this task, with a particular focus on fairness.  

#### 1) Evaluation_Datasets, folder 
We select well-known collections in the context of Hate Speech Detection, coming from different tasks but all in English and all related to social-media context (mostly from Twitter): the data are divided in three categories, dealing with bias towards different targets. For each of the category, one dataset is created (from merging existing ones) through these Jupiter notebooks:
- 1_Dataset_AMI.ipynb resulting in dataset_AMI.csv for the categories Misogyny, gender, sexual orientation
- 2_Dataset_Hate.ipynb resulting in dataset_Hate.csv for the categories Ethnicity, nationality and religion
- 3_Dataset_Disability.ipynb resulting in dataset_Disability.csv for the category Disability 
In addition, one csv foreach individual dataset is created, containing only the first 1000 records (these will be utilized for specific tests)

#### 2) Suites, folder
We developed 3 suites, each having different capabilities tested: each suite is saved in the folder Pkl (with the extension .pkl) and in the folder Txt (with the extension .txt). In Txt there is in addition tests_n500.txt, containing the tests for the original suite released in the package for Sentiment by the authors (Ribeiro et al., 2020). 
The suites are created through these Jupiter notebooks:
- 1_AMI.ipynb => Misogyny Detection
- 2_Fairness_HateSpeech.ipynb => Fairness with respect to Hate Speech targets
- 3_New_Capabilities.ipynb => New capabilities 
- 4_Tests_Executions.ipynb => The suites are runned in this final notebook, where we can explore the results (Important: The visual summary is implemented by the authors as ipywidgets and don't work on Colab or JupyterLab; in Jupyter notebooks instead is available and working). Running this notebook will create also csv files containing the results in tabular format. 

#### 3) Report_Marchiori_CheckList, document 
Describing the results and the analyses 

#### 4) Slide_Marchiori_CheckList, presentation 
Summarizing the project 

## TO RUN THE SUITES ON YOUR OWN MODEL AND REPLICATE THE RESULTS:
Compute the predictions for the txt file of your choice (in the Txt folder), saving them in a file where each line has 4 numbers: the prediction (0 for negative, 1 for neutral, 2 for positive) and the prediction probabilities for (negative, neutral, positive).
Then, in the Tests' Executions notebook, update the pred_path with this file and run the suite associated with the txt file for which you computed the predictions.

#### EXAMPLE: 
```suite_path = '*insert the path of the suite chosen in pkl extension*'

suite = TestSuite.from_file(suite_path)

pred_path = '*insert the path to the file where you saved the predictions for the txt file associated with the suite chosen*'

suite.run_from_file(pred_path, overwrite=True)

suite.summary()

```


