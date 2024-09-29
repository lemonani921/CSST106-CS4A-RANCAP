# Install the required dependencies:

!apt-get update
!apt-get install -y cmake build-essential pkg-config

!git clone https://github.com/opencv/opencv.git
!git clone https://github.com/opencv/opencv_contrib.git

!mkdir -p opencv/build
%cd opencv/build
!cmake -D CMAKE_BUILD_TYPE=RELEASE \
        -D CMAKE_INSTALL_PREFIX=/usr/local \
        -D OPENCV_ENABLE_NONFREE=ON \
        -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules \
        -D BUILD_EXAMPLES=OFF ..
!make -j8
!make install

1. SIFT Feature Extraction
SIFT (Scale-Invariant Feature Transform) is used for detecting local features in images.
![image](https://github.com/user-attachments/assets/f1c61884-7238-49e8-b25e-f208d6670d07)

2. SURF Feature Extraction
SURF (Speeded-Up Robust Features) is another local feature detector that builds upon SIFT but is faster in certain applications.
![image](https://github.com/user-attachments/assets/64ecfdad-851d-43a2-9d71-6e219936ed59)

3. ORB Feature Extraction
ORB (Oriented FAST and Rotated BRIEF) is a faster and more efficient alternative to SIFT and SURF, especially for real-time applications.
![image](https://github.com/user-attachments/assets/2bce39c2-deaa-403f-8582-3b5f084bf22e)

4. Feature Matching Using SIFT
In this task, two images are matched based on the features extracted using SIFT and the BFMatcher (Brute Force Matcher) method.
![image](https://github.com/user-attachments/assets/896bc2c8-c2e3-4b6d-b592-ccac08db53fb)

5. Image Alignment Using Homography and Feature Matching
By using good matches and applying the homography transformation, two images can be aligned for applications such as panorama creation.
![Uploading image.png…]()

Saving Feature Extraction Results to PDF
![Uploading image.png…]()
****
