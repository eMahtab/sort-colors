# Sort Colors
## https://leetcode.com/problems/sort-colors

# Implementation 1 : Counting 0's, 1's, 2's
```java
class Solution {
    public void sortColors(int[] nums) {
        if(nums == null || nums.length < 2) return;
        
        int zeros = 0, ones = 0, twos = 0;
        for(int i = 0; i < nums.length; i++) {
            if(nums[i] == 0)
                zeros++;
            else if(nums[i] == 1)
                ones++;
            else
                twos++;
        }
        int index = 0;
        for(int i = 0; i < zeros; i++)
            nums[index++] = 0;
        for(int i = 0; i < ones; i++)
            nums[index++] = 1;
        for(int i = 0; i < twos; i++)
            nums[index++] = 2;
    }
}
```

# Implementation 2 : One Pass
```java
class Solution {
    public void sortColors(int[] nums) {
        if(nums == null || nums.length < 2) return;
        
        int low = 0, high = nums.length - 1, index = 0;
        while (index <= high) {
            if (nums[index] == 0) 
                swap(nums, low++, index++);
            else if (nums[index] == 2) 
                swap(nums, index, high--);
            else
                index++;
        }
    }

    private void swap(int[] nums, int i, int j) {
        int tmp = nums[i];
        nums[i] = nums[j];
        nums[j] = tmp;
    }
}
```

# References :
1. https://www.youtube.com/watch?v=sEQk8xgjx64
2. leetcode.com/articles/sort-colors/271695/Sort-Colors/260760
