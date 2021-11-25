---
date: 2021-11-25
title: "Thinking in data"
type: blog
linkTitle: "Thinking in data"
author: Phillip LeBlanc ([@leblancphill](https://twitter.com/leblancphill))
---

Data is the fuel that powers AI. You can create an AI agent that uses all the latest state-of-the-art algorithms and techniques, but without high quality data the AI will become little more than a random number generators. Intelligent applications are applications that learn from data. In a previous post, we described how Spicepods are used to describe to Spice.ai **what** it should learn. In a traditional ML system, this might be labeling the data to show the AI what it should learn. Once you've told your AI what to learn, the mechanism it uses to actually learn is by applying its algorithms to data.

### Which data? How much?

The data you give to the AI should be relevant to what you told the AI to learn. Weather data for Cairo is likely not useful for training an AI to learn to recommend ingredients for a new delicious food recipe. However, traffic data for Seattle will be very relevant for an AI learning to recommend good travel routes within Seattle. The amount of data that is required for an AI to learn properly roughly depends on how generalizable you want the AI to become. Training an AI agent that is good at filtering spam emails for everyone requires exponentially more data than one that would work well just for your inbox. The generalized language model GPT-3 was [trained on over 45TB](https://arxiv.org/pdf/2005.14165.pdf) of plaintext data!

### Let's create some AI!

Now let's pretend you are going to create an AI model using traditional techniques. You first need to tell the AI what to learn and then gather the data it will need to actually learn. Once you've done that, you now have the challenge of transforming this raw data into a format that the AI algorithm will be able to use. All AI algorithms can only work on numbers, so you will need to transform any text data to be represented by a number. And the numerical input data usually should be normalized/scaled to have values close to 0.

<div style="display: flex; justify-content: center; padding: 5px;">
  <div style="display: grid;">
    <img style="max-width: 763px; margin: auto" alt="Normalizing raw data" src="https://user-images.githubusercontent.com/879445/143444871-92d84a64-f3f5-4592-9254-f410e423d3dc.png">
    	<div style="font-style: italic; text-align: center;">Figure 1. Processing data into an AI friendly format.</div>
  </div>
</div>

Getting closer! Now you've got your text data converted to numbers, your numerical data normalized and scaled properly and you can begin training! Let's skip all of the complexity around training the model, and assume you get a high quality model at the end.

### Deploy to production 🚀

Now it's time to deploy this model into production. One of the challenges that will immediately arise when trying to apply AI in production is figuring out how to collect and transform the data that your model needs into the input format that your model is expecting. Remember all that pre-processing you did for training? The converting text to numbers, data normalization and scaling? You need to integrate this exact same logic into your production app so that you can get the data into the format your model expects. What a headache! If you did your initial data processing work using Python and your app is written in another language, it takes a lot of work to rewrite the data gathering and processing logic into the new language. What happens when the environment changes over time and your AI is no longer as intelligent as it used to be? You need to dust off those old Python scripts you used initially and gather new data to train a new model. You can imagine this quickly becoming a full time job for someone - and this is in fact a large part of what data scientists do. But even with a team of data scientists to help, someone still needs to integrate the model and data collection/processing code into the production app.

### There is a better way

As a developer, you want to be thinking about how to make your app more intelligent, not the low-level details of data gathering and processing. This is why Spice.ai handles the tedious code for processing the data into a format the model will be able to understand. You still need to think about the type of data that is relevant and write the Spicepod manifest that describes which data to collect and where to get it. And because Spice.ai is designed from the ground up to be a real-time system, it can get new data as it becomes available. Deploying your trained Spicepod into production is as simple as starting up the Spice.ai runtime next to your application with the trained Spicepod. The same code that transformed the data for training is now transforming your production data to feed into the AI algorithm for its up-to-date recommendations. And since Spice.ai works over HTTP calls, it doesn't matter which language your production app is in - you can rest assured that your data collection code remains the same and you didn't need to convert it to another language.

### Learn more and contribute

Building intelligent apps that leverage AI is still way too hard, even for advanced developers. Our mission is to make this as easy as creating a modern web page. If the vision resonates with you, join us!

Our [Spice.ai Roadmap](https://github.com/spiceai/spiceai/blob/trunk/docs/ROADMAP.md) is public, and now that we have launched, the project and work are open for collaboration.

If you are interested in partnering, we'd love to talk. Try out [Spice.ai](https://spiceai.org), [email us](mailto:hey@spiceai.io) "hey," get in touch on [Discord](https://discord.gg/kZnTfneP5u), or reach out on [Twitter](https://twitter.com/SpiceAIHQ).

We are just getting started! 🚀

Phillip
