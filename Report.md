## Learning Algorithm

The algorithm chosen is DDPG, it an actor-critic method.  
The actor network is responsible for chosing actions based on the state and the critic network try to estimate the reward for the given state-action pair.  
DDPG in continuous control is particularly useful as, unlike discrete actions, all the actions are "choose" at every timestep with a continuous value making non-trivial to build a loss function based on these values.  
Instead, the actor network is indirectly trained using gradient ascent on the critic network, reducing the problem of building a loss function to a more classic RL problem of maximize the expected reward.  
The algorithm also leverages the fixed-Q target, double network, soft-updates and experience replay.   

## Plot of Rewards



## Ideas for Future Work  
  

Other attempts I would have liked to try to improve the learning but I didn't had the time to try them out.

- Prioritized experience replay: for previous experiences showed that can be very useful to speedup the early training of the algorithm.  
- Layer noise instead of action noise
- Several of the improvements coming from PPO: Gradient clipping, credit assignment and reward normalization.
  

## Other considerations

Variations I've tried which didn't result in a success:  

- Cosines learning rate annealing
- SGD with warm restart
- Action noise annealing 
- 20 separate local networks (actor+critic) and 1 global network (actor+critic)

Other variations which didn't improve the results significantly:

- batch normalization 
- dropout
- deeper networks
- wider networks