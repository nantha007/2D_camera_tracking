# WriteUp 

## MP.1 - Dynamic Buffer size
To avoid memory error, dataBuffer vector which stores camera images is set to have maximum size of 3. After adding an image to the dataBuffer vector, the size of the buffer is checked. If the size is more than 3, first element of the vector is removed as it is the oldest loaded image in the vector. This ensure size of the dataBuffer vector is maintained at 3.

## MP.2 - Keypoint detection
To detect the keypoints, the standard keypoints detectors such as Shi-Tomasi, Harris, FAST, BRISK, ORB, AKAZE and SIFT are used. Three functions such as `detKeypointsHarris`, `detKeypointsModern` and `detKeypointsShiTomasi` are implemented in `matching2D_Student.cpp` file to detect keypoints.


## MP.3 - keypoint removal
Keypoints detected outside the preceding vehicle is removed using inbuilt function `contains` which gives whether a keypoint is inside the box or not.

## MP.4 Keypoint Descriptors
Keypoint descriptor algorithms such as BRISK, BRIEF, ORB, FREAK, AKAZE and SIFT are implemented in `descKeypoints` function `matching2D_Student.cpp` file.

## MP.5 Descriptor Matching
The file `matching2D_Student.cpp` has the function `matchDescriptors` to match the keypoint in the (n-1)th frame to nth frame. Brute force and FLANN are implemented while considering two types of decriptors such as Histogram of Gradients and Binary descriptors. To match the keypoints nearest neighbour and K-nearest neighrbours (KNN) implemented.

## MP.6 Descriptor Distance Ratio
In KNN method to match the keypoints, descriptor distance ratio of 0.8 is considered. This removes weaker keypoints. 

## MP.7 Performance Evaluation 1
Data for this evaluation is present in `Task_7.csv` file. Harris algorithm is faster but it generates least keypoints out of all other methods. FAST algorithm generates more keypoints than other methods while maintaining good speed.

## MP.8 Performance Evaluation 2
Total matches between each keypoint generator and descriptor is present in the file `Task_8.csv`. 

## MP.9 Performance Evaluation 3
Time taken for each keypoint detector and descriptor is logged and store in the file `Task_9.csv`. 
Top 3 pick from these pair of keypoint detector and keypoint decriptor is given below.
1. FAST detector and BRIEF descriptor.
2. FAST detector and SIFT descriptor.
3. FAST detector and ORB descriptor.

Since accuracy of the matching is not considered, best way to decide on top pairs is solely based on speed and number of matches. As it can be seen FAST detector and BRIEF generates more matches than any pair of detector and descriptor. It also faster than most pairs. FAST detector and SIFT descriptor and FAST detector and ORB descriptor is closely follows the first one. Thus these are my top 3 suggestion for detector and descriptor pairs. 

