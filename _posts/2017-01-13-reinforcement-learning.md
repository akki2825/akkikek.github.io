---
title: "Notes: Reinforcement Learning"
categories: [machine-learning]
---
Reinforcement learning is the problem faced by an agent that must learn behaviour through trial-and-error interactions with a dynamic environment. It is appropriately thought of as a class of problems, rather than as a set of techniques. 

There are two main strategies for solving Reinforcement Learning problems. The first is to search in the space for behaviours in order to find one that performs well in the environment. This approach has been taken by work in genetic algorithms and genetic programming. The second is to use statistical techniques and dynamic programming methods to estimate the utility of taking actions in state of the world.

In the standard RL model, on each step of interaction the agent receives as input i, some indication of the current state, S, of the environment. The agent chooses an action, a, to generate an output. The action changes the state of the environment and the value of this state transition is communicated to the agent through a scalar reinforcement signal, r. It should choose actions that tend to increase the long-run sum of values of the reinforcement signal. It can learn to do this overtime by systematic trial and error.

An intuitive way to understand the relation between the agent and its environment is with the following example:

*Environment* : You are in state 65. You have 4 possible actions.
*Agent*: I’ll take action 2.
*Environment*: You received a reinforcement of 7 units. You are in state 15. You have 2 possible actions.

The agent’s job is to find a policy Π, mapping states to actions, that maximizes some long run measure of reinforcement. We assume the environment is stationary.

Important ideas in Reinforcement Learning that came up –

- Exploration – you have to try unknown actions to get information.
- Exploitation – eventually you have to use what you know.
- Regret – even if you learn intelligently you make mistakes.
- Sampling – because of chance you have to try things repeatedly.
- Difficulty – learning can be much harder than solving a known MDPs.


**Markov Decision Process**


- A set of states s∈S
- A set of actions a∈A
- A transition function T(s,a,s’). Also called the model or the dynamics. P(s’|s,a) = T(s,a,s’)
- The reward function R(s,a,s’)
- Start state
- Maybe a terminal state
- MDP’s are non-deterministic search problems


“Markov” generally means that given the present state, the future and the past are independent. This is just like search, where the successor function could only depend on the current state (not the history). In the deterministic single-agent search problems, we wanted an optimal plan or sequence of actions, from start to goal.

For MDPs we want an optimal policy Π* : S ⇒ A

A policy Π gives an action for each state. An optimal policy is one that maxmizes expected utility if followed. An explicit policy defines a reflex agent.

**Discounting**

Its reasonable to maximize the sum of rewards and/or to prefer rewards now to rewards later

One solution: values of rewards decay exponentially.

How to discount?
Each time we descend a level. we multiply in the discount once.

Why discount?
Sooner rewards probably do have higher utility than later rewards. Also helps algorithm converge.

Example: discount of 0.5
U([1,2,3]) = 1*1 +2*0.5 + 3*o.25

What if the game lasts forever?
Solution:

- Finite horizon: (similar to depth-limited search)
- Gives non stationary policies (Π depends on time left)
- Discounting: use 0<ϒ<1. Smaller ϒ means smaller “horizon”.

Absorbing state- guarantee that for every policy, a terminal state will eventually be reached.

How to solve MDPs?

The value (utility) of a state S:

V*(s) = expected utility starting in S and acting optimally.
(tells us how good each state is)

Q*(s,a) = expected utility starting out having taken action ‘a’ from state ‘s’ and (thereafter) acting optimally.
(‘s’ is fixed and we vary ‘a’)

The optimal policy:
Π*(s) = optimal action from state s = argmax Q*(s,a)
(its the action that achieves the maximum)

**Values of States**

Fundamental operation : compute the (expectimax) value of the state.

- Expected utility under optimal action.
- Average sum of (discounted) rewards
- This is just what expectimax computed!

Recursive definition of value:

V*(s) = max Q*(s,a)

Q*(s,a) = max Σ T(s,a,s’)[R(s,a,s’) + V*(s)]   — Bellman’s equation


**Quantities**

Policy = map of states to actions.
Utility = sum of discounted rewards.
Values = expected future utility from a state (max node)
Q-values = expected future utility from a q-state (chance node)

Both value iteration and policy iteration compute the same thing (all optimal values)

In Value iteration –

- Every iteration updates both the values and (implicitly) the policy.
- We dont track the policy, but taking the max over actions implicitly recompute it.

In policy iteration –

- We do several passes that update utilities with fixed policy (each pass is fast because we consider only one action and not all of them)
- After the policy is evaluated, a new policy is chosen (slow like a value iteration pass)
- The new policy will be better (or we’re done)


**Unknown MDP : Model Based Learning**

- Learn an approximate model based on experiences.
- Solve for values as if the learned model were correct.
- E[A] = ΣP(a).a

Unknown MDP : Model Free Learning

Passive Reinforcement Learning :

- Simplified task: policy evaluation
    1. Input : fixed policy Π(s)
    2. You don’t know the transitions T(s,a,s’)
    3. You don’t know the rewards R(s,a,s’)
    
