*Container with Most Water*
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
