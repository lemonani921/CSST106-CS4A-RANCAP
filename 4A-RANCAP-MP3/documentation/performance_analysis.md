
# **Performance Analysis**

## **Code:**
```python
# Function to analyze the performance of keypoint detection
def analyze_performance(detector_name, keypoints, descriptors, elapsed_time):
    print(f"{detector_name} Performance:")
    print(f"Number of keypoints detected: {len(keypoints)}")
    print(f"Descriptor size: {descriptors.shape if descriptors is not None else 'None'}")
    print(f"Time taken: {elapsed_time:.4f} seconds")
    print("="*50)

# Analyze SIFT performance
start_time = time.time()
keypoints1_sift, descriptors1_sift = sift.detectAndCompute(image1, None)
elapsed_time_sift = time.time() - start_time
analyze_performance("SIFT", keypoints1_sift, descriptors1_sift, elapsed_time_sift)

# Analyze SURF performance
start_time = time.time()
keypoints1_surf, descriptors1_surf = surf.detectAndCompute(image1, None)
elapsed_time_surf = time.time() - start_time
analyze_performance("SURF", keypoints1_surf, descriptors1_surf, elapsed_time_surf)

# Analyze ORB performance
start_time = time.time()
keypoints1_orb, descriptors1_orb = orb.detectAndCompute(image1, None)
elapsed_time_orb = time.time() - start_time
analyze_performance("ORB", keypoints1_orb, descriptors1_orb, elapsed_time_orb)

# Brute-Force Matcher vs FLANN Matcher Performance
def analyze_matcher_performance(matcher_name, matches, elapsed_time):
    print(f"{matcher_name} Matcher Performance:")
    print(f"Number of matches: {len(matches)}")
    print(f"Time taken for matching: {elapsed_time:.4f} seconds")
    print("="*50)

# Brute-Force Matching performance (SIFT)
start_time = time.time()
matches_sift_bf = bf.match(descriptors1_sift, descriptors2_sift)
elapsed_time_bf = time.time() - start_time
analyze_matcher_performance("Brute-Force", matches_sift_bf, elapsed_time_bf)

# FLANN Matching performance (SIFT)
start_time = time.time()
matches_sift_flann = flann.knnMatch(descriptors1_sift, descriptors2_sift, k=2)
elapsed_time_flann = time.time() - start_time
analyze_matcher_performance("FLANN", matches_sift_flann, elapsed_time_flann)

# Compare effectiveness of Brute-Force vs FLANN
def compare_matchers(bf_matches, flann_matches):
    print("Brute-Force Matcher vs FLANN Matcher:")
    print(f"Brute-Force Number of Matches: {len(bf_matches)}")
    print(f"FLANN Number of Matches: {len([m for m, n in flann_matches if m.distance < 0.75 * n.distance])}")
    print("="*50)

compare_matchers(matches_sift_bf, matches_sift_flann)
```

## **Results:**
```
SIFT Performance:
Number of keypoints detected: 119
Descriptor size: (119, 128)
Time taken: 0.1425 seconds
==================================================
SURF Performance:
Number of keypoints detected: 366
Descriptor size: (366, 64)
Time taken: 0.2204 seconds
==================================================
ORB Performance:
Number of keypoints detected: 322
Descriptor size: (322, 32)
Time taken: 0.0061 seconds
==================================================
Brute-Force Matcher Performance:
Number of matches: 61
Time taken for matching: 0.0478 seconds
==================================================
FLANN Matcher Performance:
Number of matches: 119
Time taken for matching: 0.1131 seconds
==================================================
Brute-Force Matcher vs FLANN Matcher:
Brute-Force Number of Matches: 61
FLANN Number of Matches: 4
==================================================
```

