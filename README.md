# Explainable Techniques II 
## Katie Hucker (kh509)

### Summary

This assignment explores the dataset Steam Dataset 2025 (https://www.kaggle.com/datasets/srgiomanhes/steam-games-dataset-2025). After some EDA, I create a RandomForestRegressor trying to predict video game price. I explore ACE, PDP, and ICE plots. Within the notebook is all the code, however, I have summarized the assignment related material here for ease of access. 


### EDA 

I explored the following relationships and distributions for this dataset: 
- number of total reviews
- average positive reviews for each genre (when games have >100 reviews)
- average price for each genre (when games have >100 reviews)
- the distribution of the positive percentual
- price distribution for games both with at least 100 reviews and all games

#### One of the more interesting plots was average price for each genre: 
![image](https://github.com/user-attachments/assets/3a505388-08ce-4465-a170-237facda60d3)

### Modeling 

I used a RandomForestRegressor model to predict pricing. This would enable companies to decide what to appropiately price their games at upon release. 

#### Here is a plot of actual price vs predicted price. We see there is some variation: 

![image](https://github.com/user-attachments/assets/3ea2d187-ecde-4109-9612-ace2ce579377)

### Explainable Plots 

#### Partial Dependence Plots

The feature n achievements is non-linear. As the number of achievements increases the prediction price increases. However, it does level out around 30 achievements for the most part. Most video games have achievevments, however, video games with more production typically have more achievements and in-turn are more expensive.

The feature total reviews is non-linear. As the total number of reviews increases the prediction price increases until about 2500 reviews. There is minimal increase to predicted price after that point. Number of reviews typically means the game is larger or widely played. After there is some threshold it seems reviews have no impact on the predicted price.

The feature positive percentual is non-linear. However, is mostly 'level' in nature. Positive percentual shows no impact on the predicted price. This is interesting because it shows that people leave positive ratings no matter the price of the game.

The feature review score is linear with 0 slope. Positive percentual shows no impact on the predicted price. This is interesting because it shows that people leave positive ratings no matter the price of the game.

![image](https://github.com/user-attachments/assets/5e3fc924-edf7-49e8-b31c-e68131bc5b0a)

#### ALE 

For the first order ALE plot, the number of achievements shows moderate impact on predicted price. It is downward curve which means number of achievements decreases predictions. Number of achievements provides information to the model with a moderate impact.

![image](https://github.com/user-attachments/assets/97e13405-6c61-4454-9963-eb01eed7d2f0)

For the second order ALE plot, As positive percentuals within value of 60-80 the number of achievements interaction causes a positive effect. The more achievements seems to give a positive effect at wider ranges of positive percentual. The upper region is predominantly blue, indicating that increasing the number of achievements in this range tends to decrease predictions. This is the same for the upper region. The slope variations show a non-linear relationship between these features and the model’s predictions.

![image](https://github.com/user-attachments/assets/af598505-9b67-4e74-8c3b-f30070c68541)

#### ICE 

The feature n achievements shows a spike around 20 achievements, across all instances. This shows that a moderate amount of achievements will increase your game price.

The feature total reviews shows minimal effect on price. We could probably remove this from our random forest model.

The feature positive percentual shows variation across all instances. There is one line which as a big jump in price at about 80% positive percentual.There are others which show 'jumpiness,' with a over-time decreasing trend. This shows that positive ratings does not necessarily mean a more expensive game.

The feature review score instances mostly all show 0 slope. There is no effect on price with the different review scores.

![image](https://github.com/user-attachments/assets/1d5bd2e0-0ee9-4921-ab64-d8b248be8255)


### References 

Kaggle dataset: https://www.kaggle.com/datasets/srgiomanhes/steam-games-dataset-2025

Pandas documentation: https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.explode.html

Chat GPT and Copilot: AI was used for complex code lines. This is more specifically documented within the notebook where AI was used. 

Dr. Bent's Class Example notebooks: 
- https://github.com/AIPI-590-XAI/Duke-AI-XAI/blob/main/explainable-ml-example-notebooks/global_explanations.ipynb
- https://github.com/AIPI-590-XAI/Duke-AI-XAI/blob/main/explainable-ml-example-notebooks/local_explanations.ipynb








