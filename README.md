# Chat-Screenshot-Classification-using-CNNs
Many of my friends send me a lot of chat screenshots. Gradually, my phone gallery becomes cluttered with them. So, I thought that let's try to make a model which can separate the chat screenshots from other images. Thus, I have designed this Simple CNN architecture to predict whether any input image is a chat screenshot or a normal image. The input layer of the CNN will be an image and the output layer will contain only one neuron telling us if the input image is a normal image or a chat screenshot.

## Data Collection:
In this classification problem, I have two classes: ‘chat’ and ‘not chat’. The first one denotes the chat screenshots and the other one denotes the ordinary images. I collected screenshots of my chats with friends from different messaging apps like WhatsApp, Instagram, etc. For the second class, I collected some random images of people, places, sceneries from my phone. In total, I took 520 images(260 for each class). Please note that this is not a sufficient amount of data for many harder problems.

## Train-Test Split:
I used 80% of the data for training and kept the rest for testing. To be able to use the flow_from_directory function in Keras, I organized the data like this…



I have trained the model on 416 training images and tested on 104 test images which is quite less if you want to perform any other complex operations using the model but I was able to get pretty accurate results ith this amount of data in hand.
The images were scaled to shape 64,64,3 
