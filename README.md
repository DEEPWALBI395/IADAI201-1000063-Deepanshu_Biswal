In my pose detection project, I started with a research phase to understand the key techniques required for pose detection. Then, I set up my coding environment in VS Code by installing the Jupyter Notebook and Python extensions. Using the command prompt, I installed the necessary Python libraries, including numpy, pandas, opencv-python, tensorflow, and keras, which would allow me to work with video frames, handle data, and build neural network models. I then prepared my dataset by downloading 12 videos from YouTube—4 videos for each gesture (clap, walk, and run), 3 for training the model and 1 for testing. After converting these videos to AVI format, I used this dataset to create and normalize pose landmarks.

Code Explanation

Step 1: Capturing Frame and Landmarks

The code imports cv2 for video processing, mediapipe for pose detection, and csv for data storage. Then, it initializes MediaPipe’s Pose model for landmark detection and a utility for drawing landmarks. By loading video and creating CSV file It opens a training video and creates a CSV file to store landmark data, with headers for each landmark’s x, y, z coordinates, and visibility across 33 landmarks. Processing frames, the code reads each frame, converts it to RGB for accurate landmark detection, and uses MediaPipe’s Pose model to process each frame and capture pose landmarks. Writing data to CSV, for each frame with detected landmarks, it collects the landmarks’ coordinates and visibility and appends them as a row in the CSV file.

Step 2: Normalizing Data

It imports pandas for handling the data in the CSV file. Then, it reads the CSV file containing pose landmarks and labels, preparing it for normalization.
The code adjusts each landmark’s position relative to the left hip landmark (landmark 23) to standardize pose data. By centering all other landmarks relative to a consistent body part, variations due to camera angle or person position are minimized. Finally, the normalized data is saved into a new CSV file. This ensures that all landmark data is aligned and standardized before training the model.

Step 3: Splitting into Training and Testing Sets

The code loads the newly saved CSV file with normalized data to prepare it for training and testing. It separates landmark data (features) from labels (the gesture being performed), which is essential for supervised learning. Using train_test_split from sklearn, the code splits the data into training and testing sets (80% for training and 20% for testing). This provides distinct sets to train the model and evaluate its accuracy on unseen data.

Step 4: Training the Neural Network Model

TensorFlow is imported to build and train the neural network model, a common framework for deep learning. The code defines a neural network model with two hidden layers (64 and 32 neurons each), designed to learn from the input landmarks and classify gestures. The model is compiled with the Adam optimizer and sparse categorical cross-entropy loss, both standard choices for classification tasks. The model is trained for 20 epochs on the training set and validated on the test set. This allows the model to learn gesture patterns and adjust based on the validation results. After training, the model is saved to a specified path. Saving the model allows it to be loaded later for predictions without retraining.

Step 5: Evaluating and Testing the Model

The model is evaluated on the test set, providing a measure of accuracy. This step validates how well the model generalizes to new data. The necessary libraries are re-imported, and the trained model is loaded for making predictions. A label map is created to translate the model’s numerical output to gesture labels (e.g., "clap", "walk", "run"). A new test video is loaded for live prediction of the gesture. The code processes each frame to detect landmarks, just as it did for data collection, and uses these landmarks to make predictions with the trained model. For each frame, the model’s prediction is displayed on the video, showing the detected gesture. The loop ends when the video is finished or when the 'Q' key is pressed.

Step 6: Terminating the program

The output is shown in a new window by pressing the Q button will end the video and close the new window that was open or that was used for the testing runs. To sum up, I built a dataset of pose markers from various motions after configuring the environment and downloading the required films. I then used unseen video data to test a neural network model that I had trained, and it recognized the movements with 100% accuracy. To finish the project, just press Q to turn off the video display.

Output:
![Screenshot 2024-11-12 102113](https://github.com/user-attachments/assets/c4cb0eff-f533-42ae-b2d5-6c026f274210)
        
![Screenshot 2024-11-12 102315](https://github.com/user-attachments/assets/5ba24625-e178-43be-b5c0-636ea09476b2)

link for github repositary:

This pose detection project's future scope presents a number of intriguing avenues for development and use. Here are five or six specific ideas for expanding and improving it:

1.Expansion to More Gestures and Activities: Adding more complex gestures and body movements can make the model versatile for a wider range of activities. This could include gestures specific to sports (e.g., basketball shots, yoga poses, swimming strokes) or daily activities (e.g., lifting objects, bending, sitting). Extending the gesture set would enable the model to be used in applications like fitness monitoring or rehabilitation exercises, where tracking specific movements is essential.

2.Integration with Real-Time Feedback Systems: Incorporating real-time feedback can make this project useful in scenarios requiring instant guidance. For example, a fitness app could analyze the user’s form and offer real-time suggestions for corrections during workouts, or a virtual personal trainer could provide instant feedback on posture. This could be extended to assist coaches or therapists working with people remotely.

3.Improving Accuracy with More Robust Data Collection: Gathering a larger, more diverse dataset covering different body types, backgrounds, lighting conditions, and camera angles can help the model generalize better. This improvement would make it more accurate and reliable across varied environments, allowing it to be used effectively in outdoor settings, different lighting conditions, or for people of all ages and sizes.

4.Use in Healthcare for Physical Therapy and Rehabilitation: The model could be fine-tuned to monitor specific rehabilitation exercises, ensuring patients follow prescribed movements correctly. By detecting subtle changes in posture and range of motion, the model could support physical therapists in tracking patient progress and identifying areas needing improvement, even in a remote setting.

5.Integration with Edge Devices and Wearables: Optimizing the model to run efficiently on edge devices (like mobile phones or IoT devices) or wearables (like smartwatches) can enable continuous pose detection on-the-go. This portability would open opportunities in applications like wearable fitness monitors, injury prevention systems in sports, or assistive technology for elderly people to alert caregivers about falls or unsafe movements.

6.3D Pose Estimation and Enhanced Visualization: Incorporating 3D pose estimation would allow the model to capture depth and accurately interpret complex body positions. This feature could make the model more useful in virtual reality (VR) or augmented reality (AR) applications, where 3D pose data is crucial. It could enhance user experience in VR gaming, improve interactivity in AR fitness applications, and enable more immersive educational tools for learning body mechanics.



        
