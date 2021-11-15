---
date: 2021-11-15
title: "Challenges of Reinforcement Learning in Spice.ai"
type: blog
linkTitle: "Challenges of Reinforcement Learning in Spice.ai"
author: Corentin Risselin
---

At Spice.ai we are striving to bring a new AI-based technology to create products that can easily be trained and deployed. [A previous post](/posts/2021/11/15/teaching-apps-how-to-learn-with-spicepods/) introduced Spicepods: a declarative way to create AI product with Spice.ai technology. There are many new libraries and platforms aiming at this, Spice.ai choosed to focus on time series first and [Reinforcement Learning](https://en.wikipedia.org/wiki/Reinforcement_learning) as real-life processes are commonly time dependend and label data for [supervised learning](https://en.wikipedia.org/wiki/Supervised_learning) can be very expensive.

In this post we will address the challenges and some leads for the technology we are looking to create.

## Time Series Challenges

Time series is a very common challenge in the recent years for neural networks, this is a good things as there is a very extensive litterature on the subject but this also make the task of building a product complex as there are many algorithms and approaches to explore. **It is very likely that not a single approach of time series will be a silver bullet that will be able to solve all problems.**

The first challenge of time series is the data itself. The shape/length is usually variable and can even be potentially infinite (real-time stream of data). This doesn't suit a lot of machine learning approaches as the volume of data that is needed to process can be too much for simple and efficient approaches such as [Decision Trees](https://en.wikipedia.org/wiki/Decision_tree). Deep Learning is very popular to process such data, there are several types of neural network that has been shown to work, let's review some of the common classes:

* [Convolutional Neural Networks (CNN)](https://en.wikipedia.org/wiki/Convolutional_neural_network): CNNs can only accept data with a fixed length: even with the ability to pad the data, this is a major drawback as the time window needs to be decided. Despite this limitation their are the most efficient network to train (computation, data needed, time) and the usually the smalles in storage. CNNs are very robust and also used in image/video processing, this makes them a very good baseline to start with while also having a lot of refined and mature improvement developped over the years like the very efficient MobileNet with depthwise convolutions.

* [Recurrent Neural Networks (RNN)](https://en.wikipedia.org/wiki/Recurrent_neural_network): RNNs have been researched for several decades, they aren't as fast to train as CNNs but can be faster to use as there is no need to feed a while time window like CNN if the desired input/output is in real-time (or alike, in a continuous fashion, also called `online`). RNNs are proven to be very good in some situations and a lot of new models are being discovered.

* [Transformers](https://en.wikipedia.org/wiki/Transformer_(machine_learning_model)): Popularized in the famous paper [`Attention is all you need`](https://arxiv.org/pdf/1706.03762.pdf), transformers has been shown to be flexible with many variations that output great results (Vision Transformers, Perceiver, etc). Most of state-of-the-art results today has been made fom transformers and their variations, they are very good at correlating sparse information. They suffer in a way the same limitation as CNN for the length of their input (fixed at training time) but they also have a disadvantage to not scale well with the size of the data (quadratic growth with the length of the time series). They are also the most expensive network to train in general.

Those classes of neural networks do not represent all the possibilities but **potential paths for Spice.ai to build its technology to process time series data**. There are many other paradigms that can be very interesting to explore like Memory Augmented Neural Networks (MANN) or neural network based Genetical Algorithms.


## Reinforcement Learning Challenges

RL has been growing very steadily, especially for robotic applications, the topic is very popular for its potential applications and development processes. Usually RL doesn't involve as much data process as Supervised Learning, manipulating huge amount of data can be quiet demanding for the hardware and people alike. RL feels much more dynamic: we are training agent that doesn't only aim at replicating behaviours/outputs but explores and 'optimizes' its environement.

Most of today research is base on environements the agent can interact with during the training process. In fact most of the time the most efficient to have multiple agent/environement pairs training together and sharing their experiences. Having an environement to interact with is very helpfull try differenct actions from the agents from the actual state of learning: **on-policy learning**; while past experiences from them or bootstrap data can also be used, without the need of the environement:**off-policy learning**.

At the time of writting those lines, Spice.ai is not meant to be used with an environement (wither pre-made or given by the user). **This makes off-policy learning the only possibility.** Despite limiting the exploration of agents the good size of this can be be seen as a strenght as:

* Creating environements has its downside: it can be difficult and/or expensive to create a model of the real-world, sometime even impossible.

* Off-policy learning is usually way more efficient than on-policy (time/data and computation).

In conlusion Spice.ai approach of RL can be described as 'Data-Driven', this is a very exciting domain with some research already paving the way for us to grow. Reading some research from [Berkeley Artificial Intelligence Research](https://bair.berkeley.edu/)'s blog can show the potential of this particular field. There are many other research entity that made great discoveries like [DeepMind](https://deepmind.com/), [OpenAI](https://openai.com/), [Facebook AI](https://ai.facebook.com/) and [Google AI](https://ai.google/) (amongs many others). All of the research in RL is a great inspiration for us to build our future technology, if you are Reinforcement Learning we recommend you to read some of their blog posts, come discuss with us on [discord](https://discord.gg/kZnTfneP5u), reach out on [Twitter](https://twitter.com/SpiceAIHQ) or [email us](mailto:hey@spiceai.io).


Corentin
