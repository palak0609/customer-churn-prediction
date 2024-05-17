# customer-churn-prediction
I used a bank's dataset, containing information about customers leaving the bank, using this we need to predict which customer will leave the bank in future.
Steps to approach such a problem statement - 
Importing certain libraries
Loading the dataset, finding out possible information about the dataset(for example - if the dataset contains any missing values, or presence of duplicates)
To check for the number of customers exited, I used this code which indicates the same.
Now you can analyze your dataset and acknowledge that columns such as ('RowNumber', 'CustomerId', 'Surname') doesn't impact our prediction much so we can drop them. 
Further, ONE HOT ENCODING THE CATEGORICAL VALUES, using get_dummies() and (drop_first=True) this will drop one out of others from geography and gender(ex- france and female).
Split the model to train and test dataset.
Now, we will scale the value, as some values are very large in 'balance' and 'estimated_salary', this leads to a problem where weights get converged, using StandardScaler()
Using keras library, we create an object 'model' for the sequential model.
then we add layers(hidden, output).
Adding a dense hidden layer where our activation function is sigmoid, with 3 nodes and input is 11(except-exited).
adding a output layer.
Now, we need to compile our model, where we need to specify which loss function, optimizer we are going to use, since it is a binary classification problem, the loss fuction used is crossentropy/logloss. We can use different optimizer(gradient descent, stochastic gradient descent, root mean square propagation, etc.) but adam(adaptive moment estimation) works well.
fitting the model and letting it to iterate(epochs) 10 times, and storing it in a dictionary named 'history'. Validation_split works on the point where we are training our model; if we have 8000 entries it will divide it and remove 2000 entries and while running this it will simultaneously check for 2000 points and tell us accuracy.
then we will be able to get weights and biases in an array.
now comes the prediction, as we are using sigmoid function the output will be in the range of (0–1), a probability. we need to covert the probability to 0 or 1, for which we need to decide a threshold (ex-0.5, if probability is less than 0.5 the customer wont leave the bank and if probability is more than 0.5 then they will leave bank) threshold is generally determined with the help of a plot, but here we are guessing, here to be 0.5.
Then we are good to find the accuracy score of our model.
Also you can use matplotlib to plot graphs.

Note - To increase the accuracy we can increase
the number of epochs.
activation function of hidden layer to be relu.
by increasing the number of nodes of hidden layer.
or increase the number of hidden layers (but not much as it can create overfitting).
