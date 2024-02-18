# Project Description 

This is a project for a Computer Vision and Machine Learning course where I applied CV2 to construct a real-time data collection mehtod for sign language data and constructed three models, to emphasize and learn the impacts the data set,
model architecture, and parameters have on the accuracy and efficiency of the model. Regarding the program we used the viola jones algorithm the identify the face so that an ROI can be constructed, then I used the distribution of skin 
tone in my face to help identify the location of my hands in real time, only after blocking off my face from the tracking camera. Once the foundation for the program was built, a timer was set so that it would capture my hands when they
make 3 sign langauge letters. After the arduous data collection process, I applied the data to 3 varying network models and compared the results. 

# Tasks

## Task 1

Develop a program that identifies your face in the the captured video stream using the Haarcascade classifier. Optionally, detect the eyes on your face. Once the face is detected draw a rectangle around your face and your eyes.

## Task 2 

Improve the computation speed of the face detection, by first identifying the face and then defining a new larger region of interest around your identified face. This new region of interest surround the face will then have the detection fucntion applied to only work with that ROI. This reduced the area where the detection function is applied making it more efficient in identifying the face and eyes. This application makes sense a s head does not tend drastically move across a screen quickly, it will slowly travers across it. With this in mind. When the face movs in the larger detected region the region will then apply the detect function applied over and recompute where the larger ROI should be moved to in alignment with the new detected face position.

## Task 3

Identify the face in the captured video stream, then calculate the histogram from the gray image. Then use back propagation on the constructed histogram.  Essentially, it creates an image of the same size (but single channel) as that of our input image, where each pixel corresponds to the probability of that pixel belonging to our object. In more simpler words, the output image will have our face of interest in more white compared to other parts of the image.

## Task 4 
After calculating the probability of the face using backprojection and the histogram, set the probability of the identified face to zero. Since the program will iterate through till a face is found, as your identified face will no long be recognized by the program, it will search for other parts of the image that share similar statistics based on the hues and colors of the pixels. Thus only other identifiable object in the video stream that shares similarities to your face would be your hand, forcing the program to recognize it.

## Task 5 and Task 6

Detect and Store your Hand 

After removing my face (setting the probability to 0) Cam shift will detect your hand since the skin color probability distribution of your hand is very similar to your face. 

Image should be stored in 2 sizes:


*   16 x 16
*   224 x 224 

Link to drive:

https://drive.google.com/drive/folders/1UDRvzc6WuSL_vsn8MsmEXp_IQMkmqdMY?usp=sharing

## Task 7

### The Models 1, 2, and 3



Dataset 1: 
The first dataset looks at three letters with high variability. This dataset emphasizes how variability impacts the training of the model. The model itself performed worse on dataset 2 and 3, which is due to the high variability. For the model to perform better more data would be needed and a longer training time is required. However, with the increase in data and the longer training time the increased variability would in fact make the model more robust when applied to the real world. 

Dataset 2: 
The second dataset focuses on three letters with varying amounts of images to train the model. This leads the model to make increasingly inaccurate predictions on certain classes as it is unable to differentiate differences between spatial aspects of the pixels. This reduces accuracy for some classes and makes the model less robust for certain hand gestures. 

Dataset 3: 
The third dataset has the highest loss due to its lack of variability. It focuses on three letters with low variability. Looking at the accuracy it has, it is worse than the other two models as it cannot generalize any variability in the pictures. Meaning, if the hand is tilted if you use the opposite hand, it won't be able to accurately predict the gesture.

The Model:
The model I developed consists of 5 relu hidden layers with varying number of neurons ,input relu layer with 26 neurons, and an output softmax layer. There is one dropout layer with a probability set to .7. Overall, there are 1,497,021 parameters, this was developed in an attempt to improve the validation accuracy, over 100 epochs. To help avoid overfitting and to increase the data size an augmentation was added to horizontal flip the image or the image matrix. Dropout was placed closer before the layer with more drastic increases in the number of neuron because it helps to reduce validation loss and improve generalization, without impacting more complex features. I implemented a compression from a dense layer of 6656 to 13  to compress more basic features learning into more complex ones to improve accuracy. With other parameters I tested them out multiple times with specific values. In regards to the learning rate, i set up a learning rate scheduler that exponentially decays the initial learning rate so that it is able to find an optimum minimum without resulting in divergence.


