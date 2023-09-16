---
layout: page
title: Amazon Shoe Recommender System
description: CSE 158 - Recommender Systems - Final Project
img: assets/img/cse158/cover.png
importance: 3
category: Projects
---

<header class="post-header">
  <h1 class="post-title">
  <a href="/assets/pdf/CSE158_Assignment_2_Report.pdf" target="_blank" rel="noopener noreferrer" class="float-left"><i class="fas fa-file-pdf"></i></a>
  </h1>
  <p class="post-description">Report</p>
</header>

In <a href="https://cseweb.ucsd.edu/classes/fa21/cse258-b/">CSE 158 - Recommender Systems</a>, as a part of my final project, I worked within a team to develop a computer vision and collaborative filter shoe recommender based around an <a href="https://arxiv.org/abs/1506.04757">Amazon co-purchase dataset</a>. 

The model was trained to predict co-purchase behavior (e.x. given anonymized user X bought Y, how likely they are to buy Z). Furthermore, it is also evident from fashion trends that the visual appearance of an item will also influence whether or not the item is co-purchased, similar to a user's previous shopping trends.

# Non-Visual Model

A non-visual model was constructed using a Factorization Machine of the dataset features.

# Visual Model

Our visual model was trained using additional image embedding features, obtained by extract last-layer representations of passing the images through AlexNet. Then, the Mahalobis distance of image similarities (k=1, 10. 100) were learned and passed into a Binary Classifier using a modified sigmoidal activation function, trained using PyTorch Lightning. 

<br>

<table class="table b">
  <thead>
    <tr>
      <th scope="col">Hyperparameter</th>
      <th scope="col">Accuracy</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>K=1</td>
      <td>0.8576</td>
    </tr>
    <tr>
      <td>K=10</td>
      <td>0.9369</td>
    </tr>
    <tr>
      <td>K=100</td>
      <td>0.7602</td>
    </tr>
  </tbody>
</table>

<br>
<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
      {% include figure.html path="assets/img/cse158/pos_a.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
      {% include figure.html path="assets/img/cse158/pos_b.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
      {% include figure.html path="assets/img/cse158/cover.png" class="img-fluid rounded bg-light z-depth-1" %}
    </div>
</div>
<div class="row">
    <div class="col-sm-4 mt-3 mt-md-0">
      {% include figure.html path="assets/img/cse158/neg_a.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
      {% include figure.html path="assets/img/cse158/neg_b.jpg" class="img-fluid rounded z-depth-1" %}
    </div>
    <div class="col-sm-4 mt-3 mt-md-0">
      {% include figure.html path="assets/img/cse158/acc_plots.png" class="img-fluid bg-light rounded z-depth-1" %}
    </div>
</div>