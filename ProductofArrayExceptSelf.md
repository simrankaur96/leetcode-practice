## LeetCode - Product of Array Except Self
Given an integer array nums, return an array answer such that answer[i] is equal to the product of all the elements of nums except nums[i].

The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.

You must write an algorithm that runs in O(n) time and without using the division operation.
> The above line is the kicker.

 

### Example 1:

**Input:** nums = [1,2,3,4]

**Output:** [24,12,8,6]


### Example 2:

**Input:** nums = [-1,1,0,-3,3]

**Output:** [0,0,9,0,0]
 

### Constraints:

* 2 <= nums.length <= 105
*-30 <= nums[i] <= 30
* The product of any prefix or suffix of nums is guaranteed to fit in a 32-bit integer.
 > This line is the biggest hint.

**Follow up:** Can you solve the problem in O(1) extra space complexity? (The output array does not count as extra space for space complexity analysis.)

```java
/**
* Have 2 runs through the array. Left to Right and Right to Left.
* From Left to Right
* Multiply the left product so far with i-1 th element
* From Right to Left
* Multiple the right product so far with the i+1 th element
**/

class Solution {
    public int[] productExceptSelf(int[] nums) { // 1 2 3 4
        int[] ans = new int[nums.length]; 
        int left = 1;
        ans[0] = 1;
        for(int i=1; i<nums.length; i++){
          ans[i] = left * nums[i-1]; // 1 1 2 6
          left = ans[i];
        }
        int right = 1;
        for(int i=nums.length-1; i>=0; i--){
            ans[i] *= right; 
            right *= nums[i];
        }
        
        return ans;
        
    }
}
```
