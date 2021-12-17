---
date: 2021-12-17
title: "What types of applications can you build with Spice.ai?"
type: blog
linkTitle: "What types of applications can you build with Spice.ai?"
author: Phillip LeBlanc ([@leblancphill](https://twitter.com/leblancphill))
---

If you've taken a look at the Spice.ai project and are curious about the types of intelligence you can enable for your applications, you've found the right post!

At its core, Spice.ai is a powerful decision recommendation engine that learns how to recommend decisions to optimize for a goal specific for your application. Spice.ai learns through combining real-time data streams, your application's decisions, and a reward function that defines the goal you want.

As Spice.ai trains on more data, the decisions it recommends become better. Let's explore this topic in more detail and see the types of applications Spice.ai could help you build!

## Spice.ai enables applications to make intelligent decisions.

The idea to make intelligent decision-making applications is not new. Developers first created these applications around the 1970s, and it is one of the earliest examples of using Artificial Intelligence to solve real-world problems.

These first intelligent applications were called "[expert systems.](https://en.wikipedia.org/wiki/Expert_system)" One of the traits of expert systems is that they encode some form of human expertise for automatic decision-making. One famous example of this type of system in use was the control system used by NASA's [Space Shuttle Mission Control](https://www.researchgate.net/publication/4702412_The_INCO_Expert_System_Project_CLIPS_in_Shuttle_mission_control).

<div style="display: flex; justify-content: center; padding: 5px; margin-bottom: 20px;">
  <div style="display: grid;">
    <img style="max-width: 563px; margin: auto" alt="Normalizing raw data" src="https://user-images.githubusercontent.com/879445/146541154-fb7d9ec8-482e-4d07-9227-34ca74abaff0.jpg">
    	<div style="font-size: 0.8rem; font-style: italic; text-align: center;">The flight controller for the Space Shuttle was powered by an expert system. Photo: NASA</div>
  </div>
</div>

While you might not be writing the control system for modifying the trajectory of a rocket in flight, you can still use Spice.ai to create applications that need to make automated decisions. (However, if anyone from SpaceX is reading this, let's talk 😉)

## Examples of decision-making applications

### Intelligent Auto-scaling

Let's explore some of the types of applications you can build with Spice.ai. Imagine you are the architect of a cloud SaaS product constructed from micro-services. Your customers expect that your service is always available and feels snappy. It is possible to over-provision the capacity of your services to ensure that your customers have a great experience even during peak load. Yet, your boss might not appreciate the AWS bill that comes each month. Autoscaling products exist today, but they are typically tied to a specific cloud provider and don't know how to optimize for your application's specific goal. Using Spice.ai, you can build a control system for your SaaS app that learns to make auto-scaling decisions to optimize your application's unique goals.

### Food delivery order dispatching

Another example of an application that Spice.ai can power the intelligence behind the order dispatching of a food delivery network. It is an operational challenge to efficiently dispatch customer orders to drivers to minimize the waiting each customer experiences. Trained human operators can perform this task, but a trained decision-making engine, like Spice.ai, could enable this to scale.

<div style="display: flex; justify-content: center; padding: 5px; margin-bottom: 20px;">
  <div style="display: grid;">
    <img style="max-width: 563px; margin: auto" alt="Normalizing raw data" src="https://user-images.githubusercontent.com/879445/146544134-2e969e9d-aa71-4f89-80a8-e5bc4c991bd2.png">
    	<div style="font-size: 0.8rem; font-style: italic; text-align: center;">Routing customer orders to delivery drivers can leverage a decision engine. Photo: Shuttle Korea</div>
  </div>
</div>

### Optimizing energy usage of an office building

As a final example, let's imagine you are in charge of temperature control for shared office space in a smart building. Your job is to ensure that the tenants are comfortable while minimizing the energy spent running the heating/cooling systems.

You could write a simple algorithm, such as "turn on A.C. at a specified temperature at 7 a.m. and turn off at 7 p.m." What about that group in office A that frequently requests to adjust the temperature for their office? You can make a minor tweak to adjust the temperate for that particular office in your algorithm - but what about when they move out? How about the group in office B who usually works until 8 p.m. and frequently asks to turn on the A.C., etc.

Accommodating all of these variations and ensuring that the energy isn't wasted can be done for a single building. But instead of one building, imagine needing to manage 100s of buildings. Developing an application that can efficiently manage the temperature for buildings becomes more accessible with Spice.ai as the decision-making engine.

## Spice.ai works best on real-time data streams.

One of the themes you may have noticed in the previous section is the need to make decisions in real-time. Enabling decisions in real-time requires access to real-time data streams to base the decisions on. This real-time data could be generated by the application or come from another external data source - or even both.

To ensure that Spice.ai trains efficiently, it requires access to historical data (in the same format as the real-time data stream) and a record of historical decisions. The historical data allows Spice.ai to generate a baseline of its initial behavior. After the initial training, Spice.ai will continuously learn to improve its behavior after seeing how its decisions affect the goal it is optimizing for.

Access to enough historical data is often the biggest challenge to integrating Spice.ai effectively in most projects. This challenge is an area that the Spice.ai team is working on.

## Summary

Let's quickly recap; Spice.ai is your application's real-time intelligent decision engine. It works best when it has access to a real-time data stream that it can make decisions from and access to historical data and historical decisions that allow it to train an effective initial model.

Getting that historical data (if it exists) is often the most challenging aspect of integrating Spice.ai and is an area we're working on making easier. As Spice.ai runs next to your app, it can continuously learn from the new data coming in and see how your app's decisions affect your application's goal in the subsequent period.

If you’d like to partner with us on the journal of making new types of intelligent decision making applications, we invite you to discuss with us on Discord, reach out on Twitter or email us.

Phillip
