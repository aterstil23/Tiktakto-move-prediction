# Tiktakto-AI
In the past, i was confused on how to generate a list of all possible moves for the next turns in a game like chess. Trying to do the same with Tiktakto made me understand how to pass in an object that contains the past moves recursively to generate all the future possible moves.
Then there would be a way to reward each possible sets of winning moves, then to sort them by set of moves that have most points.
A problem that i encountered was at each turn that i generated all the winning moves, i tried to reuse the already generated moves by removing the list of moves that diverged from the true game as the turns went by, but the function removeothermoves took too long to compute.
Also, using brute force to verify if one set of moves was led to victory by force (meaning there was two ways to do a tiktakto in the next 2 turns which would force the oppenent to block one of the ways garanteeing the other way led to victory) was wasteful in terms of performance. 
So the reward system was simple, add 15 or 10 points to the set of moves that occupied the center early on, then reward 5 or 10 points if 1 or 2 edge was occupied.

Now, for a more complicated game like chess, it would be interesting to know how the set of moves are rewarded and how divergent movesets were discarded.
