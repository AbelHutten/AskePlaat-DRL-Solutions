## Answers to the questions of chapter 6

1. 
    > What are the differences between AlphaGo, AlphaGo Zero, and AlphaZero?
    
    * **AlphaGo** (2016): A computer program that defeated a human world champion in Go. It used a combination of Monte Carlo tree search and a database of expert games to make decisions.
    * **AlphaGo Zero** (2017): An improved version of AlphaGo that learned from self-play, without any human data or expertise. It trained itself by playing against previous versions of itself        
    and achieved superhuman performance in Go.
    * **AlphaZero** (2018): A generalized algorithm based on AlphaGo Zero's approach, which was applied to the games of chess and shogi. Unlike AlphaGo Zero, it didn't use any domain-specific
    knowledge or data.

    Key differences:

    * AlphaGo relied on human expertise, while AlphaGo Zero and AlphaZero were self-supervised.
    * AlphaGo focused on Go specifically, whereas AlphaZero is a more general algorithm that can be applied to other games.

2. 
    > What is MCTS?

    MCTS stands for **Monte Carlo Tree Search**, an algorithm used in decision-making problems that combines random sampling (Monte Carlo) with tree search to efficiently explore solution spaces. It's often used in games like Go, Chess, and Poker.

3. 
    > What are the four steps of MCTS?

    The four main steps of Monte Carlo Tree Search (MCTS) are:

    1. **Selection**: Choose a promising node from the tree to expand.
    2. **Expansion**: Add new child nodes by applying possible actions to the selected node.
    3. **Playout / Sampling / Rollout / Simulation**: Randomly simulate many playouts of the game or process from each child node.
    4. **Backpropagation / Backup**: Backtrack up the tree, propagating the results of the simulations to their parent nodes.

4. 
    > What does UCT do?

    UCT (Upper Confidence bound for Trees) is a selection rule that governs the exploration/exploitation trade-off in MCTS.

5. 
    > Give the UCT formula. How is P-UCT different?

    $$\mathrm{UCT}(a) = \frac{w_a}{n_a} + C_p\sqrt{\frac{\mathrm{ln} \ n}{n_a}}$$
    where $w_a$ is the number of winds in child $a$, $n_a$ is the number of times childe $a$ has been visited, $n$ is the number of times the parent node has been visited, and $C_p$ is a constant that governs the amount of exploration. This is formula 6.1 from page 172.

    The formula for P-UCT it slightly different (page 173):
    $$\textrm{P-UCT}(a) = \frac{w_a}{n_a} + C_p\pi(a|s)\frac{\sqrt{n}}{1 + n_a}$$
    In this formula, the probability assigned to $a$ by the policy is taken into account, and actions that are likely under the policy are explored more.
    
6. 
    > Describe the function of each of the four operations of MCTS.

    The functions of the four MCTS operations are described on page 170:
    > 1. **Select** In the selection step the tree is traversed from the root node down until a leaf of the MCTS search tree is reached where a new child is selected that is not part of the tree yet. At each internal state the selection rule is followed to 
    > 2. **Expand** Then, in the expansion step, a child is added to the tree. In most cases
    only one child is added. In some MCTS versions all successors of a leaf are added
    to the tree.
    > 3. **Playout** Subsequently, during the playout step random moves are played in a
    form of self-play until the end of the game is reached. (These nodes are not added
    to the MCTS tree, but their search result is, in the backpropagation step.) The
    reward 𝑟 of this simulated game is +1 in case of a win for the first player, 0 in
    case of a draw, and −1 in case of a win for the opponent.9
    >4. **Backpropagation** In the backpropagation step, reward 𝑟 is propagated back upwards in the tree, through the nodes that were traversed down previously. Two
    counts are updated: the visit count, for all nodes, and the win count, depending
    on the reward value. Note that in a two-agent game, nodes in the MCTS tree
    alternate color. If white has won, then only white-to-play nodes are incremented;
    if black has won, then only the black-to-play nodes.
    MCTS is on-policy: the values that are backed up are those of the nodes that
    were selected.  

<br>

7. 
    > How does UCT achieve trading off exploration and exploitation? Which inputs does it use?

    The UCT formula contains two terms. The first is the win rate, which means that actions which have shown a high win rate so far are more likely to be selected (exploitation). The second term will be high for nodes that have not been selected often, pushing the algorithm to explore these actions more. 

8. 
    > When $C_p$ is small, does MCTS explore more or exploit more?

    When $C_p$ is small, MCTS exploits more and explores less.

9. 
    > For small numbers of node expansions, would you prefer more exploration or more exploitation?

    For a small number of node expansions, the estimates of the win rates will be very high variance, and it therefore makes sense not to put to much weight on them and instead focus more on exploration.

10. 
    > What is a double-headed network? How is it different from regular actor critic?

    In regular actor critic, there are typically two separate neural networks: one for the policy and one for the value. With double headed actor critic, on the other hand, both the policy and value net are integrated into a single network, with a top that is split into two parts, two "heads". Having the policy and value function integrated together in a single network can potentially improve training speed by allowing a kind of weight sharing between the two networks. Since the lower layers can be interpreted as learning features, and the same features may be useful to the policy and the value estimation, learning can be improved.

11. 
    > Which three elements make up the self-play loop? (You may draw a picture.)

    Search, training, evaluation. The illustration can be found on page 164 (figure 6.10).

12. 
    > What is tabula rasa learning?

    Tabula rasa learning stands for a version of learning in which the agent is given no prior knowledge of the problem, but instead learns completely from scratch from its own experience.

13. 
    > How can tabula rasa learning be faster than reinforcement learning on top of supervised learning of grandmaster games?

    From the text (page 179):

    > Why is
    self-play faster than a combination of supervised and reinforcement learning? The
    reason is a phenomenon called curriculum learning: self-play is faster because it
    creates a sequence of learning tasks that are ordered from easy to hard. Training
    such an ordered sequence of small tasks is quicker than one large unordered task.
    Curriculum learning starts the training process with easy concepts before the
    hard concepts are learned; this is, of course, the way in which humans learn. Before
    we learn to run, we learn to walk; before we learn about multiplication, we learn
    about addition. In curriculum learning the examples are ordered in batches from
    easy to hard. Learning such an ordered sequence of batches goes better since understanding the easy concepts helps understanding of the harder concepts; learning
    everything all at once typically takes longer and may result in lower accuracy.

14. 
    > What is curriculum learning?

    Curriculum learning organizes the training examples in a meaningful order. It could for example start with simple examples or concepts, and move on to progressively harder problems and concepts. This attention to the order of the training examples can help facilitate learning complex tasks.
