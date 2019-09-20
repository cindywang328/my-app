**Container with Most Water**
This is a 2 pointers question; the 2 pointers start at the left and right and move inwards. At every step, we check if (distance between 2 pointers) * (minimum of the 2 heights) is greater than the current maximum. 
```
int maxArea(int* height, int heightSize) {
    int n = heightSize;
    int i = 0;
    int j = n-1;
    int maxh = 0;
    while(j>i){
        int a = (j-i)*min(height[i], height[j]);
        maxh=max(maxh, a)
        if(height[i]>=height[j]){j--;}
        else i++;
    }
    return max;
}
```
**Longest Valid Parentheses**
The DP array for this one is very interesting:
- DP\[i\] represents the longest valid parentheses, of a substring starting at 0 and ending at index *i*.
- We will only consider when the current pointer is at a closing bracket
- If the substring so far is "....()", then we add the length of the "()"; dp\[i\] = dp\[i-2\] + 2
- If the substring ends in "...abcd))" - let abcd represent possibly another substring consisting of of valid parentheses - then 
    - if abcd is valid and dp\[i-1\] is not 0 then there must have been a ( before the "abcd" part; "....(abcd))"
        - the length of the (abcd) is stored in dp\[i-1\]
    - if there was another ( beforehand - "....((abcd))" then we can find a longer valid parentheses ending at index i; 
        - check `if s[i-dp[i-1]-1] == '('` 


```
    int longestValidParentheses(string s) {
        int max = 0;
        int n = size(s);
        if(n <= 1) return 0;
        vector<int> dp(n, 0);
        
        for(int i = 1; i<n; i++){
            if(s[i] == ')'){
                if(s[i-1] == '('){
                    dp[i] = (i>= 2)?dp[i-2]+2:2;
                }
                else if (s[i-1] == ')'){
                    if(i-dp[i-1]>0 && s[i-dp[i-1]-1] == '('){
                        dp[i] = dp[i-1]+ (i-dp[i-1] > 1 ? dp[i-dp[i-1]-2]:0)+2 ;
                    } 
                }
                max = max>dp[i] ? max : dp[i];
            }
            
        }
        return max;
    }
 ```
