## Answers to the questions of chapter 4

1. 
    > Why are value-based methods difficult to use in continuous action spaces?  

    Value based methods construct a policy using $\pi(s) = \underset{a}{\operatorname{\argmax}} \ Q(s, a)$. While taking this $\underset{a}{\operatorname{\argmax}}$ is straightforward in discrete action spaces, in continuous action spaces this becomes a potentially computationally expensive optimization problem. Also, value based methods always lead to deterministic policies, and can cause a change in the weights of the value network to lead to discrete jumps in the selected action. These are disadvantages when the optimal policy is a stochastic one, or the environment requires subtle adjustments to the policy, respectively.

2.
    > What is MuJoCo? Can you name a few example tasks?

    MuJoCo, which stands for Multi-Joint dynamics with Contact, is a popular physics engine designed for robotics and RL tasks. Example tasks include HalfCheetah, Humanoid, Walker2d and Swimmer

3. 
    > What is an advantage of policy-based methods?

    On continuous action spaces, policy based methods do not suffer from the problems listed in the answer to question 2. They directly optimize the policy instead of taking an $\operatorname{\argmax}$ over the value function. The can also learn smooth and continuous functions, which is an advantage in continuous action spaces since it allows subtle adjustments. They can also learn stochastic policies, which is required in certain environments to achieve a good reward (with poker, for example).

4.
    > What is a disadvantage of full-trajectory policy-based methods.

    Quoting the summary of this chapter:
    > After the full trajectory has been rolled out, the reward and the value of the trajectory is calculated and the policy parameters are updated, using gradient ascent. Since the value is only known at the end of an episode, classic policy-based methods have a higher variance than value based methods, and may converge to a local optimum.

5.
    > What is the difference between actor critic and vanilla policy-based methods?

    Actor critic methods include both a policy network and a value network. The value network can help reduce the variance of the algorithm.

6. 
    > How many parameter sets are used by actor critic? How can they be represented in a neural network?

    In actor-critic methods, there are typically at least 2 parameter sets, the actors parameters $\theta$, which govern the policy network $\pi(a | s; \theta)$, and the critic parameters $\phi$, which govern the value function $V(s; \phi)$ or $Q(s, a;\phi)$.  

    The actor and critic can be represented by separate network, or by a single network with multiple heads.

    In some actor-critic methods, there are more parameters. An example is A3C, where, in addition to the value network and the policy network, there is an explicit advantage network as well.

7.
    > Describe the relation between Monte Carlo REINFORCE, 𝑛-step methods, and temporal difference bootstrapping.

    The relationship is the same as in other contexts. With Monte Carlo, you sample until termination, and only run an update at that point. With temporal difference learning, you update after each step, based on the difference between the value function value at the old state (or state-action pair), and the reward obtained plus the value function value at the new state (-action pair). N-step methods lay in between, where they roll out n-steps, and then perform the update using the reward obtained and the value of the value function at this n'th state.

    Monte Carlo sampling is unbiased, but high variance. Temporal difference learning is biased but lower variance. N-step methods lie in between.

8. 
    > What is the advantage function?

    The advantage function $A(s, a)$ is defined by the formula $A(s,a) = Q(s, a) - V(s)$. It represents the relative value of an action in a state compared to the average value of that state, where the average is taken over the policy. Using advantages in Actor-Critic methods helps reduce variance, since we are essentially choosing $V(s)$ as a baseline. A2C and PPO are examples of algorithms that make use of the advantage function.

9. 
    > Describe a MuJoCo task that methods such as PPO can learn to perform well.

    Humanoid is an example of such a task. PPO works relatively well on high dimensional tasks with continuous in- and output spaces, such as Humanoid.

10. 
    > Give two actor critic approaches to further improve upon bootstrapping and advantage functions, that are used in high-performing algorithms such as PPO and SAC.

    Entropy regularization and clipping the surrogate objective.

11. 
    > Why is learning robot actions from image input hard?

    Visuo-motor interaction is difficult.




