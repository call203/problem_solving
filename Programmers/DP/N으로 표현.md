```
function solution(N, number) {
    const dp = Array.from({length: 9},()=> new Set() )
    
    for(let i=1; i<=8; i++){ 
        dp[i].add(Number(String(N).repeat(i)))
        for(let j=1; j <i; j++){
            for(const num1 of dp[j]){
             
                for(const num2 of dp[i-j]){
                    dp[i].add(num1 + num2)
                    dp[i].add(num1 - num2)
                    dp[i].add(Math.floor(num1 / num2))
                    dp[i].add(num1 * num2)
                }
            } 
        }
        if(dp[i].has(number)){
            return i
        } 
    }
    return -1
}
```

**DP Table**
The maximum number of times you are allowed to use `N` is 8. Therefore, create a `dp` table that corresponds to the number of times `N` is used. The reason the array size is 9 is because the index will start from 1.

**Memoization**
The current step can be calculated using the results from the previous steps.
```
i| i-j | j

2  = 1 + 1
2 = 2 + 1

3 = 1 + 2
3 = 2 + 1
3  = 3 + 0
```
