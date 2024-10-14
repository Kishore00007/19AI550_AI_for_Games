# Ex.No: 7 Implementation of Decision Tree Learning 
## DATE:  13/09/2024
## REGISTER NUMBER : 212221240023
# AIM:
Design a decision tree for following data. 
1 Healthy, In Cover, With Ammo -> Attack
2.Hurt, In Cover, With Ammo -> Attack
3.Healthy, In Cover, Empty -> Defend
4.Hurt, In Cover, Empty -> Defend
5.Hurt, Exposed, With Ammo -> Defend
# Algorithm:
1. Start the program
2. import the necessary packages 
3. Design a training data and test data 
4. Create a decision tree classifier model
5. Output the predictions 
6. Visualize the decision tree 
# Program:
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





# Output:
![Screenshot 2024-10-14 224952](https://github.com/user-attachments/assets/657ed7d7-4f84-48cd-b3b0-7461fcd69b98)



# Result:
Thus the optimum value of max player was found using minimax search.
