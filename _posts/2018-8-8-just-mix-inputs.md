---
layout: post
title: You can blend two images and use result as a new training example
categories: CNN mixup NN
---

The core idea for this post is actually from 2017, and it is very unexpected and impressive.

## Blend them

For many ML problems insufficiency of training data is a huge roadblock. For example,
if you have 1000 images and 100 objects on them, that's 10 image examples per object,
which is not enough to train many previous models.

In 2017, there was a surprising discovery, that you can get a meaningful benefit when training
a convolutional neural network, if in addition to the 1000 images you have, you feed the network
with linear combinations (e.g. blending together two or more images) of them. To train with the
blended image, you set the expected output of the network to the same linear combination of classes.
For example, if you are trying to classify horses and dogs, and blend images of a horse and a dog
with factors 0.6 and 0.4 respectively, you set the expected output to be (0.6, 0.4) rather than
(1, 0) or (0, 1) for unblended examples.

That gives you essentially infinite amount of training data, as you can pick any n images,
and blend them together. However, at some point you will see diminishing returns from this technique.

## Advances

The reason I decided to write about this (in addition to this being an awesome and unexpected result)
is that there have been some papers published recently, that improve the effect.

In particular, there is a new paper, that suggests to perform blending at random layers
of a neural network. In that sense, one can consider the original idea to be a special case,
the random layer always being the input layer of the network.

So what you do is:
- pick a layer in NN
- compute outputs of that layer for all images in the batch
- build linear combinations/blends of these outputs as suggested in part 1
- feed them to the subnetwork after the choosen layer, appropriately mixing the expected outputs

In the author's experiments on CIFAR-10 (accuracy):
No mixup = 94.88
Simple blend from part 1 = 96.498
Advanced mixup = 97.10


paper: [Arxiv](https://arxiv.org/abs/1806.05236)
via [Reddit/MachineLearning](https://www.reddit.com/r/MachineLearning/comments/8xz63l/r_manifold_mixup_encouraging_meaningful/)