---
date: 2021-11-25
title: "Processing data for intelligent apps is hard, Spice.ai makes it easy"
type: blog
linkTitle: "Processing data for intelligent apps is hard, Spice.ai makes it easy"
author: Phillip LeBlanc ([@leblancphill](https://twitter.com/leblancphill))
---

One of the challenges with developing apps powered by AI is that writing the logic to process the data to feed the AI is complex and time-consuming. Spice.ai makes this easy by using standard data connectors and combining the training and usage of the AI into the same workflow.

### Why is data necessary?

If you're a developer, you probably build intelligence into your app every day without realizing it - and used data to do so. If you've ever performed an A/B test to see which version of a website works better - you just used data to make your website more intelligent. If you've ever looked through your app's logs and found a behavior that wasn't supposed to happen and then fixed it - that's another place you used data to make your app more intelligent.

One critical difference with an intelligent app that leverages AI is it can learn from data and experience on its own, without help from a human. It is also possible to build entirely new classes of applications that are infeasible to write code.

### Why is processing data hard?

Integrating AI into your application is challenging because getting the data and processing it into the format an AI can understand is difficult. This data processing is similar to how a compiler translates the code you write into machine code. Your machine only understands 1s and 0s; it doesn't understand what an if statement or a function is. Like a code compiler, you will need to write a data compiler that works for your specific data and "compiles" it to a format the AI can learn from. The data compilation often involves simple techniques, such as [data normalization/standardization](https://deepchecks.com/glossary/normalization-in-machine-learning/) or cleaning the data to fill in or remove missing elements, and can include more advanced techniques like [embeddings](https://www.toptal.com/machine-learning/embeddings-in-machine-learning).

What makes this worse is that you will likely need to write this data compiler twice. To understand why let's talk about the two phases of AI: Training and Production.

### Two Phases: Training and Production

The standard way to create good AI is by splitting the work into a training phase and a production phase. The training phase will improve the neural networks, or the brain, of the AI to produce what is known as a model, or a "compiled" neural network. To understand how the training phase works more in-depth, this talk "[Machine Learning Zero to Hero](https://www.youtube.com/watch?v=VwVg9jCtqaU)" is an excellent resource explaining neural networks and how to train them.

The production phase is when you take the AI model you trained and integrate that with your production app. The AI model conceptually becomes an intelligent function in your app that you can call to get an output based on the current data. This function call is called inferencing in the AI world, and in [Spice.ai](http://Spice.ai) we call this a [recommendation](https://docs.spiceai.org/concepts/recommendations/).

Most of the training for AI is today done in Python due to the broad ecosystem support for AI frameworks and libraries. So you will need to write the data-compiler code for Python to support the training. If you develop your production app in a language other than Python, you would need to rewrite the data-compiler logic in that language to get the data in the correct format for inferencing. So now you are responsible for maintaining two copies of the same logic across two different coding languages and ensuring they stay consistent and evolve together.

### Spice.ai combines both phases

Spice.ai handles this challenge by combining the training phase and production phase into the same workflow. By defining your Spicepod to describe which data to collect and where to get it, Spice.ai will handle the data-compilation step in a way that is consistent across both training and in production. Running Spice.ai next to your application, you can be sure the same code that transformed the data during training is now changing the data in real-time to feed into the AI model to get recommendations for your app.

### Learn more and contribute

Building intelligent apps that leverage AI is still way too hard, even for advanced developers. Our mission is to make this as easy as creating a modern web page. If the vision resonates with you, join us!

Our [Spice.ai Roadmap](https://github.com/spiceai/spiceai/blob/trunk/docs/ROADMAP.md) is public, and now that we have launched, the project and work are open for collaboration.

If you are interested in partnering, we'd love to talk. Try out [Spice.ai](https://spiceai.org), [email us](mailto:hey@spiceai.io) "hey," get in touch on [Discord](https://discord.gg/kZnTfneP5u), or reach out on [Twitter](https://twitter.com/SpiceAIHQ).

We are just getting started! 🚀

Phillip
