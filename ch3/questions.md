1. From the Gym github page [https://github.com/openai/gym]: "Gym is an open source Python library for developing and comparing reinforcement learning algorithms by providing a standard API to communicate between learning algorithms and environments, as well as a standard set of environments compliant with that API. Since its release, Gym's API has become the field standard for doing this." 
<br> <br>
Note that Gym is no longer maintained, and it that it is a good idea to switch to Gymnasium [https://github.com/Farama-Foundation/Gymnasium] which is a fork of gym that is still actively maintained.

2. From the Stable Baselines docs [https://stable-baselines.readthedocs.io/en/master/]: "Stable Baselines is a set of improved implementations of Reinforcement Learning (RL) algorithms based on OpenAI Baselines."

3. Since the Q function is changing during training, the training target is non-stationary. This makes the deep learning problem significantly harder, and can lead to instability and convergence issues.

4. To guarantee that a learning algorithm converges to the optimal solution, sufficient exploration is required. If the agent does not explore enough, it may happen that it misses parts of the state space that are very advantageous. An example could be a person that refuses to try new foods. Although there may be foods out there that this person would like more than the foods he is choosing, he can never find this out because of lack of exploration. There is also a benefit to choosing actions that are believed to lead to high reward. This is because this leads to learning in regions of the state space that are likely to be more important, because they are visited by the optimal policy. For example, imagine an agent trying to learn basketball in a simulator. If the agent believes that breaking its own leg at the start of the game is bad, it may still do so as a form of exploration. The experience it gathers during a game where it has a broken leg probably does not teach it much about playing good basketball, however, since with basketball important parts of the state space include things like running and jumping, which the agent can not explore in the runs in which it has a broken leg. This can slow down learning. By focussing on actions the agent believes are good, learning can accelerate. The agent needs to balance these two factors; without enough exploration, the learned policy could be bad. With too much exploration, learning could be slow.

5. $\epsilon$-greedy.

6. Bootstrapping is a method by which you generate a new estimate (for example of the Q function) using your old estimate. TD and n-step TD are examples of bootstrapping methods.

7. The input is 4 consecutive frames of 84 $\times$ 84 grey scale pixel values. The first layer is a convolutional layer of 16 8 $\times$ 8 filters with stride 4 and ReLU nonlinearities. The next layer is again convolutional with 32 4 $\times$ 4 filters with stride on and ReLU nonlinearities. Then follows a fully connected layer consisting of 256 ReLU units. This is fully connected to the output layer, which is of size 18 corresponding to the 18 possible actions in Atari.

8. There are multiple reasons. In deep supervised learning, the training samples are i.i.d., while in deep RL they are not, since the training samples received depends on the actions taken by the agent. A second reason is that, when a bootstrapping method is used and no steps are taken to avoid it, the target depends on the old estimate, leading to a moving target as described in the answer to question 3.

9. The deadly triad consists of bootstrapping, function approximation and off-policy learning. It was believed that algorithms that include these components would have issues with convergence, however, more recent successes have shown that there are context in which it can indeed be made to work.

10. Function approximation complicates RL because it introduces approximation errors, and can cause feedback loops.

11. Experience replay can decorrelate the training states, making them more independent. This stabilizes learning. Experience replay can also improve coverage.

12. Correlation between states can cause the "specialization trap", and reduce coverage of the state space. If there are regions of the state space that aren't sufficiently covered, it could be that the global optimum is not found and the algorithm converges to a local optimum.

13. See the answer to question 4. Insufficient state space coverage implies insufficient exploration.

14. When deep RL algorithms don't converge, they typically do not lead to good solutions to the MDP.

15. $10^{47}$

16. $10^{170}$

17. $10^{1685}$

18. Rainbow is the name of the algorithm presented in the Rainbow paper. The algorithm is a combination of different improvements to DQN, analogous to how a rainbow is a combination of different colors. The main message is that these different individual improvements can be combined to give something that's better than any of the improvements alone; they "stack" in a way.

19. The improvements combined in Rainbow are:
    * DDQN
    * Prioritized experience replay
    * Duelling network architecture
    * Multi-step bootstrap targets (as in A3C)
    * Distributional Q-learning
    * Noisy DQN