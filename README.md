# AI
Learning about AI and making my own.
This project will be about not just using AI, but fully understanding and grasping the behind the scenes of how AI works (NOT just LLMs) and trying to make my own AIs that learn, adapt and improve themselves. 



## ACS
### Concept of ACS
 
When I first wanted to make my own AI, I of course didn't really know how AIs worked but I still wanted to make my own one. The online tutorials and so on were all too complex for my brain, so I decided on making my own system. I dubbed it ACS (Actions-Conditions
System). 

Here is How it works: We make a matrix of values (all starting at say zero, so an zero matrix). We make conditions (the things the AI takes into consideration in its decision-making, boolean values) as the rows and the actions (the things the AI can choose to do) as the columns. You can switch the actions and conditions if you want to, just make sure that actions and conditions aren't on the same row/column and always remember how you place them. 
```
  A1   A2  A3
C1 1   2   3
C2 4   5   6
C3 7   8   9

```
Suppose this 3x3 matrix of 3 conditions and 3 actions. 
Each element in the matrix means how much that condition impacts the value of that action.
In laymen's terms - C1 increases the value of all 3 actions, but it increases the value of A3 MORE than that of A1 because (A3,C1) is MORE than (A1,C1). 
Now, all we have to do is: when the AI has to evaluate which decision (action) to take, it simply goes thru all the conditions and checks if they are fulfilled (true or not). If the action IS true, then all of the condition's values are added to to each respective action's value. E.g. - if C1 is true, then A1 increases by +1, A2 by +2, A3 by +3. If C2 is true, its respective own values are also added to each action and so on, thus checking all the conditions. Only those conditions that are true get their values be added to the respective action's value. In the end, we simply check which action has the highest total value, or - *importance* given these conditions and this action is chosen. If 2 actions share the same highest value, then the AI can randomly pick either.

> [!NOTE]
> It doesnt matter if there is no single action with the highest value, as in that case the AI can choose any of the highest-value actions. It will simply eventually *learn* which action IS in fact the most important one in this same condition-combination.

Thus say C1 and C3 are true, but C2 is not.
```
  A1   A2  A3
C1 1   2   3
C3 7   8   9

```
>[!TIP]
>I removed the row containing C2 because C2 was false in this example, thus its elements wont impact the action we are taking and thus we can eliminate it for clarity. This can be done for ALL conditions that are false in any decision-making step.

Now, we have to evaluate the importance of each action, to do that we just sum up all the values on the same column as the respective action. A1 is equal to 8 (1+7), A2 is 10 (2+8), whilst A3 is 12 (3+9).
From here, we get that A3 is the most important action here, due to 12 being the highest value for any action. 
Thus action 3 is the chosen one. 

### AI learning with ACS.
Teaching an AI with ACS is extremely in fact simple. All we need is to set up this matrix of given actions and conditions, as well as we need to figure out how to score the AI. 

Scoring an AI is done by evaluating the given environment that the AI is in and adding (or subtracting) points given that. For example say in chess-  we could add points to such an AI that decides to capture a piece, execute an checkmate, whilst subtracting points for loosing pieces, blundering and so on. 
>[!WARNING]
>Technically speaking ACS wont actually be that good for chess because chess requires thinking forward and evaluating a large amount of things / aspects, thus this was given only as an example. you can ofcourse still try to make a chess-bot using ACS, I simply wont recommend it as a first project.

After each trial, if the current AI has atchieved an higher total score than the current record-holder, its variant of the matrix values becomes the standart. if Not, in the next trial / generation, the AI's matrix is reset to that of currently-best plus slight mutations in element values.

This is literally it, just start an AI with a zero matrix (all values are equal to 0s), let it run and evaluate for a given amount of runs, if the run is better than the currently-best one then it becomes the *default* one, otherwise the next generation has its matrix be that of the best one but slightly randomly mutated.

### Example of ACS in work.

Say we have to teach an AI to balance a rod. 

The AI is fed just 4 conditions: is it leaning left, leaning right, falling towards left, falling towards right. In addition it is given just 3 actions: push it towards left, push it towards right, or just do nothing (the AI has its score be subtracted for too much actions taken).

>[!TIP]
>If you want to, you can look up the files in this repository at the top.


<img width="1306" height="740" alt="image" src="https://github.com/user-attachments/assets/32318d5a-9007-49fe-ba7e-a276b0a79065" />
Just by running the simulation a few hundred times, the AI is able to very quickly approach the optimal matrix.


<img width="1055" height="645" alt="image" src="https://github.com/user-attachments/assets/58730eb0-30e7-43bb-9eec-2ed220281fa1" />

Whilst after more than a thousand trials, its able to improve significantly. 

<img width="1039" height="616" alt="image" src="https://github.com/user-attachments/assets/daa9c0c1-c378-4f7a-92a0-cb7de7d752f4" />
Note how as the AI becomes better and better, it becomes exponencially harder and harder to make it better. 



