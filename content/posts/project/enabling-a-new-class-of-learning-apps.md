---
date: 2021-12-17
title: "Enabling a new class of learning apps"
type: blog
linkTitle: "Enabling a new class of learning apps"
author: Phillip LeBlanc ([@leblancphill](https://twitter.com/leblancphill))
---

Spice.ai is a decision engine that learns from data to recommend actions to achieve an application's goals. In this post, we'll explore a brief history of apps that have used decision engines successfully and explore some use-cases for this kind of application.

But first, what do we mean by "a new class of learning apps"? As Luke mentioned in "[Making apps that learn and adapt](https://blog.spiceai.org/posts/2021/11/05/making-apps-that-learn-and-adapt/)" these are apps where decision-making AI that learns and adapts is integrated as a core part of the application logic. Spice.ai aims to make building these types of learning apps as simple as building a modern web page.

## History of decision engines

The idea to make intelligent decision-making applications is not new. Developers first created these applications around the 1970s, and it is one of the earliest examples of using Artificial Intelligence to solve real-world problems. [[1]](http://aima.cs.berkeley.edu/)

These first applications to use a decision engine were called "[expert systems](https://en.wikipedia.org/wiki/Expert_system)." A distinguishing trait of expert systems is that they encode human expertise in the form of rules for automatic decision-making. These rules were created by experts in the domain and the combination of these rules powered the expert systems' decision making capabilities. Some of the uses for an expert system include:

- [Fault diagnosis](https://ieeexplore.ieee.org/document/9549566)
- ["Smart" operator and troubleshooting manual](https://www.gregstanleyandassociates.com/whitepapers/IFAC91objectPaper.pdf)
- [Recovery from extreme conditions](https://www.gregstanleyandassociates.com/whitepapers/IFAC91objectPaper.pdf)
- [Emergency shutdown](https://www.gregstanleyandassociates.com/whitepapers/IFAC91objectPaper.pdf)

The time investment required by experts and the number of rules that needed to be created to make this type of system useful meant these systems were expensive to create and infeasible for most applications. [[2]](https://www.worldcat.org/title/introduction-to-knowledge-engineering/oclc/70987401) These systems were also unable to learn from experience, relying on experts to write more rules to be able to learn. With the advent of modern deep-learning techniques and access to lots of data it is now possible to, in effect, have the computer figure out the rules needed to power a decision engine and improve them over time.

Our vision for Spice.ai is to make it possible to build a new class of applications that are powered by a decision engine that learns and adapts. What would these use-cases look like?

## Use cases of decision-making applications

### Reduce energy costs by optimizing air conditioning

**Today**: A office building air conditioning system runs on a fixed schedule, and is set to a fixed temperature in business hours only adjusting using in-room sensor data, if at all. This potentially overcools at business close as the outside temperature lowers, and the building starts vacating.

**With Spice.ai**: Using Spice.ai the application combines time-series data from multiple data sources, including the time of day and day of week, building/room occupancy, and outside temperature, energy consumption and pricing. The A/C controller application learns how to adjust the air conditioning system as the room naturally cools towards the end of the day, and as the occupancy decreases, being rewarded for both maintaining the desired temperature and minimizing energy consumption/cost.

### Routing web3 token swaps across pools

**Today:** Token swaps on a platform like [Uniswap](https://uniswap.org/) utilize a static algorithm based on the current state of the blockchain to determine the best route for a token swap to occur. These systems either don't aggregate across all of the pools of liquidity that exist, or don't account for the expected slippage that occurs across each pool along the swap route.

**With Spice.ai:** The Spice.ai decision engine is rewarded for routing token swaps across pools with the least amount of slippage. The routing software learns over time a model based upon these rewards and patterns in the data such as pending transactions, time of day, day of week, size of the transaction, recent history of transactions, etc. The token swap application continuously feeds new swap transactions into Spice.ai, which along with Spice.ai's own real-time feed of blockchain data improves the recommendations back to the application.

### Food delivery order dispatching

**Today:** Customers order food delivery with a mobile app. When the order is ready to be picked up from the restaurant the order is dispatched to a delivery driver by a simple heuristic that chooses the nearest available driver. As the app gets more popular with customers, and the number of restaurants, drivers and customers all increase the heuristic needs to be constantly tuned or supplemented with human operators to handle the demand.

**With Spice.ai**: The Spice.ai engine handles the timing of when to dispatch a driver and which driver to choose. The engine rewarded for minimizing the end-to-end time and maximizing customer star ratings. The application learns the optimal time to send a driver to pick up the food, based on the restaurant's history of how long an order takes to prepare, and chooses the optimal driver to pick the order up and deliver it to the customer in the fastest time. As the app increases in complexity, with the number of users, drivers and customers increasing over time the app is able to adapt to keep up with the demands of the business.

## Summary

Spice.ai is a decision engine that learns from data to recommend actions to achieve an application's goals. These applications are part of a new class of applications that are enabled by integrating with a decision engine that can learn and adapt.

If you'd like to partner with us on the journey of making new types of intelligent decision making applications, we invite you to discuss with us on Discord, reach out on Tiwtter or email us.

Phillip
