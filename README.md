# Tiktakto-move-prediction
In the past, i was confused on how to generate a list of all possible moves for the next turns in a game like chess. Trying to do the same with Tiktakto made me understand how to pass in an object that contains the past moves recursively to generate all the future possible moves.
Then there would be a way to reward each possible sets of winning moves, then to sort them by set of moves that have most points.
A problem that i encountered was at each turn that i generated all the winning moves, i tried to reuse the already generated moves by removing the list of moves that diverged from the true game as the turns went on and it seems it cost a lot (takes a lot of computation time) to check for every set of winning moves which set diverged remove them and reallocate the rest of the winning moves to fill up the removed element (vector of moves) in the vector (vector of vector of moves). So to be able to use removeothermoves without having to wait too long it's better to generate predictions later on in the game (2 or 3 moves in) only for the version that uses removeothermoves. Otherwise the version without removeothermoves is quicker in general (by regenerating the winning moves each turn).
Even though it takes time to remove the divergent moves (even more time than to regenerate the winning moves at each turn) i still included a second version of the code that uses the function removeothermoves (removing the divergent winning moves).
Also, using brute force to verify if one set of moves was led to victory by force (meaning there was two ways to do a tiktakto in the next 2 turns which would force the oppenent to block one of the ways garanteeing the other way led to victory) was wasteful in terms of performance. 
So the reward system was simple, add 15 or 10 points to the set of moves that occupied the center early on, then reward 5 or 10 points if 1 or 2 edge was occupied.

Now, it would be interesting to now how the set of winning moves are rewarded in a more complex game like chess.




When you run the application:
it says "enter 1 to start game".
As long you don't enter 1 it won't start.
Then it says:
"Enter o for round and x for x."
(The lower letter 'o' or the lower case letter 'x'
I've made the game so that every even turn starting by 0 has to be player by "o". 
So then, at each turn it asks, 
"Press 1 to generate predictions". 
So at each turn to generate all the possible next moves sorted by best to worst winning moves, enter 1 or enter another value to refuse.
Then' if you entered ! to generate predictions' it asks:
"Press 1 to see best set of moves predicted".
If you enter something than 1, it means you refused. Otherwise, it will print the best set of moves leading to victory that is predicted.
Note that at this point, it will only show you the set of moves, but not make the move yet.
Then it says:
"Press 1 to make predicted move".
If you press 1, it will make the next best move for you.
If you press another value than 1, it will ask:
"position", which is the position on the board you'd like to play from 0 to 8, 0 to 2 for the row, 3 to 5, second row and 6 to 8, third row.
After that it prints the board.
The ID for round player is 1 and for the x player is -1.

If you want to see the number of winning moves, you can add print statement after the generate moves function genbestmoves(...). std::cout<<bestmovesforround.size()<<std::endl; for round and for x,  
std::cout<<bestmovesforx.size()<<std::endl;
