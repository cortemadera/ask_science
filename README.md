# Reddit Post Score Predictions

This repo utilizes a Linear Regression model to predict the scores of Reddit posts.

## Stack
* matplotlib
* numpy
* pandas
* scikit-learn
* torch
* tqdm
* transformers

## File Descriptions
1. askscience_post_analysis.ipynb: Analyze and visualize data to identify the characteristics of successful posts on r/askscience.

2. askscience_score_prediction_model.ipynb: Builds a model that predicts the score of a post on r/askscience, using **TfidfVectorizer** for text representation.

3. askscience_score_prediction_model_using_embedding.ipynb: Builds a model that predicts the score of a post on r/askscience, using **Embedding (model_name='bert-base-uncased')** for text representation.

## How to Run
1. Install required packages
 * pip install -r requirements.txt

2. Run the Jupyter notebooks

## Results
The document "model_performance_comparison.pdf" provides a listing of Mean Squared Logarithmic Error (MSLE) and R-squared values for various experiments run.

![Model Performance](https://github.com/cortemadera/takehome-xiao/blob/main/askscience/model_performance_comparison.pdf)

## Approaches and Conclusions
1. Model Selection: 
The Linear Regression model was chosen due to the target variable being numerical (i.e., the score).

2. Additional Feature Selection:
Analysis indicates a strong correlation between the scores and two key features: upvote_ratio and title length. These features are being experimented with.

![Feature Correlation](https://github.com/cortemadera/takehome-xiao/blob/main/askscience/feature_correlations.png)

3. Text Representation:
I tried two approaches to text representation for title and body:

 * TfidfVectorizer: This method focuses on keyword-based features.
 * bert-base-uncased Embedding: This technique provides a semantically rich representation.

4. Conclusions:

 * 4.1 The use of the **upvote_ratio** alone has yielded the best results for this dataset.

 * 4.2 Given that the upvote_ratio typically accumulates over time, it is vital for the model to rely on the post's content, such as the title and body. A model that utilizes **embeddings for text representation** of the title and body demonstrates better and more consistent performance, whether or not the upvote_ratio and other metadata are available.