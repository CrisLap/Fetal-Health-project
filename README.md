# Fetal-Health-project
Fetal Health classification project <br>
You will analyse a fetal health dataset. <br>
This project starts with a dataset and its analysis is not defined in every detail, just like a real Data Science project. There are no precise instructions but simply a guideline that I think is fairly standard and general for each problem. <br>
Your task will be to follow each point and comment on it, showing me that you understand what you are doing. If some points prove impossible, explain the reason why. You will probably find some models or techniques that you have not really studied. Don't worry, experimentation, discovery and continuous updating are part of the game. <br>
EDA <br>
First of all, divide the dataset into a training part and a testing part. Start analysing the dataset. Pay attention to which dataset to use for each point (training, test or all?). Among other things, also consider:<br>
- Are outliers present (check feature by feature and plot feature values vs. classes)? If yes, what percentage? 
- The various features may have very different values. This is not good for almost any ML algorithm, so consider applying a Standardisation to the dataset, such as StandardScaler(). Be careful to exclude the label column!
Then ask yourself the following questions: 
- Are there any features with missing values? 
- Is the dataset balanced? If the answer is no, consider whether to balance it. Be careful though, we do not have many samples available. Is it worth it?
- How correlated are the variables? Then calculate the correlation matrices and give an interpretation. If there are highly correlated variables (e.g. feature_1 and feature_2), make a plot in which you show their correlation and consider whether to eliminate some of them (e.g. feature_2). 
- Are all the variables necessary for target prediction or can I select a subset of them and neglect the others? First use Mutual Information to do feature selection. Then try feature selection using ANOVA f-test (f_classif() in sklearn). In both cases you can make use of SelectKBest(). Compare the two methods and discuss whether they are consistent with each other.<br>
Choose the proper metric <br>
Once we understand the type of task to be solved (in our case it is a multi-class classification: 0,1,2), an important step that determines all future evaluations is the choice of metrics with which we are going to measure performance.<br>
The first that may come to mind is accuracy, but it is not the only one that is relevant. Indeed, often for problems where the dataset is not balanced (like ours) it is not the most appropriate. Try to consider other metrics and justify your choice.<br>
Model definition, training, hyperparameter tuning <br>
Think now about how to approach and set up the problem of health state prediction: Normal, Suspect, Pathological. Choose the following models: Logistic Regression, RandomForest Classifier and K-nearest neighbours (how do you choose the number k?). For each model you choose, read the documentation on sklearn. <br>
Now let's try two different ways. The road we call 1) consists of using all available features, while the road we call 2) consists of selecting the features (3 or 4) that proved to be most relevant according to the Mutual Information or ANOVA f-test above. <br>
Therefore perform the following procedure for both paths, first with 1) then with 2). <br>
1.	Perform a spot check on the chosen models and select the two best models using StratifiedKFold k-fold cross validation with one of the metrics discussed above as evaluation method (use the whole training set as dataset. The cross validation procedure will then divide the various k-folds into training and validation). The spot check is not intended to be a complete training but just a quick procedure to see if there are any types of models that stand out more than others. <br>
2.	Then carry out a tuning of the hyper-parameters on these two best models, e.g. using a grid search and always cross validation as an evaluation method (there is a GridSearchCV method on sklearn). You should now be in a position to know the best hyperparameters for both selected models. <br>
Now evaluate the two models on the hitherto unused test set. You will see which one performs better by comparing the values of the chosen metrics. <br>
Final Evaluation <br>
Now compare routes 1) and 2) and obtain the best model. Make a final discussion about the problem and the solution found.
Notes: I suggest to open the notebook with nbviewer at this link: https://nbviewer.org/github/CrisLap/Fetal-Health-project/blob/main/Fetal%20health%20project.ipynb
