---
date: 2021-12-09
title: "Q-learning: a reward is all you need"
type: blog
linkTitle: "Q-learning: a reward is all you need"
author: Corentin Risselin
---

There are 2 general ways to train a AI to match a given expectation: we can either give it the expected outputs (commonly named labels) for differents inputs, this is called supervised learning. Or we can give a reward for each outputs, like a score, this is called reinforcement learning (RL).

Supervised learning works by tweaking all the parameters (weights in neural networks) to fit the desired outputs. Usually hoping that given enough input/label pairs the AI will average to common rules that generalize for any input.

Reinforcement learning's reward is often given from a simple formula that can score any output: we don't know what specific output we want but we can recognize how good is the result. In this latter statement their are 2 underlying concept we will address in this post:

* Can we just tell if an output is good or not in a binary way or do we have to quantify the output to train our AI?
* Do we have to give a reward for every AI's output? Can we give a reward only at specific time?

Obviously those questions are already answered and many algorithms deals with those 2 topics. Our journey here will be to understand how we tackle those questions and end up with a beautiful formula that is a the core modern approaches of RL:

[Bellman Equation](https://wikimedia.org/api/rest_v1/media/math/render/svg/678cb558a9d59c33ef4810c9618baf34a9577686)
<div style="display: flex; justify-content: center; padding: 5px;">
  <div style="display: flex; flex-direction: column;">
    <img style="max-width: 600px; margin: auto" src="https://user-images.githubusercontent.com/" />
	<div style="font-size: 0.8rem; font-style: italic;">Figure 1. Time Series processing visualization: a time window is usually chosen to process part of the data stream</div>
  </div>
</div>

## Q-learning

The vast majority, if not all, modern RL algorithms are based on the principles of Q-learning: the idea is to evaluate a 'reward expectation' for each possible actions. If we can have a good evalutation we could simply try to maximize the reward by taking the action that have the maximum evalutation. The function giving this expected reward is named Q. For now we will assume we can have a reward for any action.

[[Q(state, action) => expected reward]]

The `t` indices shows that the state and action aren't constant and will vary, usually with time/action taken. The `Q` function and the reward funciton `r` on the other hand are unique functions that would perfectly returns the 'expected reward' for any given state/action pairs.

For now we will assume we can have a reward that give an objective and perfect evaluation of each state/action.

[[Q values per actions trying to get to a point in an empty 2d map]]

### Q-Table

We know that actions' outcomes (rewards) will vary depending of the current state we are, otherwise the problem would be trivial to solve. If the states that a relevant to our actions can be numbered, a simple way would be to build a table with all the possible states/action pairs. There are different ways to build such a table depending on how we can interact with our environment, eventually we would have a good 'map' to guide us to do the best actions.

[[Q-Table]]


### Deep Q-Learning

When the number of variables of the environment relevant to our actions/rewards become to large the amount of possible states grow quickly. It doesn't take a lot of possible parameters to make the Q-table approach unfeasible. Neural networks are known to work very nicely and efficiently in high dimmensionnality (with a lot of input variables). They also generalize well, so the idea in Deep Q-Learning is to use a neural network to predict the different Q values for each action given a state.

[[NN as Q evaluator]]

In this case we do not need to given the state/action pairs but only the state as the neural network would exhaustively returns all the Q values associated to each action. This is due to the general cases of having complex environments but a smaller number of possible actions.

This method works very well, it is similar to a supervised learning with states as inputs and rewards as labels. We assumed so far we had a reward for each action and we simply take the best reward for the next action (called a greedy policy). In many cases this is not enough: even if an action would yield the best reward at a given state, this may affect the next state so that we wouldn't optimize the reward in the long term. Also if we can have a reward for each action, we usually give 0 as a reward, we will not be able to choose the right action if they would affect latter states despite not yeilding different reward at the current state.

The sparsity of reward and/or the long-term calculation of total reward (non greedy policies) leads us to diverge from supervised learning and learn potiential future rewards.

## Temporal difference: TD-Learning

TD-learning is a clever way to account for potential future value without knowing them yet. TD is a model-free class of algorithm: we will not try to simulate/evaluate the future states/environment. The main idea would be to be able to take into acount all the rewards of a sequence of actions to give a better value than just the reward of the next action.

We can, for instance, just sum all the future rewards:

[[cumulating actions' reward: equation + illustration]]

This is named TD(0) the simplest form of TD methods: simply accumulating all the rewards.

### Introducing policies

We could try different trajectories (sequence of actions) and retrospectively get the final reward for each actions but this has 2 drawbacks: the environment is usually too vast and the sequence of actions might not even have a definite end. Also such exhaustive methods might not be very efficient. Instead we can evaluate the `value` of the next state overall, like the maximum of all its possible rewards (direct reward), and add this value to the reward of a given action.

If a state can have diferrent branches we would select the best one, this is be called our policy: the way we choose actions. This simple form of taking the maximum is known as greedy policy.

[[value function from expected value with policy]]

This can be written down as:

[[policy explanation]]

The expected value notation is defiened as:

[[expected value]]

For a greedy policy the probabilites `p` would all be set to 0 but the one associated with the highest return to 1 (in case of an equality between n actions we would attribute '1/n' as probabilities to get the same expected value).

[[expected value for greedy policy]]

### Relation with Q function

The expected reward can be replace by the Q function we used earlier, which now can be denominated to be specific to our chosen policy:

[[value/Q relation]]

### TD-0

We previously talked about the problem of not being able to exhaustively go through all the states and that the evalution of the Q value from a neural network could help. Now we want to be able touse the TD-method to have a better value estimattion that will take into account potential future rewards.

The TD-0 method is elegant as we can, in fact, just use the next state's expected value intead of all future ones. The idea is that with succesive evaluations we build a chain of dependencies as each states' value depend on the next one.

[[td-0 with value]]

[[td-0 propagation]]

We can see that now even with a null reward in the trajectory the greedy policy would work. We can explicit our greedy policy, going back to use Q value instead of the state value V:

[[td-0 with Q]]

### TD-lambda

We need to fix a problem: if a trajectory would grow too long or never ends a state value can potentially grow indefinitely. To counter that we can add a **discount factor** (originally named lambda, usually refer as gamma in Q-learning) for the next state's value:

[[td-lambda equation]]

Notice that we simplify the reward notation for clarity.

This discount has to be between 0 and 1 (strictly bellow 1) to avoid exploding values. We can think about it as giving more importance to the direct reward than latter ones. As the contribution to latter reward decrease the chain of action can grow without the calculated value growing: if the reward has an upper limit the value will also be bounded.

This can solve also the sparsity of rewards: giving only a positive rewards after many non rewarding steps will make the intermediate states' value nicely decaying. It looks like any rewards, positive or negative, will diffuse its value to the neighboor states.

[[maze rewards]]


## Q-Learning algorithm

Finally as we are training a neural network to estimate the Q function we need to update its target with successive iteration. As we cannot 100% trust the estimator (neural network here) to give the correct value we introduce a **learning rate** to update the target smoothly.

[[final formula]]

That is it! We now understand all the part of this formula. Over multiple training steps with different sates/actions the training should find a good averages Q function. While training the estimator uses its own output to train itself (commonly refered as bootstrapping): it is like it is chasing itself. This can lead to instability in the training process. There are many additional methods to help against such instability.

From giving rewards, sparse or not, binary or fine grained we have a smooth space of values for all our states/actions so the AI can follow a greedy policy to the best outcome.

This way of training is not a silver bullet though and there is no guaranty that the AI will find a mathematical operation from the information given as state to the returned reward.

## Conclusion

We can see our rewards function are used to train AI's policy using Q-learning. Understanding the many iterations required and the bootstrapping issues we can help our AI by carefully given relevant state information and reward:

* There needs to be a correlation between the state information and the reward: the more the relation is simple the easier/faster the AI will find it.
* Sparse and binary reward makes the training problem way more long and difficult. Giving more information through the reward can tremendously increase the speed/accuracy of the learnt Q-estimator.
* The longer the chain of actions the longer and more complex the Q-value will be to estimate.

We didn't see how the AI's algorithm can explore different actions given an environment but SpiceAI's technology focus exclusively on off-policy training where we only have past data and cannot interact with the environment. RL is a vast topic and currently quickly growing. Robotics is an amazing application but many other areas are yet to be explored with such a technology. We hope to push foward the technoly and its field of application with our platform.

If you'd like to partner with us on the mission of making new applications by leveraging RL, we invite you to discuss with us on [Discord](https://discord.gg/kZnTfneP5u), reach out on [Twitter](https://twitter.com/SpiceAIHQ) or [email us](mailto:hey@spiceai.io).

I hope you enjoy this post and learn new things.

Corentin
