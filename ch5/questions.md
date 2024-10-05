## Answers to the questions of chapter 5

1. 
    > What is the advantage of model-based over model-free methods?

    Model-based methods can potentially achieve better sample complexity. They may also use the model for more effective exploration.

2. 
    > Why may the sample complexity of model-based methods suffer in high-dimensional problems?

    In high-dimensional problems a naive model-based strategy may struggle to find an accurate model. When learning the model has poor sample complexity, the sample complexity of the model based method will have poor sample complexity as well.

3. 
    > Which functions are part of the dynamics model?

    The transition function and the reward function.

4. 
    > Mention four deep model-based approaches.

    Dyna, PlaNet, DreamerV3, MuZero.

5. 
    >  Do model-based methods achieve better sample complexity than model-free?

    Yes, by using their experience to learn a model, model based methods make more efficient use of the information contained in their experience, leading to better sample complexity (but not per se better in terms of wall clock time, since the algorithm may require more compute).

6. 
    > Do model-based methods achieve better performance than model-free?

    Model-based methods don't necessarily achieve better performance than model free methods; when the model they learn is not accurate, that inaccuracy can cause the method to learn a poor policy. 

7. 
    > In Dyna-Q the policy is updated by two mechanisms: learning by sampling the environment and what other mechanism?

    Learning by sampling rollouts of the dynamics model.

8. 
    > Why is the variance of ensemble methods lower than of the individual machine learning approaches that are used in the ensemble?

    The process of averaging over the different models reduces it's variance, as long as these errors are not correlated too strongly.

9. 
    > What does model-predictive control do and why is this approach suited for models with lower accuracy?

    Quoting page 137:
    > Model-predictive control is a well-known approach in process
    engineering, to control complex processes with frequent re-planning over a limited
    time horizon. Model-predictive control uses the fact that many real-world processes
    are approximately linear over a small operating range (even though they can be
    highly non-linear over a longer range). In MPC the model is optimized for a limited
    time into the future, and then it is re-learned after each environment step. In this
    way small errors do not get a chance to accumulate and influence the outcome
    greatly. Related to MPC are other local re-planning methods. All try to reduce the
    impact of the use of an inaccurate model by not planning too far into the future
    and by updating the model frequently
    
10. 
    > What is the advantage of planning with latent models over planning with actual models?

    An effective latent space reduces the dimensionality of the representation of the environment. By learning a model in this lower dimensional latent space, many of the difficulties associated with learning in high dimensional environments are mitigated and the sampling efficiency improves. In addition to the dimensionality reduction, if the compression is lossy in such a way that the salient parts of the environment are kept but the irrelevant parts lost, this can also improve learning.

11. 
    > How are latent models trained?

    There isn't a single way in which latent models get trained. See for example [Oh et. al.](https://arxiv.org/abs/1707.03497) or [Hafner et. al.](https://arxiv.org/abs/2301.04104) for different examples of how latent models get trained.

12. 
    > Mention four typical modules that constitute the latent model.

    Encoder, reward function, value function, transition function.

13. 
    > What is the advantage of end-to-end planning and learning?

    As it states on page 138, end-to-end approaches are often more general and tend to perform better than their hand-crafted counterparts.

14. 
    > Mention two end-to-end planning and learning methods.

    Two methods mentioned in the text are Value Iteration Networks (VIN) and TreeQN.