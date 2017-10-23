# deeprl-notes
my notes on the history of (deep) RL // very much still a work in progress

### [Learning from Delayed Rewards (Watkins, 1989)](http://www.cs.rhul.ac.uk/~chrisw/new_thesis.pdf)
- *Q*-learning is first introduced; the proof of convergence is only outlined.

### [_Q_-Learning (Watkins and Dayan, 1992)](http://www.gatsby.ucl.ac.uk/~dayan/papers/cjch.pdf)
- A full proof that _Q_-learning converges.
- _Q_-learning converges to the optimum action-values with probability 1 so long as all actions are repeatedly sampled in all states and the action-values are represented discretely.

### [Self-Improving Reactive Agents Based on Reinforcement Learning, Planning and Teaching (Lin, 1992)](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.75.7884&rep=rep1&type=pdf)
- To speed the convergence of the _Q_-learning algorithm, the authors investigated three methods: **experience replay**, learning action models for planning, and teaching.
- The main idea behind experience replay is that it is wasteful to obtain experience and then use it only once to update the network.  Some experiences are rare and costly to obtain, and so should be reused in an effective way.  In experience replay, the agent remembers its past experiences and repeatedly presents the experiences to its learning algorithm; the result is that the credit/blame propoagation is sped up and therefore the networks usually converge more quickly.  The authors add that in order for experience replay to be useful, the laws that govern the environment of the learning agent should not change rapidly over time (since, in this case, past experiences may become irrelevant or even harmful).

### [Issues in using Function Approximation for Reinforcement Learning (Thrun & Schwartz, 1993)](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.73.3097&rep=rep1&type=pdf)
- In order to be of use in more complex domains (that are too large to be searched exhaustively), RL techniques must be combined with generalizing function approximation methods such as NNs.  TD-Gammon represents an early success of this combination. 
- Function approximators induce some noise (generalization error) on the output predictions.  This noise can lead to a systematic overestimation effect of values, where the agent fails to learn an optimal policy in certain situations.
- Authors provide concrete examples where overestimation leads to suboptimal policies, even asymptotically.

### [Temporal Difference Learning and TD-Gammon (Tesauro, 1995)](https://courses.cs.washington.edu/courses/cse590hk/01sp/Readings/tesauro95cacm.pdf)
- A very accessible introduction to TD-Gammon.
- TD-Gammon approximated the value function using a multi-layer perceptron with one hidden layer.
- Early attempts to follow up on this work were unsuccessful.  Furthermore, it was shown that combining _Q_-learning with non-linear function approximators could cause the _Q_-network to diverge.

### [Neural Fitted Q Iteration - First Experiences with a Data Efficient Neural Reinforcement learning Method (Riedmiller, 2005)](https://pdfs.semanticscholar.org/2820/01869bd502c7917db8b32b75593addfbbc68.pdf)
- The proposed algorithm (called **Neural Fitted Q Iteration**) is a special form of experience replay (and another technique called Fitted Q Iteration).

### [Double _Q_-learning (van Hasselt, 2010)](https://papers.nips.cc/paper/3964-double-q-learning.pdf)
- _Q_-learning's performance can be poor in stochastic MDPs, because of large overestimations of the action values.  The author proposes a new algorithm (called **Double _Q_-learning**, in a tabular setting) to avoid this overestimation. 
- In double _Q_-learning, we decouple action selection from the evaluation.  Two value functions are learned, and each is trained on a different set of experience samples.

### [Human-level Control through Deep Reinforcement Learning (Mnih et al., 2015)](https://web.stanford.edu/class/psych209/Readings/MnihEtAlHassibis15NatureControlDeepRL.pdf)
- This paper introduces the **Deep Q network (DQN)** algorithm, that makes use of:
	- a target network, and
	- experience replay

### [Deep Reinforcement Learning with Double _Q_-learning (van Hasselt et al., 2015)](https://arxiv.org/pdf/1509.06461.pdf)
- _Q_-learning is known to sometimes learn unrealistically high action values, because it includes a maximization step over estimated action values, which tends to prefer overestimated to underestimated values.  The authors propose a new algorithm (called **Double DQN**) and demonstrate that it reduces overestimations and leads to better performance in Atari games.
- In Double DQN, we reduce overestimations by decomposing the max operation in the target into action selection and action evaluation.

### [Asynchronous Methods for Deep Reinforcement Learning (Mnih et al., 2016)](https://arxiv.org/pdf/1602.01783.pdf)
- Note that the introduction has a nice list of solutions towards stabilizing the NN + RL combination (all pretty similar to experience replay).
- Drawbacks of experience replay: uses more memory and computation per real interaction; and requires off-policy learning algorithms that can update from data generated by an older policy.
- Instead of experience replay, we asynchronously execute multiple agents in parallel, on multiple instances of the environment.