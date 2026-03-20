## Problem  
You are given an array `prices` where `prices[i]` is the price of a given stock on day `i`.  
  
You may complete **as many transactions as you like** (buy one and sell one share multiple times).  
  
However, you **cannot hold more than one stock at a time**.  
  
Return the **maximum profit**.  
  
---  
  
## Approach  
  
Use a **Greedy strategy**.  
  
Observation:  
Whenever price increases from the previous day, we can make profit.  

profit += prices[i] - prices[i-1]

  
This effectively captures **all upward trends** in the price graph.  
  
Example:  

1 → 5 → 3 → 6

profit = (5-1) + (6-3)

---

```java
class Solution {
    public int maxProfit(int[] prices) {
        int profit = 0;
        for(int i = 1; i<prices.length; i++){
            if(prices[i] > prices[i-1]){
	            profit += prices[i] - prices[i-1];
	        }
        }
        return profit;
    }
}
```