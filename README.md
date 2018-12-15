# Arithmetic-Slices

Since an arithmetic slice is determined after 3 elements, we can go through the array and check if every consecutive 3 numbers is arithmetic. We can store the results in an array `dp[]` with the same length as `A`.

We go through the array and check if `A[i] - A[i-1] == A[i-1] - A[i-2]`. If this is true we set `dp[i] = 1`. However, if the sequence of 3 right before the current one was **also** arithmetic that means these both have the same number difference in their sequences which makes the entire sequence of 4 numbers also arithmetic. So really, setting `dp[i] = 1` is wrong, we need to set `dp[i] = 1 + dp[i-1]`.
As we progress through the sequence, we can also keep track of the total `sum` of `dp[]` so we don't have to traverse through it again to calculate.

Examples:  
` A = [1,3,5,7,9]`  
`dp = [0,0,1,2,3]` `sum = 6`  

` A = [1,1,2,5,7]`  
`dp = [0,0,0,0,0]` `sum = 0`  

` A = [1,2,3,4,7,10,12]`  
`dp = [0,0,1,2,0,1,0]` `sum = 4`
