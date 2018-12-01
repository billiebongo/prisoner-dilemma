# 3-way prisoner-dilemma



The goal of the task is to achieve a high score among a large group of other players (~100) in the
game of 3-way iterated prisoner’s dilemma. Round-robin of the game would be programmatically carried out and a total score would be tabulated for each player at the end of 100 rounds for each player.

3-way iterated prisoner's dilemma is a variant of the usual 2-way prisoner dilemma problem. A more detailed explanation can be found here: [3-way PD game ](https://www.classes.cs.uchicago.edu/archive/1998/fall/CS105/Project/node6.html)


The dominant strategy in a normal 2-way prisoner’s dilemma is to defect, however, the goal is to attain a relative high score amongst a large group of players. For example, if you defect in all rounds while all of the other players cooperate amongst themselves, but defected with you as a form of retaliation or self-defense, you would get the lowest average scores.
A strategy encouraging cooperation would be a better strategy. The knowledge of other
agents is needed, however this knowledge is not available. 
in assessing the performance of my agent for the task.Tit for tat strategy is popular for sequences of prisoner's dilemma and it is a common strategy in real-life, ie retaliative tariffs. This implementation is a variant of the classic tic-for-tac which aims to gain a higher score by cooperating when others cooperate, while at the same time
defending themselves by defecting against defects. In order to not be put in the losing end with
matches with tit for tat agents, to always cooperate is the best strategy. 

It will defect when at least one of the other 2 defects so
as to not be taken advantage of and also to minimise the points lost if the opponents defect.
After defecting to retaliate, it will cooperate the immediately next round (coopNextRound=true)
to signal willingness to cooperate. If at least one of them do not cooperate after my chance
given in that round, my agent will -1 from the number of chanceGiven and defect. The agent
would only give chance 5 times (signal willingness to cooperate even opponents defected in
previous round) ( int chanceGiven = 5). After that it might suggest that it is the case that at least
one of them would not cooperate when my agent signal willingness to cooperate. If both show
no signs of cooperating, defect all the way.

This agent would also defect all the way after 95 rounds. This would be effective against agents
who decide to defect only by considering the percentage of history of defects/cooperates and
might choose to cooperate when my agent defects. 

To defect in the very last round is the best
strategy, which would gain the best score regardless whether the other agents cooperate or
defect simply because there is no "next round" which allows opportunity for retaliation. 

Sample Evaluation of performance against other standard agents
>Tournament Results (example)

| Player            | Points        |
| ------------------|:-------------:| 
|TolerantPlayer     | 170.2322      |  
|prisoners.MY_PLAYER| 168.36728     | 
| T4TPlayer         |164.49934      | 
| FreakyPlayer      | 147.01097     |
| RandomPlayer      |  143.24231    |
| NicePlayer        | 140.7134      |
| NastyPlayer       | 130.7342      |

Results vary, but in almost all the tournaments, MY_PLAYER, T4T and Tolerant players are the top
3 players.

This implementation assesses the performance of my strategy by comparing scores with the standard
agents of this task, FreakyPlayer, NicePlayer, RandomPlayer, NastyPlayer. These are "extreme cases" and not representative of the real players this agent has to go up against. might be misleading

Rounds introducing 2 players, student1 and student2, with strategies that are closer to actual strategies

Student1: This agent uses a variant of T4T. It will cooperate by default and every 10 rounds
decide if to retaliate(defect) if the defect rate in the last 10 rounds is above a threshold
Student2: This agent will retaliate if the defect rate of last 25 rounds of the other agents is above
0.25%, otherwise cooperate.

> Tournament Results(removed unlikely players like Nasty, Nice and Freaky which would skew
evaluation of a realistic tournament)


| Player             | Points        |
| -------------------|:-------------:| 
|prisoners.student2  | 154.32132     | 
| prisoners.MY_PLAYER|153.28175      | 
| TolerantPlayer     |152.46585      |
| prisoners.student1 |   151.9193    |
| T4TPlayer          | 151.75694     |
| RandomPlayer       | 100.9449      |

Results vary widely but the range of scores for the top 5 of the 6 is almost always less than 4
points. It is hard to conclude the performance amongst so few agents.
