# machine-learning-challenge

An assignment was carried out to classify candidate exoplanets based on the feature data of candidate objects.

Read the CSV
-First, data was read in from a CSV file that contained feature data and koi_disposition classifications.

Feature Selection
-Next, features were selected for analysis and assigned to the 'selected_features' variable.
-After that, the koi_dispositions from the DataFrame were assigned to a variable of the same name and reshaped to prepare for Machine 
Learning.

Train Test Split
-From there, the 'train_test_split' from sklearn was used to randomly split the data into 'X_train', 'X_test', 'y_train', and 'y_test'
variables.

Pre-Processing

-The 'StandardScaler' module was used to transform the X data to have a range from 0 to 1 to prepare for analysis.

-Then, label encoding was used, followed by one-hot-encoding to allow for the koi_disposition labels to be assigned distinct numerical
values to enable classification analysis.

-Models were created in two separate Jupyter Notebooks to try different approaches to classifying data.

	-In 'model_1.ipynb', a K_Nearest_Neighbors classifier was used to find the optimal amount of k nearest data points that should be 
	used to for making predictions.

		-The optimal value was k=17.

		-'model1' was set as KNeighborsClassifier(n_neighbors=17)

		-'model1' was then fit to 'X_train_scaled' and 'one_hot_y_train', and scores were obtained as follows:

			-Training data: R^2=0.857

			-Testing data: R^2=0.847

	-In 'model_2.ipynb', a LogisticRegression classifier was used.

		-'model2' was set as LogisticRegression.

		-'model2' was then fit to 'X_train_scaled' and 'encoded_y_train', and scores were obtained as follows:

			-Training data: R^2=0.835

			-Testing data: R^2=0.827

Hyperparameter Tuning

-For both of these models, 'GridSearchCV' was used to optimize the predictions of the models by way of hyperparameter tuning.

-Lists of values were passed for each parameter in a dictionary, and every combination of parameter values was tested.

-A dictionary was returned showing the set of optimal parameter values along with the corresponding best score.

-Predictions were made based on 'X_test_scaled'.

	-The final scores were as follows:

		-'model1': R^2=0.841

		-'model2': R^2=0.841

-The 'classification_report' module was used to compare the predicted and actual values.

-Lastly, ANOVA analysis was done to obtain the F-values and p-values for each feature and order by relative importance.

	-Iterative passthroughs of the feature selection were done to select the right amount/types of features followed by all of the
	proceeded steps in order to maximize the R^2 values from the hyperparameter tuning step with GridSearchCV.

Save the Model

-The models were saved as a final step so that users could pull the model parameters and use them on other sets of planetary data if
desired.

Conclusions

-Both models gave the same predictive power when optimized.

-This would suggest that GridSearchCV equalizes the predictive power of the models through its optimization process.

-Thus, as long as GridSearchCV is used properly, the model type might not matter much.




