# Exploring the images

hypothesis considered:
there are images where hands or legs are raised/folded so we cannot rely on the wrist, elbow, knee, ankle, etc.
so i've considered only using coordinates of fixed landmarks like nose, ear,shoulder and eyes.

### Annoted data for head in the images using labelImages.
- Made dataframe from annotation.
- 4 new cols viz, Head_x, Head_y, Head_w, Head_h, created
- other key points hold no significance so only coordinates of bbox of head annoted.


# Exploring height and pose dataset

- pose column contains several metadata
- so we will create other feature out of that col.

# Feature Engineering

Pose col in our main dataset is a dataset itself.
so extracted different column from itself.
so that it will be a valid data for training the model.
Finally after merging datasets, there are 35 cols
		'Coord_x', 'Coord_y', 'Coord_w', 'Coord_h', 
            'bbox_confidence_score', 'body_pose_score',
            'Nose_x', 'Nose_y', 'Left_eye_x','Left_eye_y', 
            'Right_eye_x', 'Right_eye_y','Left_ear_x', 'Left_ear_y',
		'Right_ear_x', 'Right_ear_y','Left_shoulder_x', 
		'Left_shoulder_y', 'Right_shoulder_x','Right_shoulder_y', 
		'Left_hip_x', 'Left_hip_y', 'Right_hip_x',
		'Right_hip_y', 'Nose_p', 'Left_eye_p', 'Right_eye_p', 
		'Left_ear_p', 'Right_ear_p', 'Left_shoulder_p',
            'Right_shoulder_p', 'Left_hip_p', 'Right_hip_p'
		'Depthmap Image', 'Height(cm)', 'Head_x',
		'Head_y', 'Head_w', 'Head_h'
		* Here cols with p suffix are probability score of detecting landmarks.

# Data Preprocessing

since the quantity of data is very small.
so I've trained it on all the data

here target variable is Height(cm)
and rest are the independent variables(excluding 'Depthmap Image')
Depthmap Image is a name of the image file, so it holds no significance

# Model Training
used Random Forest regressor.
basically when there are so many variables and the difference in value is slightly 
difference like the coordinates of nose differ slighly in value in different images.
so in that case ensemble based algorithms work better.

# Prediction

For the sake of testing purpose.
I've used a observation from our dataset.
where actual height is 100.6 cms.
and our model predicted 97.78 cms

pretty close. it only differ by 3.4 cms.

refer height_prediction.ipynb file for details.
