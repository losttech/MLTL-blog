---
layout: post
title: Quickly learn something new, basing on past experience
categories: LSTM RNN reinforcement-learning RL meta-learning unsupervised MDP
---

Commonly, <a title="recurrent neural network" href="https://en.wikipedia.org/wiki/Recurrent_neural_network">RNNs</a>
are used to solve a specific task (e.g. how to play Go in AlphaGo), requiring a lot of data
(billions of self-play matches). Ultimately, we'd like a <span title="neural network">NN</span>, that can quickly
learn new tasks (e.g. Chess) with just a few examples by using experience with other tasks, like people do.

This paper proposes a way to that with some success.

Typically when reinforcement learning a task, RNN (as of now usually - <a href="https://en.wikipedia.org/wiki/LSTM">LSTM</a>)
gets the state of the environment as input (e.g. picture of the game board), and part of its own output from previous turn (via LSTM cells),
outputting an action to make (e.g. move queen).

This paper proposes a simple idea to add own action on the previous turn to inputs,
and, most importantly, the actual reward (game score), received on the previous turn for the previous action.

Authors show, that for a set of relatively simple tasks that enables new architecture to quickly adapt when task is changed,
e.g. like it is tasked to play Chess after playing Go for a while. They also show, that it
can later train itself on new tasks, without the need to adjust network weights like it is done during pretraining.
Instead, network just changes internal state in a way, that makes it perform the new task better.
That ability is introduced to the network by allowing it learn the history of getting rewards.

paper: [Arxiv](https://arxiv.org/abs/1611.05763)
via [HN](https://news.ycombinator.com/item?id=17216821)