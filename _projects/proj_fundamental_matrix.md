---
layout: page
title: 2 View Fundamental Matrix Estimator
description: CSE252B - Computer Vision II - Final Project
img: assets/img/cse252b/cover.png
importance: 2
category: Projects
---

Within <a href="https://cseweb.ucsd.edu/classes/wi23/cse252B-a/">CSE 252B:
Computer Vision II</a>, I developed an end-to-end pipeline capable of estimating
the fundamental matrix of 2 source images.

# Feature Detection

Feature Detection was done by implementing the
<a href="https://en.wikipedia.org/wiki/Corner_detection#Scale-space_interest_points_based_on_the_Lindeberg_Hessian_feature_strength_measures">Shi-Tomsai
Corner Detector</a> with non-maximal suppression of the minor eigenvalue image,
as well as the
<a href="https://cseweb.ucsd.edu/classes/sp02/cse252/foerstner/foerstner.pdf">Forstner
Point Operator</a> for sub-pixel coordinates.

<div class="row">
    <div class="col-sm-1 mt-3 mt-md-0">
    </div>
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse252b/corner_detect.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-1 mt-3 mt-md-0">
    </div>
</div>
<div class="caption">
  Sub-Pixel corner features
</div>

# Feature Matching

Putative Feature Matching was accomplished by brute-force cross-correlation
feature matching, filtering by correlation-coefficient thresholding, as well as
correlation-coefficient uniqueness (relative to the 2nd highest correlation
value). Bilinear interpolation was done due to account for sub-pixel feature
coordinates.

<div class="row">
    <div class="col-sm-1 mt-3 mt-md-0">
    </div>
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse252b/putative_matches.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-1 mt-3 mt-md-0">
    </div>
</div>
<div class="caption">
  Feature correspondences
</div>

# Outlier Rejection

Poor feature correspondences were removed by an implementation of the
<a href="https://en.wikipedia.org/wiki/Random_sample_consensus#Development_and_improvements">M-Estimator
Sample Consensus (MSAC)</a> algorithm. To estimate the Fundamental Matrix, the
<a href="https://users.cecs.anu.edu.au/~u5535909/revisit_fundamental.pdf">Seven-Point
algorithm with Direct Linear Transform</a> was used with Sampson Error.

<div class="row">
    <div class="col-sm-1 mt-3 mt-md-0">
    </div>
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse252b/outlier_rejection.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-1 mt-3 mt-md-0">
    </div>
</div>
<div class="caption">
  Feature correspondences inliers
</div>

# Linear Estimate of the Fundamental MAtrix

Using the
<a href="https://users.cecs.anu.edu.au/~u5535909/revisit_fundamental.pdf">Direct
Linear Transform Algorithm</a> and all inlier point correspondences, the
Fundamental Matrix was estimated.

# Non-Linear Estimate of the Fundamental Matrix

Using two-view triangulation, the 2d point correspondences can be corrected
(using the linear estimate of the Fundamental Matrix) and converted to 3d
points. Then, by assuming
<a href="https://en.wikipedia.org/wiki/Camera_matrix#Normalized_camera_matrix_and_normalized_image_coordinates">canonical
camera</a> coordinates, a non-linear estimate of the second projection matrix
can be computed.

To obtain the best estimate, the projection matrix was parameterized into an
11-dimensional space, optimized using the non-linear
<a href="https://en.wikipedia.org/wiki/Levenberg%E2%80%93Marquardt_algorithm">Levenberg-Marquardt
Algorithm</a>, and lastly unparameterized back as a 4x3 projection matrix.

Lastly, using the non-linear estimate of the Fundamental Matrix, the
point-to-epipolar-line correspondences can be visualized using some salient
features from the source image.

<div class="row">
    <div class="col-sm-1 mt-3 mt-md-0">
    </div>
    <div class="col-sm-10 mt-3 mt-md-0">
        {% include figure.html path="assets/img/cse252b/point_and_line.png" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-1 mt-3 mt-md-0">
    </div>
</div>
<div class="caption">
  Point and corresonding epipolar line
</div>
