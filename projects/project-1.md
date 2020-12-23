---
layout: project
type: project
image: images/meteor_shower_icon.png
title: Meteor Shower
permalink: projects/meteor_shower
# All dates must be YYYY-MM-DD format!
date: 2020-11-08
labels:
  - Machine Learning and AI
  - Reinforcement Learning
  - Genetic Algorithms
  - Neural Networks
  - Python
summary: Little red squares learn to avoid "meteors" with the help of machine learning.
---

Source: <a href="https://github.com/alexeygorskiy/meteor_shower"><i class="large github icon"></i>alexeygorskiy/meteor_shower</a>

<h1>Problem Description</h1>
The goal of this project was to design an environment where little red squares (envisioned as spaceships in space) learn to avoid little grey squares (envisioned as meteors). Below is a demonstration of the best individual after 20 generations of training:

<video width="330" height="395" controls>
    <source src="../images/bestof_gen20_14s.mp4" type="video/mp4">
  Your browser does not support the video tag.
</video>

<h1>Below are snapshots of the whole population every fifth generation as well as the best individual of that generation:</h1>

**Generation 0**
<video width="330" height="395" controls>
  <source src="../images/gen0_8s.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

<video width="330" height="395" controls>
  <source src="../images/bestof_gen0_1s.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

**Generation 5**
<video width="330" height="395" controls>
  <source src="../images/gen5_13s.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

<video width="330" height="395" controls>
  <source src="../images/bestof_gen5_4s.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

**Generation 10**
<video width="330" height="395" controls>
  <source src="../images/gen10_16s.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

<video width="330" height="395" controls>
  <source src="../images/bestof_gen10_6s.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

**Generation 15**
<video width="330" height="395" controls>
  <source src="../images/gen15_25s.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

<video width="330" height="395" controls>
  <source src="../images/bestof_gen15_7s.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

**Generation 20**
<video width="330" height="395" controls>
  <source src="../images/gen20_52s.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

<video width="330" height="395" controls>
  <source src="../images/bestof_gen20_14s.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>


<h1>How It Works</h1>
The red squares die if they are hit by one of the grey squares. However, the red squares can “see” a certain distance around themselves:

<img class="ui large centered rounded image" src="../images/spaceship_img.png">

If a grey square overlaps with one of the blue points, the red square will know that and will be able to decide where to move based on that. The red square will also know if one of the blue points is outside the bounds of the map. To be able to make decisions the red square is equipped with a neural network that takes the state of the blue points as inputs and outputs a decision:

<img class="ui medium centered rounded image" src="../images/neural_network.png">

The outputs can either be -1, 0 or 1. The numbers correspond to whether to decrease, leave unchanged or increase a coordinate. Output 1 controls the x-coordinate and output 2 the y-coordinate. If for example both outputs are ones, then the red square will move towards north east.
The red squares are rewarded based on how long they survive. When all the red squares die, the current generation ends and the squares that survived the longest are chosen as parents for the next generation. The weights of the parents’ neural networks are combined to produce new networks for the next generation.

Over many generations the red squares evolve through the process of artificial natural selection to eventually avoid the grey squares. In the end they become much better than a human at achieving the given task.

By adjusting the reward function, network topology and the genetic algorithm, the squares can learn to solve other problems as well, such as chasing the grey squares (could be envisioned as food), navigating a track and many more.

<video width="330" height="395" controls>
  <source src="../images/food_problem_30s.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>

<video width="330" height="330" controls>
  <source src="../images/track_problem_34s.mp4" type="video/mp4">
Your browser does not support the video tag.
</video>
