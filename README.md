# deeprl-notes
my notes on the history of (deep) RL // very much still a work in progress

## [Learning from Delayed Rewards (Watkins, 1989)](http://www.cs.rhul.ac.uk/~chrisw/new_thesis.pdf)
- $Q$-learning is first introduced; the proof of convergence is only outlined.

## [Q-Learning (Watkins and Dayan, 1992)](http://www.gatsby.ucl.ac.uk/~dayan/papers/cjch.pdf)
- A full proof that $Q$-learning converges.
- $Q$-learning converges to the optimum action-values with probability 1 so long as all actions are repeatedly sampled in all states and the action-values are represented discretely.

## [Issues in using Function Approximation for Reinforcement Learning (Thrun & Schwartz, 1993)](http://citeseerx.ist.psu.edu/viewdoc/download?doi=10.1.1.73.3097&rep=rep1&type=pdf)
- In order to be of use in more complex domains (that are too large to be searched exhaustively), RL techniques must be combined with generalizing function approximation methods such as NNs.  TD-Gammon represents an early success of this combination. 
- Function approximators induce some noise (generalization error) on the output predictions.  This noise can lead to a systematic overestimation effect of values, where the agent fails to learn an optimal policy in certain situations.
- Authors provide concrete examples where overestimation leads to suboptimal policies, even asymptotically.

## [Temporal Difference Learning and TD-Gammon (1995)](https://courses.cs.washington.edu/courses/cse590hk/01sp/Readings/tesauro95cacm.pdf)
- A very accessible introduction to TD-Gammon.

## [Double Q-learning (2010)](https://papers.nips.cc/paper/3964-double-q-learning.pdf)
- $Q$-learning's performance can be poor in stochastic MDPs, because of large overestimations of the action values.  The author proposes a new algorithm (called **Double Q-learning**, in a tabular setting) to avoid this overestimation.

## [Human-level control through deep reinforcement learning (2015)](https://web.stanford.edu/class/psych209/Readings/MnihEtAlHassibis15NatureControlDeepRL.pdf)

## [Deep Reinforcement Learning with Double Q-learning (van Hasselt et al., 2015)](https://arxiv.org/pdf/1509.06461.pdf)
- Q-learning is known to sometimes learn unrealistically high action values, because it includes a maximization step over estimated action values, which tends to prefer overestimated to underestimated values.  The authors propose a new algorithm (called **Double DQN**) and demonstrate that it reduces overestimations and leads to better performance in Atari games.