- Direct Evaluation:
    Goal : Compute values for each state under Π
    Idea : Average together observed sample values.
    Act according to Π.
    Everytime you visit a state, write down what the sum of discounted rewards turned out to be.
    Average those samples.

What’s good about direct evaluation?

- Its easy to understand. 
- It does’nt require any knowledge of T,R.
- It eventually computes the correct average values, using just sample transitions.


What’s bad about it?

It wastes information about state connnection.
Each state must be learned seperately. So, it takes log time to learn.

- Sample based Policy Evaluation:
    Take samples of outcome s'(by doing action!) and average.
    We want to improve our estimate of V by computing these averages.

- Temporal Difference Learning:
    Big Idea: Learn from every experience!
    Update V(s) each time we experience a transition (s,a,s’,r)
    Likely outcomes s’ will contribute updates more often.

- Temporal difference learning of values:
    Policy still fixed, still doing evaluation!
    Move values toward value of whatever successor occurs : running avg

Sample of V(s) : sample = R(s,Π(s),s’) + ϒV(s’)

Update to V(s): V(s) ⇐ (1-α)V(s) + (α)sample
Can also be written as : V(s) ⇐ V(s) + (α)[sample – V(s)]

Problems with TD value Learning:
TD value learning is a model – free way to do policy evaluation, mimicking Bellman               Updates with running sample averages.
Idea : Learn Q-values, not values. Makes action selection model – free too!

**Active Reinforcement Learning**

- Value iteration:
    1. Start with Q(s,a) = 0, which we know is right.
    2. Given Qk, calculate the depth k+1
    3. Q- values for all Q-states:
    Qk+1 (s,a) ⇐ ∑ T(s,a,s’)[R(s,a,s’) + ϒmax Qk(s,a)]

- Q-learning:
    Learn Q(s,a) values as you go
    1. Receive a sample (s,a,s’,r)
    2. Consider your old estimate : Q(s,a)
    3. Consider your new sample estimate:
    sample = R(s,a,s’) + ϒmax Q(s’,a’)
    4. Incorporate the new estimate into a running average:
    Q(s,a): V(s) ⇐ (1-α)Q(s,a) + (α)[sample]
    Q-learning converges to optimal policy — even if you’re acting suboptimally!
    This is called off-policy learning.

    Caveats:
    1. You have to explore enough.
    2. You have to eventually mae the learning rate small enough.
    3…but not decrease it too quickly.
    4. Basically, in the limit, it doesn’t matter how you select actions!

**Exploration**

How to explore?

Several schemes for forcing exploration:

Simplest: random action (Ε – greedy)
- Every time step, flip a coin.
- With (small) probability Ε, act normally.
- With (large) probability 1-Ε, act on current policy.

Problems with random actions?

- You do eventually explore the space, but keep thrashing around once learning is done.
- One solution: lower Ε over time.
- Another solution : exploration functions
- Take a value estimate u and a, visit count n and returns an optimistic utility e.g : f(u, n) = u + k/n

**Regret**

- Even if you learn the optimal policy, you still make mistakes along the way.
  - Regret is a measure of your total mistake cost : the difference between your (expected) rewards, including youthful suboptimality, and optimal (expected) rewards.
- Mimicking regret goes beyond learning t be optimal – it requires optimally learnin g to be optimal.

Example : random exploration and exploration functions both end up optimal, but random exploration has higher regret.

**Approximate Q- learning**

Generalizing across states:

- Basic Q-learning keeps a table of q-values.
- In realistic situations, we cannot possibly learn about every single state!
- Too many states to visit them all in training.
- Too many states to hold the q-tables in memory.

Instead, we want to generalize:

Learn about some number of training states from experience. Generalize that experience to new, similar situations. This is a fundamental idea in machine learning.

Solution: describe a state using a vector of features (properties)

- Features are functions from state to real numbers (often 0/1) that capture important properties of the state .
- Can also describe a q-state (s,a) with features.


**Linear Value Functions**

- Using a feature representation, we can write a q-function (or value function ) for any state using a few weights –
    V(s) = w1f1(s) +w2f2(s)…+wnfn(s)
    Q(s,a) = w1f1(s,a) + w2f2(s,a)+…+wnfn(s,a)
- Advantage: Our experience is summed up in a few powerful numbers.
- Disadvantage: States may share features but actually be very different in value !
- Q- learning with linear Q-functions

Intuitive interpretation:

- Adjust weights of active features.

Example: if something unexpectedly bad happens, blame the features that were on : disprefer all states with that state’s features.

**Policy Search**

Problem: often the feature-based policies that work well aren’t the ones that approximate V/Q best.

Solution: Learn policies that minimize rewards, not the values that predict them.

Policy Search: start with an OK solution (eg: Q-learning) then fine-tune by hill climbing on feature weights.

Simplest policy search :

Start with an initial linear value function or Q-function. Nudge each feature weight up and down and see if your policy is better than before.

Problems:

- How do we tell the policy got better?
- Need to run many sample episodes!
- If there are a lot of features, that can be impractical.

Better methods exploit look-ahead structure, sample wisely, change multiple parameters.
