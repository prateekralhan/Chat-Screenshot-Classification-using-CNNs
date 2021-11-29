# Chat-Screenshot-Classification-using-CNNs [![Project Status: Inactive](https://www.repostatus.org/badges/latest/inactive.svg)](https://www.repostatus.org/#inactive) [![](https://img.shields.io/badge/Prateek-Ralhan-brightgreen.svg?colorB=ff0000)](https://prateekralhan.github.io/)

Many of my friends send me a lot of chat screenshots. Gradually, my phone gallery becomes cluttered with them. So, I thought that let's try to make a model which can separate the chat screenshots from other images. Thus, I have designed this Simple CNN architecture to predict whether any input image is a chat screenshot or a normal image. The input layer of the CNN will be an image and the output layer will contain only one neuron telling us if the input image is a normal image or a chat screenshot.

## Data Collection:
In this classification problem, I have two classes: ‘chat’ and ‘not chat’. The first one denotes the chat screenshots and the other one denotes the ordinary images. I collected screenshots of my chats with friends from different messaging apps like WhatsApp, Instagram, etc. For the second class, I collected some random images of people, places, sceneries from my phone. In total, I took **520** images(**260** for each class). Please note that this is not a sufficient amount of data for many harder problems.

## Train-Test Split :
I used **80%** of the data for training and kept the rest for testing. To be able to use the flow_from_directory function in Keras, I organized the data like this…

![hitachi_TNPSUITE](https://user-images.githubusercontent.com/29462447/71326992-b1323a80-2528-11ea-9bd9-4147c08fccc5.png)

## Model Architecture:
 In the convolution base, I have used two convolution blocks containing 32 filters each. The kernel size is **3x3**. The input dimension for the first convolution layer is **64x64x3**(RGB images of size **64x64** px). Each convolution block is followed by a max_pooling layer of size **2x2**. Relu activation function is used for the convolution layers. The output of the convolution block is flattened into a vector to pass it to the fully connected network. The hidden layer consists of 128 neurons. The activation function for this layer is again Relu. The output layer(i.e. the last layer) contains only one neuron which will tell us the result. 
I have used zoom, sheer, flip transformations for data augmentation and images have also been normalised.
 
![ai-fb](https://user-images.githubusercontent.com/29462447/71327140-aed0e000-252a-11ea-8cfd-5cdf0a2a7473.png)

## Training: 
I have trained the model on **416** training images and tested on **104** test images which is quite less if you want to perform any other complex operations using the model but I was able to get pretty accurate results ith this amount of data in hand. I have chosen **Adam** optimizer in this case. The cost function is **binary_crossentropy** (as this is a binary classification). Keras offers a function named *fit_generator* which can be used to run the training. Here we can also set the number of *epochs*, *steps_per_epoch*, and *validation_steps*. As the data is comparatively small hence I used **steps_per_epoch = number of training images** and **validation_steps = number of test images**

![coco](https://user-images.githubusercontent.com/29462447/71326989-ad061d00-2528-11ea-808e-4271ff430538.png)

## Result:
After only 5 epochs the model achieved **~99%** training accuracy and **98%** test accuracy.

I have also made it in the form of a simple web app using flask that can be executed, where you can upload images and the model will predict whether the image is a chat screenshot or not!! :)

![CHAT_SCREENSHOT](https://user-images.githubusercontent.com/29462447/71327150-e770b980-252a-11ea-939e-8e047c58a8ec.png)
