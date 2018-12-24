
#### Ex2.1: In ε-greedy action selection, for the case of two actions and ε = 0.5, what is the probability that the greedy action is selected?

Based on the assumptions of ε-greedy action selection, it should be 0.5 -- because when choosing the random action we exclude the greedy action.

#### Ex2.2: Bandit example Consider a k-armed bandit problem with k = 4 actions, denoted 1, 2, 3, and 4. Consider applying to this problem a bandit algorithm using ε-greedy action selection, sample-average action-value estimates, and initial estimates of Q1(a) = 0, for all a. Suppose the initial sequence of actions and rewards is A1 =1,R1 =1,A2 =2,R2 =1,A3 =2,R3 =2,A4 =2,R4 =2, A5 = 3, R5 = 0. On some of these time steps the ε case may have occurred, causing an action to be selected at random. On which time steps did this definitely occur? On which time steps could this possibly have occurred?

At timestep 2 this definitely occurred, as we know that the average reward associated with A1 is 1 and 
Q<sub>2</sub>(a<sub>1</sub>) > Q<sub>2</sub>(a<sub>2</sub>) = 0. Therefore, choosing A2 = 2 must have been the result of a exploration step. Similarly, this must have also occurred at time-step 5. It might have occurred at time step 1, depending on how the algorithm picks among actions with equal Q. The same is true for time step 3, at the beginning of which a<sub>2</sub> and a<sub>1</sub> have the same Q value.

If when one is picking a random action, one chooses among all actions rather than just all the ones currently considered suboptimal, then it is possible that a random action was selected at any of the time steps.

#### Ex2.3: In the comparison shown in Figure 2.2, which method will perform best in the long run in terms of cumulative reward and probability of selecting the best action? How much better will it be? Express your answer quantitatively.

The ε = 0.01 method would improve more slowly, but eventually would perform better than the ε = 0.1 and greedy method in terms of both the cumulative reward and probability of selecting the best action.

This is because – assuming stationarity – it is guaranteed to find the optimal action and then exploit it. Once the algorithm has found the optimal action, it will exploit it 99\% of the time, while the ϵ=0.1will only exploit the optimal action 90\% of the time.

Let’s say that the average Q value of suboptimal values is q<sub>s</sub> Then we know that:
- ϵ = 0.01 will have an average reward of (0.01 x q<sub>s</sub>) + (0.99  x q<sub>opt</sub>)
- ϵ = 0.1 will have an average reward of (0.10 x q<sub>s</sub>) + (0.90 x q<sub>opt</sub>)

Depending on how large the gap between q<sub>s</sub> and q<sub>opt</sub>is, this could change the performance of the algorithm very much.

However, on average q<sub>s</sub> < q<sub>opt</sub> ∴ ϵ = 0.01 would be most optimal in the long run. 

#### Ex2.4 If the step-size parameters, αn, are not constant, then the estimate Qn is a weighted average of previously received rewards with a weighting different from that given by (2.6). What is the weighting on each prior reward for the general case, analogous to (2.6), in terms of the sequence of step-size parameters?

2.6: Q<sub>n+1</sub> = (1-α)<sup>n</sup>Q<sub>1</sub>  + \sum {i=1}^{n} α(1-α)<sup>n-i</sup>R<sub>i</sub>

The general form:
- Q<sub>n+1</sub>  = Q<sub>n</sub> + α<sub>n</sub> (R<sub>n</sub> - Q<sub>n</sub> )
- 			       = α<sub>n</sub> R<sub>n</sub> + 1 -α<sub>n</sub> Q<sub>n</sub> 
- 			       = α<sub>n</sub> R<sub>n</sub> + (1 - α<sub>n</sub>) (α<sub>n -1</sub>) R<sub>n -1</sub> + (1 - α<sub>n-1</sub>) Q<sub>n -1</sub> 
-			       = α<sub>n</sub> R<sub>n</sub> + (1 - α<sub>n</sub>) α<sub>n -1</sub> R<sub>n -1</sub> +  (1 -α<sub>n</sub>) (1 - α<sub>n -1</sub>) Q<sub>n -1</sub>
- 			       = \sum {i=1}^{n}(α<sub>i</sub> R<sub>i</sub> \sum {j=1}^{n-1}(1 - α<sub>j</sub>)) + Q<sub>1</sub> \sum {i=1}^n(1 - α<sub>i</sub>)
			       