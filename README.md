---
title: "README.md"
output: html_document
---


# Explanation of files

#### A note about small_data
My dataset was too large to upload to GitHub. So, I took the first 10000 examples from each and put it into the folder called small_data. If you want to clone this REPO and run this code, change the name of the foler to data. 


### Scraping files

The files "MP_Forum_Scraping.ipynb", "MP_Route_Scraping.ipynb", and "Trailspace_Scraping.ipynb" all scrape data from the Mountain Project forums, Mountain Project routes, and Trailspace reviews, respectively. The data is stored in the data folder at "all_routes_and_desc.csv", "discussion_forum.csv", "review_forum.csv", and "trailspace_gear_reviews.csv". 



### Tuning DistilBERT

The file "DistilBERT_tuning.ipynb" tunes DistilBERT in three ways: one with the "all_routes_and_desc.csv", one with "trailspace_gear_reviews.csv", and one that uses both. These models are saved in the "models" folder. The folders "transformers" and "glue_data" are from HuggingFace and are needed to make the notebook run, but could not be uploaded here; they can be installed with the following bash commands:

```
git clone https://github.com/huggingface/transformers.git
cd transformers
pip install -e .
```



### Forum Labeling

In order to create a newtork, I had to label some of the Mountain Project forums. I did the actual labeling in Google Sheets, but there is some work related to it in the "forum_labelling.ipynb" notebook. The labels are saved in the data folder under "discussion_forum_labels_small.csv" and "review_forum_labels.csv". "labeled_forum_test.csv" was created from these two documents, and it is used to train and test the neural network. 



### Neural Network training

The models could not be uploaded here because the files are too big. However, the code in the notebooks will create them. There are four models that I compared: a baseline that uses untuned DistilBERT, then three more using the tuned DistilBERT models from above. An identical neural network was added to the top of each DistilBERT in the files "keras_DistilBERT_model.ipynb", "keras_route_model.ipynb", "keras_route_and_gear_model.ipynb", and "keras_gear_model.ipynb". The final models were saved in the folder "models/final_models." At first, each were trained on 30 epochs. Then, I re-trained each of them on an optimal number of epochs; that is why there are two of each (e.g. "gear_only" and "gear_only2").



### Final Analysis

After selecting the best model, "final_analysis.ipynb" uses the model to make predictions on "discussion_forum.csv" and "review_forum.csv", which were combined into "all_forums.csv". After predictions were made, the data was saved in the data folder at "full_forum_labeled.csv". The notebook then goes through some analysis of this dataset. 



