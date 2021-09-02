---
date: 2021-09-02
title: "Introducing Spice.ai - open source, time series AI for developers"
type: blog
linkTitle: "Introducing Spice.ai - open source, time series AI for developers"
notoc: true
author: Spice AI ([@SpiceAIHQ](https://twitter.com/SpiceAIHQ))
---

We are three ex-Microsoft/GitHub engineers, and today, we are making [Spice.ai](https://spiceai.org), a new open source project that helps developers use AI to create intelligent applications, public on [GitHub](https://github.com/spiceai/spiceai). We're looking for feedback on the direction. It's not finished, in fact, we only just started in June, and we invite you on the journey.

Like many developer stories, it all started with a side-project. We were interested in [neurofeedback](https://en.wikipedia.org/wiki/Neurofeedback), a type of biofeedback therapy that reinforces healthy brain function but can cost up to $15,000. We wanted to make it accessible to more people, so we set out to build a system that leverages AI to deliver neurofeedback more cost-effectively. And as often many AI projects go, this turned out to be much more challenging than we first thought.

AI has recently seen some impressive advances, like with OpenAI developed [GPT-3](https://en.wikipedia.org/wiki/GPT-3) and [GitHub Copilot](https://www.linkedin.com/pulse/announcing-github-copilot-kevin-scott/). And at the same time, levering AI to make intelligent applications is still too hard. [@mrogati](https://twitter.com/mrogati)'s [Data Science Hierarchy of Needs](https://hackernoon.com/the-ai-hierarchy-of-needs-18f111fcc007) pyramid from 2017 _still_ illustrates it well. For developers, there are still too many unmet needs in leveraging ML to create intelligent applications. We faced the same AI development challenges many developers do; even though we had years of engineering experience at Microsoft and GitHub, there was still too much to learn and build. We simply didn't have the time, resources, or tools to utilize AI effectively in the project. After experiencing this pain ourselves, we saw an opportunity to make it better for everyone, created a repo on GitHub, and Spice.ai was born.

In the neurofeedback project, we worked with brain activity [EEG](https://en.wikipedia.org/wiki/Electroencephalographyhttps://en.wikipedia.org/wiki/Electroencephalography) data - time series data. We realized time series data applies to everything from health and biometrics to finance, sales, logistics, security, IoT, and application monitoring. The amount of time series data in these fields is growing exponentially, and extracting value from this data to make more intelligent software will determine the success of the next generation of applications.

We also realized that handling time series data is often sensitive, such as with health, financial, and security data. Instead of sending all data into a 3rd-party AI service, we needed the choice to bring AI to wherever our data and compute lived, either in the cloud, on-premises on or the edge.

### Spice.ai - a modern development experience and open source runtime for deep learning on time series data

Spice.ai is an open source, portable runtime for training and using deep learning on time series data. It's written in Golang and Python and runs as a container or microservice with applications calling a simple HTTP API. It's deployable to any public cloud, on-premises, and edge.

The vision for Spice.ai is to make creating intelligent applications as easy as possible for developers in their development environment of choice. Spice.ai brings AI development to their editor, in any language or framework with a fast, iterative, inner development loop, with continuous-integration (CI) and continuous-deployment (CD) workflows.

The Spice.ai runtime also includes a library of [community-driven components](https://github.com/spiceai/data-components-contrib) for streaming and processing time series data, with the vision of enabling developers to quickly and easily combine data with learning to create intelligent models.

[**spicerack.org**](http://spicerack.org) **- the Spice.ai package registry**

Modern developers build with the community by leveraging registries such as [npm](https://npmjs.org), [NuGet](https://nuget.orghttps://www.nuget.org/), and [pip](https://pypi.org/). The registry for sharing and using Spice.ai packages is [spicerack.org](https://spicerack.org). As the community shares more and more AI building blocks, developers can quickly build intelligence into their applications, initially with definitions of AI projects and eventually by sharing and reusing fully-trained models.

### Applying Spice.ai to real-world problems

We are already working with several companies on Spice.ai pilots to develop intelligent applications, such as optimizing in-store pickups for a large online retailer and scheduling optimizations for healthcare workers and resources. We've had interest in use cases from suspicious login detection to intelligent cloud spend analysis and order routing for a food delivery app. And a personal interest of ours, stock and crypto trading.

### Alpha software

The vision to bring intelligent application development to the maturity of modern web development is a vast undertaking. We started working on it in June with three engineers, and we haven't figured it all out or solved all the problems yet.

Spice.ai and [spicerack.org](http://spicerack.org) are both pre-release, early, alpha software. Spice.ai v0.1-alpha has many gaps, including limited deep learning algorithms and training scale, streaming data, simulated environments, and offline learning modes. Packages aren't searchable or even listed on [spicerack.org](http://spicerack.org) yet. See what features are upcoming and the problems we are solving next on the [Spice.ai Roadmap](https://github.com/spiceai/spiceai/blob/trunk/docs/ROADMAP.md).

## Learn more and contribute

You can read more about Spice.ai on the project page at [spiceai.org](https://spiceai.org) and get started with quickstarts at [github.com/spiceai/quickstarts](https://github.com/spiceai/quickstarts).

The goal is to make it easier for developers to create intelligent applications, and we'd love your feedback on the direction. If the vision resonates with you, we invite you to join us on the journey.

Get in touch on [Discord](https://discord.com/channels/803820740868571196/803820740868571199) or reach out on [Twitter](https://twitter.com/0xlukekim). We are also [hiring](https://spiceai.io/careers).

Luke, Phillip, and Lane - Spice.ai project founders
