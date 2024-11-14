
# Ex.No: 9   Implementation of Alpha Beta Pruning 
### DATE:                                                                           
### REGISTER NUMBER : 2212221240060
### AIM: 
Write a Alpha beta pruning algorithm to find the optimal value of MAX Player from the given graph.
### Steps:
1. Start the program
2. Initially  assign MAX and MIN value as 1000 and -1000.
3.  Define the minimax function  using alpha beta pruning
4.  If maximum depth is reached then return the score value of leaf node. [depth taken as 3]
5.  In Max player turn, assign the alpha value by finding the maximum value by calling the minmax function recursively.
6.  In Min player turn, assign beta value by finding the minimum value by calling the minmax function recursively.
7.  Specify the score value of leaf nodes and Call the minimax function.
8.  Print the best value of Max player.
9.  Stop the program. 

### Program:
```
# Define a large negative and positive value to represent infinity
INF = float('inf')


# Alpha-Beta Pruning function
def alpha_beta_pruning(depth, node_index, maximizing_player, values, alpha, beta):
    # Base case: leaf node is reached
    if depth == 3:
        return values[node_index]

    if maximizing_player:
        max_eval = -INF
        # Recur for the two children of the current node
        for i in range(2):
            eval = alpha_beta_pruning(depth + 1, node_index * 2 + i, False, values, alpha, beta)
            max_eval = max(max_eval, eval)
            alpha = max(alpha, eval)

            # Prune the branch
            if beta <= alpha:
                break
        return max_eval
    else:
        min_eval = INF
        # Recur for the two children of the current node
        for i in range(2):
            eval = alpha_beta_pruning(depth + 1, node_index * 2 + i, True, values, alpha, beta)
            min_eval = min(min_eval, eval)
            beta = min(beta, eval)

            # Prune the branch
            if beta <= alpha:
                break
        return min_eval


# Driver code
if __name__ == "__main__":
    # This is the terminal/leaf node values of the game tree
    values = [3, 5, 6, 9, 1, 2, 0, -1]

    print("Optimal value:", alpha_beta_pruning(0, 0, True, values, -INF, INF))
```
### Output:
![Screenshot 2024-10-24 185808](https://github.com/user-attachments/assets/1c1cec52-4bf5-4ceb-9b5c-61ec5a61e0da)



### Result:
Thus the best score of max player was found using Alpha Beta Pruning.
