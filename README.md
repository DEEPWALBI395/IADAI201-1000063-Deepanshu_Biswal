# IADAI201-1000063-Deepanshu_Biswal

In my pose detection project, I started with a research phase to understand the key techniques required for pose detection. Then, I set up my coding environment in VS Code by installing the Jupyter Notebook and Python extensions. Using the command prompt, I installed the necessary Python libraries, including numpy, pandas, opencv-python, tensorflow, and keras, which would allow me to work with video frames, handle data, and build neural network models. I then prepared my dataset by downloading 12 videos from YouTube—4 videos for each gesture (clap, walk, and run), 3 for training the model and 1 for testing. After converting these videos to AVI format, I used this dataset to create and normalize pose landmarks.

Code Explanation

The project code can be broken down into a few main sections:

Capturing and Extracting Pose Landmarks:

First, the cv2 library opens a video file, which we’ll process frame by frame.
Using mediapipe, a powerful library for pose detection, we detect 33 key landmarks on the body in each frame. These landmarks represent points like shoulders, hips, and elbows, which are essential for recognizing human poses.
For each frame with detected landmarks, we store the x, y, z coordinates, and visibility of each landmark into a CSV file. This is the raw dataset capturing body positions in every frame, which we later use to train our model.
Normalizing and Preparing Data:

Once we capture the landmark coordinates, we normalize them by using the left hip landmark as a reference. Normalization centers all positions around this point, which helps make the model more robust to movement or scaling differences.
The normalized data is saved to a new CSV file, ready for further processing.
Splitting Data for Training and Testing:

We split the dataset into training and testing subsets (80% training, 20% testing). This separation is crucial for evaluating how well the model generalizes to new, unseen data.

Building and Training a Pose Classifier:

Using TensorFlow and Keras, we define a neural network model for pose classification. The model consists of three layers: an input layer (taking all normalized landmarks as features), two hidden layers (for learning complex patterns), and an output layer (which predicts one of our poses).
We train the model using the normalized pose landmarks and associated labels from our dataset, achieving high accuracy (even close to 100%).
Running and Testing the Model:

After training, we load the model and open a test video to see how well it recognizes the gestures in real-time.
For each frame, we predict the pose and display it as a label on the video screen. If the model correctly identifies the gestures, it shows labels such as "clap," "walk," or "run" on the screen.
The program runs until the video ends or until we press 'Q' to quit.
In this project, I not only captured and normalized pose data but also trained and tested a model that can accurately recognize different body gestures. The result is an interactive demo that shows real-time pose recognition on video, with the model achieving high accuracy. Pressing 'Q' allows the program to exit gracefully, completing the demonstration.
