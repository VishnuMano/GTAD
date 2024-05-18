# GTAD
Georgia Tech AutoDrive Localization Library (Research Suite + Benchmarking)

Dev Note: tradeoff between Visual Odometry and vSLAM is a tradeoff between performance, consistency, and simplicity in implimentation.

## Visual Odometry
### Description
- Estimating the pose of a camera by examining the changes that motion induces on the images.
- Identify features + track across different frames
- Benchmarked with KITTI Vision Suite
### Implementation
- Pipeline: Image Sequence -> Feature Detection -> Feature Matching Tracking -> Motion Estimation -> Local Optmization (Bundle Adjustment)
- Triangulation: camera path is computed incrementally (pose by pose) by determining the transformation that minimizes the reprojection error of the triangulated points in each image (factoring in scale ambiguity by calculating relative scale).
### Essential Matrix
- Computed directly from image coordinates (need atleast 5 point corrospondences)
- Decomposed into Rotation and Translation
- Results in 4 solutions
- E = K^TFK   |   E = [t]xR
- Note: loop detection utilizes similarities that are computed with global/local image descriptors

## vSLAM
- Goal of SLAM is to obtain a global, consistent estimate of the robot path.
- vSLAM is comprable to visual odometry with loop closing and global optimization.
- in progress ...
