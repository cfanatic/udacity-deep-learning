# udacity-deep-learning

This repository hosts all projects that I was working on during the Udacity Deep Learning program. Highlights include the development of multi-layer neural networks, convolutional neural networks, recurrent neural networks and generative adversarial networks.

## [Project 1](https://github.com/cfanatic/udacity-deep-learning/tree/master/1-project-bikesharing)

The task of this project was to build and train a neural network from scratch to predict the number of bikeshare users on a given day.

The dataset has the number of riders for each hour of each day from January 1 2011 to December 31 2012. The number of riders is split between casual and registered, summed up in the `cnt` column.

![Input Data](https://raw.githubusercontent.com/cfanatic/udacity-deep-learning/master/99-misc/project1_data.png)

The network has two layers, a hidden layer and an output layer. The hidden layer will use the sigmoid function for activations. The output layer has only one node and is used for the regression.

![Predicted Output](https://raw.githubusercontent.com/cfanatic/udacity-deep-learning/master/99-misc/project1_prediction.png)

I believe the prediction is quite good up to December 21. However, I notice that there is a general offset between prediction and test data. This happens on December 15, for example. This means that training could still be improved. But I wanted to avoid overfitting. There is a negative prediction of bike users between December 16 and 17. This does not make sense and it needs to be fixed: Somehow the output of the neural network must be limited to positive values only. Also, there is an obvious mismatch between prediction and test data starting from December 21 onwards. Although holidays are flagged in the dataset, I assume that the dataset is generally biased towards regular working days and not towards the holiday season. Concerning the general offset between prediction and test data, I believe it is a better idea to randomize weights each iteration instead just once in the class constructor.
