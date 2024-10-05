## Answers to the questions of chapter 2

1. 
    >In reinforcement learning the agent can choose which training examples are generated. Why is this beneficial? What is a potential problem?
    
    A potential benefit is that the agent can choose to focus its learning on more relevant parts of the state space, i.e, parts that are relevant for the task or parts that the value function or model has a large error on. A potential drawback is that the samples are no longer i.i.d., which makes learning less stable and more difficult. It can also lead to suboptimal solutions, if the agent doesn't explore sufficiently.

2. 
    > What is Grid world?
    
    Grid world is a simple environment, where the states are points (or squares) on a 2D orthogonal grid. The states correspond to the different squares that the agent can be in. The actions are moving north, east, south or west (although in some squares, not all of these actions may be available, for example when the agent is next to a wall). Some squares give reward (positive or negative) when the agent visits them. Grid world is interesting because it is a simple discrete environment, which makes well suited for investigating RL algorithms and developing an intuition for the way they work.

3. 
    > Which five elements does an MDP have to model reinforcement learning problems?
    
    The five elements of an MDP are $(S, A, T, R, \gamma)$.
    * $S$ is the set of states in the MDP. These states have the Markov property: if you know the state at time $t$, knowing the states before time t does not give you extra information about the state in the future; the future is independent of the past conditioned on the present. MDPs can have finite, countably infinite or uncountably infinite state spaces.
    * $A$ is the set of actions. The actions that are available to the agent may depend on the state that the agent is in, in which case it is sometimes written as $A(s)$ or $A_s$. 
    * $T$ is the transition function. It gives the probability of ending up in state $s'$ at time t given that at time t-1 the agent was in state $s$ and took action $a$, i.e, $$T(s', s, a) = Pr(s_t = s' | s_{t-1} = s, a_{t-1} = a)$$
    * $R$ is the reward function. I specifies the distribution over rewards that the agent samples from, i.e., the probability of receiving reward $r$ at time $t$ given that the agent transitioned to state $s'$ by taking action $a$ in state $s$; $$R(r, s', s, a) = Pr(r_t = r | s_t = s', s_{t-1} = s, a_{t-1} = a)$$ Typically, the reward is considered part of the environment. In some cases, however, some authors consider it part of the agent.   
    * $\gamma$ is the discount factor. It appears in the agent's objective function, the return (also denoted $R$) $R_t = \sum_{i=0}^\infty \gamma^t r_{t+1}$. The discount factor encodes the fact that the agent cares more about rewards in the near future than it does about rewards in the far future. Often this is done for mathematical convenience, to avoid divergent returns, but there are also other justifications for it. For example, the agent may be more certain of the near future, so it may be appropriate to prefer a more certain reward in the near future over a less certain reward in the far future. A discount factor is also logically equivalent to having an alternative MDP without a discount factor (i.e. $\gamma$ = 1) where there is a special "death" state, with a probability of 1 - $\gamma$ of transitioning to this death state, and staying there indefinitely and receiving 0 reward ever after. In episodic MDPs, the discount factor is typically set to 1. A discount factor can also be thought of as inducing an "effective horizon" of $1/(1-\gamma)$.

4. 
    > In a tree diagram, is successor selection of behavior up or down?
    
    The successor selection is down, towards the leaves.

5. 
    > In a tree diagram, is learning values through backpropagation up or down?
    
    Learning value functions happens from states that are closer to the leaves, and the values are backed up in the direction of the root, so it is up. In the case of temporal difference learning, the information is propagated up by one level, while in monte carlo learning it is backed up from the leave node to all nodes on the trajectory between the leave and the root.

6. 
    > What is $\tau$? 

    $\tau$ is a trace or trajectory, which denotes the history of the agent in terms of states visited, actions taken and rewards received.

7. 
    > What is $\pi(s)$?
    
    $\pi$ is the policy. $\pi(a|s)$ gives the probability that the agent takes action $a$ in state $s$. The policy fully specifies the behavior of the agent. The goal of RL is finding the policy that maximizes the expected return.

8. 
    > What is $V(s)$?
    
    $V(s)$ is the value function. It depends on a specific policy, and is therefore typically indexed by $\pi$. $V^\pi(s)$ is the expected return for following policy $\pi$ when starting in state $s$.

9. 
    > What is $Q(s,a)$?
    
    $Q(s,a)$ is the action value function (also called state-action value function). Like $V$, $Q$ depends on the policy, so is typically written $Q^\pi(s, a)$. It is defined analogously to the value function, as the expected reward for starting in state $s$, taking action $a$ and following $\pi$ afterwards.

10. 
    > What is dynamic programming?
    
    Dynamic programming (DP), in the context of RL, refers to a class of algorithms for solving discrete MDPs by systematically breaking down the problem into smaller subproblems. They typically solve the MDP by solving the Bellman equation recursively. Value iteration is an example of a DP algorithm. DP methods depend on having full knowledge of the MDP, including full knowledge of the transition dynamics and reward function. Due to their computational complexity, they are typically only feasible on smaller problems.

11. 
    > What is recursion?
    
    From Wikipedia [https://en.wikipedia.org/wiki/Recursion]: "Recursion occurs when the definition of a concept or process depends on a simpler or previous version of itself. Recursion is used in a variety of disciplines ranging from linguistics to logic. The most common application of recursion is in mathematics and computer science, where a function being defined is applied within its own definition. While this apparently defines an infinite number of instances (function values), it is often done in such a way that no infinite loop or infinite chain of references can occur. A process that exhibits recursion is recursive."

12. 
    > Do you know a dynamic programming method to determine the value of a state?
    
    Value iteration.

13. 
    > Is an action in an environment reversible for the agent?
    
    No it is irreversible.

14. 
    > Mention two typical application areas of reinforcement learning.

    Robotics, autonomous vehicles, finance, advertising.

15. 
    > Is the action space of games typically discrete or continuous?
    
    Discrete, although it may be very large (pixel space in video games for example can be very large).

16. 
    > Is the action space of robots typically discrete or continuous?
    
    Continuous. It deals with angles, forces, torques, etc., which are all continuous.

17. 
    > Is the environment of games typically deterministic or stochastic?
    
    Both occur often. Games like chess and go are deterministic, while backgammon for example is stochastic. Many video games contain random elements, but some, like some of the Atari games for example, are deterministic.

18. 
    > Is the environment of robots typically deterministic or stochastic?
    
    The environment of robots is typically stochastic. Robots operate in the real world, which has so many degrees of freedom that the only feasible way to model them is as stochastic.

19. 
    > What is the goal of reinforcement learning?
    
    The goal of RL is to find a policy that maximizes the expected discounted future sum of rewards (a.k.a. the return) for a given (PO)MDP.

20. 
    > Which of the five MDP elements is not used in episodic problems?
    
    The discount factor is typically not used. Since the episodes are finite, there is no risk of divergent returns.

21. 
    > Which model or function is meant when we say “model-free” or “model-based”?
    
    The transition model is typically meant. Sometimes, the reward model can also be meant.

22. 
    > What type of action space and what type of environment are suited for value-based methods?
    
    Value based methods are most suitable in discrete action spaces. They lead to deterministic policies, which can be suboptimal in partially observed environments. They are not well suited for partially observable, continuous, or non-Markovian environments. 

23. 
    > Why are value-based methods used for games and not for robotics?
    
    Because in robotics the state space is continuous.

24. 
    > Name two basic Gym environments.

    CartPole, MountainCar, Pendulum, LunarLander, BipedalWalker, Taxi, HalfCheetah, Hopper, Humanoid, HumanoidStandup, InvertedPendulum, Swimmer and the Atari games are some popular ones.
