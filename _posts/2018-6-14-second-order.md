---
layout: post
title: New 2nd order gradient method beats SGD and ADAM on large models.
categories: SGD ADAM hyperparameter CIFAR ImageNet ResNet VGG-f Hessian 2-order
---

The paper brings 2-order optimization method to a comparable training speed with 1-order counterparts (SGD, ADAM).
2-order optimization method appears to be superior in terms of the final model performance,
as tested on CIFAR and ImageNet using ResNet and VGG-f, and did not require hyperparameter tuning.

The paper uses automatic differentiation to compute 2-order derivatives
(as opposed to just 1-order used in SGD), which are then used in 2-order optimization algorithm.
This paper's novel is a technique to avoid expensive matrix inversion by
computing an estimate once, and updating it later with a relatively cheap procedure.
This operation was a major roadblock for 2-order optimization methods.

paper: [Arxiv](https://arxiv.org/abs/1805.08095)
via [Reddit/ML](https://www.reddit.com/r/MachineLearning/comments/8lap1f/r_new_newton_solver_beats_sgd_and_adam_for_large/)