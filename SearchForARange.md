## LeetCode - Search For a Range

Given an array of integers nums sorted in ascending order, find the starting and ending position of a given target value.

If target is not found in the array, return [-1, -1].

You must write an algorithm with O(log n) runtime complexity.

 

### Example 1:

**Input:** nums = [5,7,7,8,8,10], target = 8

**Output:** [3,4]

### Example 2:

**Input:** nums = [5,7,7,8,8,10], target = 6

**Output:** [-1,-1]

### Example 3:

**Input:** nums = [], target = 0

**Output:** [-1,-1]

### Constraints:

* 0 <= nums.length <= 10^5
* -10^9 <= nums[i] <= 10^9
* nums is a non-decreasing array.
* -10^9 <= target <= 10^9

```java
class Solution {
    public int[] searchRange(int[] nums, int target) {
        int left = 0, right = nums.length - 1;
        int range[] = new int[2];
        range[0] = -1;
        range[1] = -1;
        while(left <= right){
          int mid = left + (right - left)/2;
          if(target < nums[mid]){ //current mid is greater than target, move window to the left.
            right = mid-1;
          } else if (target > nums[mid]){ //current mid is less than target, move window to the right.
            left = mid+1;
          } else { //mid index is equal to target
            left = mid;
            right = mid;
            while(left>=0 && nums[left] == target) left--;
            while(right<=nums.length-1 && nums[right] == target) right++;
            range[0] = left+1;
            range[1] = right-1;
            return range;
          }
        }
        return range;
    }
}
```
