# Slider-Puzzle-Solver-using-A*-search  
Finding the minimum number of moves to solve the slider puzzle, if solvable.  

The puzzle : https://en.wikipedia.org/wiki/Sliding_puzzle  

The problem : To solve the slider puzzle for a 3 * 3 grid(and its natural generalizations) using A* search.   

Board.java : The board data type :  
                  * Hamming and Manhattan distances.  To measure how close a board is to the goal board, we define two notions of distance. The Hamming distance betweeen a board                     and the goal board is the number of tiles in the wrong position. The Manhattan distance between a board and the goal board is the sum of the Manhattan                           distances (sum of the vertical and horizontal distance) from the tiles to their goal positions.    
                  * Comparing two boards for equality : Two boards are equal if they are have the same size and their corresponding tiles are in the same positions.  
                  * Neighboring boards.  The neighbors() method returns an iterable containing the neighbors of the board. Depending on the location of the blank square, a board                     can have 2, 3, or 4 neighbors.  

A solution to the 8-puzzle problem that illustrates a general artificial intelligence methodology known as the A* search algorithm. We define a search node of the game to be a board, the number of moves made to reach the board, and the previous search node. First, insert the initial search node (the initial board, 0 moves, and a null previous search node) into a priority queue. Then, delete from the priority queue the search node with the minimum priority, and insert onto the priority queue all neighboring search nodes (those that can be reached in one move from the dequeued search node). Repeat this procedure until the search node dequeued corresponds to the goal board.  

The efficacy of this approach hinges on the choice of priority function for a search node. Two possible choices of priority functions:  

   * The Hamming priority function is the Hamming distance of a board plus the number of moves made so far to get to the search node. Intuitively, a search node with a small number of tiles in the wrong position is close to the goal, and we prefer a search node if has been reached using a small number of moves.  

   * The Manhattan priority function is the Manhattan distance of a board plus the number of moves made so far to get to the search node.  

2 Optimizations :  
  * A* search has one annoying feature: search nodes corresponding to the same board are enqueued on the priority queue many times. To reduce unnecessary exploration of useless search nodes, when considering the neighbors of a search node, don’t enqueue a neighbor if its board is the same as the board of the previous search node in the game tree.  
  * Caching the Hamming and Manhattan priorities. To avoid recomputing the Manhattan priority of a search node from scratch each time during various priority queue operations, pre-compute its value when you construct the search node; save it in an instance variable; and return the saved value as needed.   

Solver.java contains the solution to the puzzle.  
