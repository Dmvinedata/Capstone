

# Finding Homes for the Pet Homies
## Predicting Animal Adoptions with Binary Classification
## Data Scientist: Deztany Jackson

I am partnering with Malaysia's Ministry of Tourism to refine their country's pet adoption process. "Will a stray be adopted or not?" is the driving question.  An advanced decision tree model is used as the binary classification model predictor. This model has ~81% (precsion) predicting if a Malaysian stray (cat or dog) will be adopted.  

Real world data was imported from PetFinder.my (via Kaggle). The training dataset had over 11000 entries with about 19 attributes descrbing the animal. It will surely help protect Malaysian states health (locals and tourists) while making the adoption process more cost and labor efficient.


![Wallstreet Journal GettyImages,Cat&Dog](https://github.com/Dmvinedata/Capstone/blob/main/images/cat_dog.jpeg)



# Business Understanding
[Malaysian Strays, 2021](https://www.thesundaily.my/local/need-to-address-issue-of-strays-population-EE85305030)<br>
[Poltical Animals,2021](https://www.scmp.com/week-asia/society/article/2106109/how-malaysias-dogs-became-political-animals) <br>
[VetFuturist,Unknown](https://vetfuturist.com/stray-animals-malaysia-reality-i-saw-travelling-there-past-months)
Malaysia's Ministry of Tourism is partnering with the local pet adoption agencies to minmize stray animals in the country. They spend about RM10.3 ($2.3Million) managing pounds and euthanization cost.<br>

The ministry cares about correctly predicting adoptable animals well. The adoptable animals will be prioritized in a shelter or pound. It is not determined what will happen with ther other animals. The Ministry of Tourism has another phase to find the best solutions that utilize the animals and minimizes Euthanasia.

**Ministry of Tourism (Main Stakeholder)**
- Want to understand which animals are the most adoptable. (Phase 1:Current Model)<br>
- There goal is to improve the safety, attraction of area and soothe political upheival about all the strays.<br>
**Adoption Agency (Secondary Stakeholder)**
- Minimize Euthenasia and maximize holding animals as long as possible
# Date Understanding

Pet Finder supplied data for about 19,000 adoption entries for dogs and cats in each of Malaysias states.
[Kaggle PetFinder, 2018](https://kaggle.com/competitions/petfinder-adoption-prediction)<br>

- **Initial Target Classes:**
    - One Day Adoption: 410
    - One Week Adoption: 3090
    - One Month Adoption: 3259
    - Two/Three Month Adoption: 4037
    - No Adoption: 4197
- **Modified Target Classes:**
    - Adopted: 10796
    - Not Adopted: 4197

**Chosen Metrics:**<br>
- Primarily want **Precision** to maximize TP and minimize FP of adoptees.<br>
- Secondary we want **Recall and F1** to minimize FN and because of imbalance.<br>

[F1 Score Metric, Joos Kortanje, 2021](https://towardsdatascience.com/the-f1-score-bec2bbc38aa6)

**
![Classificaiton Distribution](https://github.com/Dmvinedata/Capstone/blob/main/images/AdoptionDist.png)
***



# Modeling & Evaluation

## Model Iteration

- **Dummy Model:** 
- **Baseline:**
    - Logistic Regression
    - KNN
    - XGBoost
    - Randon Forest
    - Neural Net
- **Pipeline (Scaled and Smoted)and GridsearchCV**
    - Logistic Regression
    - KNN
    - XGBoost
    - Randon Forest
    - Neural Net
## Best Estimator

- StandardScaler()
- SMOTE (random_state=42, sampling_strategy= Minority)
- XGBClassifier (criterion='entropy',max_depth=6, learning_rate=0.01,n_estimators=120,gamma=3,random_state=42)

***
![Confusion Matrix](Best Estimator's Classification Matrix](https://github.com/Dmvinedata/Capstone/blob/main/images/ConMatrix.png)
***

***
![Plot Matrix](Best Estimator's Plot Curve](https://github.com/Dmvinedata/Capstone/blob/main/images/PR_AUC.png)
***

**Results Summary**
- They both have an average of ~13% FP rate from the Confusion Matrix. This is a decreased FP from baseline.
- Test precision metrics of ~81%.
- The model performs better (87%) than the base Dummy Classifier (~72%)
- The best modeol based on performance and FP and FN percentage. Slightly better than the Random Forest model.

## Best Features 
The top 5 featureswere:

- Age
- Breed1
- Color1
- PhotoAmt
- Gender

******

- The top two features are the same as the results from the initial correlation
- PhotoAmt and Color were initial weakly correlated to the Adoption Speed
- The Breed would help understand the animal without the Type explicitly known
- Knowing the photoAmt may help us to know that animals with photos and possibly multiple may have an easier time being adopted

# Conclusion

### Limitations

- Deeper explantion of attributes
- Target Class imbalance
- Synthetic Data used
- HW Resources: Hyperparamter tuning resource intensive
- Time for more hypertuning
- Analysis on numerical tabular attributes only

### Reccomendations
- Use model with an experienced rescuer
- Prioritize adoption form attributes
    - The feature importance shows with are the driving factors to understand if a animal will be adopted
- Plan cost with ~16% margin
- Acquire photos of all rescues

### Future Next Steps
- Photo Analysis ( Image Classification)
- Textual Analysis (Natural Language Processing )
- Recommend specific attributes to rescue first   

# Repository Navigation

**Repository Organization**
- .gitignore 
- License
- data
- images
- notebook_capstone.ipynb
- notebook.capston.pdf
- presentation_capston.pdf 

[Presentation Link](https://github.com/Dmvinedata/Capstone/blob/main/presentation_capstone.pdf) <br>

[Jupyter Notebook Link](https://github.com/Dmvinedata/Capstone/blob/main/notebook_capstone.pdf)  <br>

[Reproducibility Instructions](https://github.com/Dmvinedata/Capstone/tree/main/repoducibility)

