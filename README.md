# AI
Learning about AI and making my own.
This project will be about not just using AI, but fully understanding and grasping the behind the scenes of how AI works (NOT just LLMs) and trying to make my own AIs that learn, adapt and improve themselves. 



# ACS
## When I first wanted to make my own AI, I of course didn't really know how AIs worked but I still wanted to make my own one. The online tutorials and so on were all too complex for my brain, so I decided on making my own system. I dubbed it ACS (Actions-Conditions
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
