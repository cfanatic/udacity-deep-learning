# udacity-deep-learning

This repository hosts all projects that I was working on during the Udacity Deep Learning program. Course highlights include the development of multi-layer neural networks, convolutional neural networks, recurrent neural networks and generative adversarial networks.

## [Project 1: Multi-Layer Perceptron](https://github.com/cfanatic/udacity-deep-learning/tree/master/1-project-bikesharing)

The task of this project was to build and train a neural network from scratch to predict the number of bikeshare users on a given day.

The dataset has the number of riders for each hour of each day from January 1 2011 to December 31 2012. The number of riders is split between casual and registered, summed up in the `cnt` column.

![Input Data](https://raw.githubusercontent.com/cfanatic/udacity-deep-learning/master/99-misc/project1_data.png)

The network has two layers, a hidden layer and an output layer. The hidden layer will use the sigmoid function for activations. The output layer has only one node and is used for the regression.

![Predicted Output](https://raw.githubusercontent.com/cfanatic/udacity-deep-learning/master/99-misc/project1_prediction.png)

I believe the prediction is quite good up to December 21. However, I notice that there is a general offset between prediction and test data. This means that training could still be improved, but I wanted to avoid overfitting. There is a negative prediction of bike users on December 16. This does not make sense. The output of the neural network must be limited to positive values only. Also, there is an obvious mismatch between prediction and test data starting from December 21 onwards. Although holidays are flagged in the dataset, I assume that the dataset is generally biased towards regular working days and not towards the holiday season. Concerning the general offset between prediction and test data, I believe it is a better idea to randomize weights each iteration instead just once in the class constructor.

## [Project 2: Convolutional Neural Network](https://github.com/cfanatic/udacity-deep-learning/tree/master/2-project-dog-classification)

The task of this project was to build a convolutional neural network for image classification. The code accepts any user-supplied image as input. If a dog is detected in the image, it will provide an estimate of the dog's breed. If a human is detected, it will provide an estimate of the dog breed that is most resembling.

I designed and trained my own convolutional neural network from scratch, and also applied transfer learning on a ResNet-101 model with a final accuracy of 85%.

![Dog](https://raw.githubusercontent.com/cfanatic/udacity-deep-learning/master/99-misc/project2_dog.png)

![Human](https://raw.githubusercontent.com/cfanatic/udacity-deep-learning/master/99-misc/project2_human.png)

The lower image confirms that neural networks are vulnerable towards adversarial attacks. The implemented CNN is not able to distinguish between a real face and a fake mask. Adversarial attacks are an important field of research for self-driving cars, since computer vision algorithms for traffic light and street sign detection could be fooled in similar ways.

## [Project 3: Recurrent Neural Network](https://github.com/cfanatic/udacity-deep-learning/tree/master/3-project-tv-script-generation)

The task of this project was to build a recurrent neural network for text generation. The model was trained with a dataset consisting of Seinfeld TV scripts. It produces some dialog based on the patterns it has learned in this training data.

Starting with the word `jerry` as the input seed, this recurrent neural network predicts a series of next words until it has reached a set length of 200 words. These types of models have a kind of built-in memory which are really useful in prediction tasks that are time or sequence dependent.

```text
jerry: hey!

jerry: i can't believe this, i was in the hospital to be a little more tactful.

george: you know what? you know, i have a very bad idea.

george: what is it?!!

kramer: (to jerry) you got the job?

helen: i don't know why we had a little more time.

jerry: i think i can see the whole thing, and i was thinking of a little problem with you?

george: (looking at the tv)

jerry: i think you're going to go. (to george) hey, you gotta see the doctor?

elaine: no, no. no.

newman: (to jerry) you know i don't know what you think.

kramer: oh yeah, you know i was gonna get out
```

The model output does not make perfect sense. The data pre-processing step could be improved by removing frequent words such as "the", "to", "no", etc. This is only noise. Additional hidden layers could be introduced which would allow the model to learn more text features. Using a larger training dataset could help to improve semantic meaning.
