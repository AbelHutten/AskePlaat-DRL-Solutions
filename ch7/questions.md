1. 
    > Why is there so much interest in multi-agent reinforcement learning?

    The following answer, provided by llama3.1 (7B), describes it pretty well:

    > There's a growing interest in multi-agent reinforcement learning (MARL) for several reasons:
    > 1. **Complexity of real-world systems**: Many real-world applications involve multiple agents, such as autonomous vehicles, drones, or robots interacting with each other and their environment. MARL provides a framework to study and optimize the behavior of these complex systems.
    > 2. **Emergence of social behavior**: When individual agents interact with each other, they can exhibit emergent behaviors that are not explicitly programmed. For example, in a game of rock-paper-scissors, the Nash equilibrium is an emergent property of the interactions between players. MARL allows researchers to study and understand these emergent phenomena.
    > 3. **Scalability**: As the number of agents increases, traditional single-agent reinforcement learning (SARL) approaches can become computationally infeasible or even impractical. MARL provides a framework for scaling up reinforcement learning to large numbers of agents.
    > 4. **Coordination and cooperation**: In many real-world applications, agents need to coordinate their actions to achieve a common goal. MARL provides a way to study and optimize coordination strategies among agents.
    > 5. **Competitive and cooperative games**: MARL can be applied to competitive games (e.g., poker, sports) or cooperative games (e.g., rescue missions, collaborative robotics). This broad range of applications makes MARL an attractive area of research.
    > 6. **Theoretical foundations**: Studying MARL has led to new insights into the theory of reinforcement learning and game theory. Researchers are exploring the connections between MARL and concepts like Nash equilibrium, Pareto optimality, and strategic interaction.

2. 
    > What is one of the main challenges of multi-agent reinforcement learning?

    Multi-agent environments violate the Markov property and can be non-stationary. They also tend to be partially observable.

3. 
    > What is a Nash strategy?

    A Nash strategy is the joint strategy where no player can expect a higher reward by changing their strategy.

4. 
    > What is a Pareto Optimum?

    Quoting page 201:
    > A policy is Pareto-optimal when deviating from the policy will make at least one agent worse off.
    
5. 
    > In a competitive multi-agent system, what algorithm can be used to calculate a Nash strategy?

    Counterfactual Regret Minimization.

6. 
    > What makes it difficult to calculate the solution for a game of imperfect information?

    In an imperfect information setting, there are many possible states of the world that could correspond to the observations of the agent. It is difficult to take into account all these possible states when making decisions.

7. 
    > Describe the Prisoner’s dilemma.

    It's described on pages 202/203.

8. 
    > Describe the iterated Prisoner’s dilemma.

    Two players play out the prisoners dilemma over and over, allowing them to tune their strategies to the behavior of the second player. A strategy that was mentioned, which performed well in an iterated prisoners dilemma tournament, is tit for tat. In this strategy, the agents starts out cooperating in the first round, and in all subsequent rounds it chooses the same action that the other agent chose in the round before. This strategy is hard to exploit due to its retaliatory nature. It also facilitates cooperation by starting off with cooperation and by being easy to learn for the opponent.

9. 
    > Name two multi-agent card games of imperfect information.

    Poker, bridge.

10. 
    > What is the setting with a heterogeneous reward function usually called?

    Such a setting is usually called a dec-POMDP.

11. 
    > Name three kinds of strategies that can occur a multi-agent reinforcement learning.

    Competitive, cooperative, mixed.

12. 
    > Name two solution methods that are appropriate for solving mixed strategy games.

    Evolutionary algorithms and swarm computing.

13. 
    > What AI method is named after ant colonies, bee swarms, bird flocks, or fish schools? How does it work in general terms?

    Swarm computing. It includes a large number of homogeneous, simple agents that communicate in a decentralized way.  

14. 
    > Describe the main steps of an evolutionary algorithm.

    Mutation, recombination and selection.

15. 
    > Describe the general form of Hide and Seek and three strategies that emerged from the interactions of the hiders or seekers.

    There are teams of hiders and teams of seekers, in a randomly generated world. The hiders receive negative reward when they are in line of sight of the seekers, while the seekers earn positive reward in that case. Some emergent strategies was the hiders blocking themselves in, the seekers using ramps to overcome the blockades, the hiders locking or removing the ramp, and the seekers box-surfing.

