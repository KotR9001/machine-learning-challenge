# machine-learning-challenge

Carried out an assignment to classify candidate exoplanets based on the feature data of candidate objects.<br />
<br />
<b>Read the CSV</b><br />
-First, read in data from a CSV file that contained feature data and koi_disposition classifications.<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/06784d14-0285-4362-8e27-877678370e2f)<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/46ad1fba-57e0-4bb2-9b0f-89cd140036d1)<br />
<br />
<b>Feature Selection</b><br />
-Next, selected features for analysis and assigned to the 'selected_features' variable.<br />
-After that, assigned the koi_dispositions from the DataFrame to a variable of the same name and reshaped to prepare for Machine 
Learning.<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/9b14300d-90a8-4fe8-b21e-7c5bf075e40f)<br />
<br />
<b>Train Test Split</b><br />
-From there, used the 'train_test_split' from sklearn to randomly split the data into 'X_train', 'X_test', 'y_train', and 'y_test'
variables.<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/146a8070-8465-4970-b7a3-c2e66485ab19)<br />
<br />
<b>Pre-Processing</b><br />
-Used the 'StandardScaler' module to transform the X data to have a range from 0 to 1 to prepare for analysis.<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/ade3c4a4-dbaa-4324-9d1e-71c3b64a92aa)<br />
-Then, used label encoding, followed by one-hot-encoding to allow for the koi_disposition labels to be assigned distinct numerical
values to enable classification analysis.<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/75f519fd-3146-4ede-b621-cdda0a4cacd6)<br />
-Created models in two separate Jupyter Notebooks to try different approaches to classifying data.<br />
	-In 'model_1.ipynb', used a K_Nearest_Neighbors classifier to find the optimal amount of k nearest data 
	points that should be used to for making predictions.<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/d5268523-3b4a-4cc3-a63c-0fc88a58196f)<br />
		-The optimal value was k=17.<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/674e31f2-58fc-4e50-b770-34cbf86739c3)<br />
		-Set 'model1' as KNeighborsClassifier(n_neighbors=17)<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/debc7c9b-5e4e-4fc8-af47-064d1a97c7fd)<br />
		-Fit 'model1' to 'X_train_scaled' and 'one_hot_y_train', and obtained scores as follows:<br />
			-Training data: R^2=0.857<br />
			-Testing data: R^2=0.847<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/27a8de71-8caa-4ec8-a686-e3c63d6b7a34)<br />
	-In 'model_2.ipynb', used a LogisticRegression classifier.<br />
		-Set 'model2' as LogisticRegression.<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/2215db8f-665c-4aeb-9763-2dd1dd9f7d5f)<br />
		-Fit 'model2' to 'X_train_scaled' and 'encoded_y_train', and obtained scores as follows:<br />
			-Training data: R^2=0.835<br />
			-Testing data: R^2=0.827<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/57776e2e-e4e6-45cf-b156-b5809d4705a5)<br />
<br />
<b>Hyperparameter Tuning</b><br />
-For both of these models, used 'GridSearchCV' to optimize the predictions of the models by way of hyperparameter tuning.<br />
-Passed lists of values for each parameter in a dictionary, and tested every combination of parameter values.<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/b8032719-4e88-4445-8581-f7e91e0794fe)<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/fcc9608b-466d-430f-b1a7-0efeafafdb5e)<br />
-Returned a dictionary showing the set of optimal parameter values along with the corresponding best score.<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/4e8b8614-c709-499a-924a-7f610180c50b)<br />
-Made predictions based on 'X_test_scaled'.<br />
	-The final scores were as follows:<br />
		-'model1': R^2=0.841<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/d19871cd-f0b9-40d1-acc7-0708b10de041)<br />
		-'model2': R^2=0.841<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/0fdc3f0d-f887-4e88-a154-3540ec97a702)<br />
-Used the 'classification_report' module to compare the predicted and actual values.<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/7aff46f6-91dc-420c-b3a1-6cda3543dac4)<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/f171473b-202c-4f1d-a006-adc348cd04e2)<br />
-Lastly, performed ANOVA analysis to obtain the F-values and p-values for each feature and order by relative importance.<br />
	-Did iterative passthroughs of the feature selection to select the right amount/types of features 
	followed by all of the proceeded steps in order to maximize the R^2 values from the hyperparameter tuning 
	step with GridSearchCV.<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/1259548f-ca26-4e67-9a1a-5970f51f9f99)<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/2d475d47-1616-488c-b03d-eb890d8ef99c)<br />
<br />
<b>Save the Model</b><br />
-Saved the models as a final step so that users could pull the model parameters and use them on other sets of planetary data if
desired.<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/2f135d13-d1c6-4c0f-b4aa-7d35de7fea7e)<br />
![image](https://github.com/KotR9001/machine-learning-challenge/assets/57807780/f82e5c1d-d737-42dd-be62-c2c132a86e09)<br />
<br />
<b>Conclusions</b><br />
-Both models gave the same predictive power when optimized.<br />
-This would suggest that GridSearchCV equalizes the predictive power of the models through its optimization process.<br />
-Thus, as long as GridSearchCV is used properly, the model type might not matter much.<br />
