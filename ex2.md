#### Exercise 2.1 In ε-greedy action selection, for the case of two actions and ε = 0.5, what is the probability that the greedy action is selected?

Based on the assumptions of ε-greedy action selection, it should be 0.5 -- because when choosing the random action we exclude the greedy action.

#### Bandit example Consider a k-armed bandit problem with k = 4 actions, denoted 1, 2, 3, and 4. Consider applying to this problem a bandit algorithm using ε-greedy action selection, sample-average action-value estimates, and initial estimates of Q1(a) = 0, for all a. Suppose the initial sequence of actions and rewards is A1 =1,R1 =1,A2 =2,R2 =1,A3 =2,R3 =2,A4 =2,R4 =2, A5 = 3, R5 = 0. On some of these time steps the ε case may have occurred, causing an action to be selected at random. On which time steps did this definitely occur? On which time steps could this possibly have occurred?

At timestep 2 this definitely occurred, as we know that the average reward associated with A1 is 1 and 
Q<sub>2</sub>(a<sub>1</sub>) > Q<sub>2</sub>(a<sub>2</sub>) = 0. Therefore, choosing A2 = 2 must have been the result of a exploration step. Similarly, this must have also occurred at time-step 5. It might have occurred at time step 1, depending on how the algorithm picks among actions with equal Q. The same is true for time step 3, at the beginning of which a<sub>2</sub> and a<sub>1</sub> have the same Q value.

If when one is picking a random action, one chooses among all actions rather than just all the ones currently considered suboptimal, then it is possible that a random action was selected at any of the time steps.