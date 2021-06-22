## LeetCode: 3sum
Given an integer array nums, return all triplets [nums[I], nums[j], nums[k]] such that i!=j , j!=k and k!=I 
and nums[I] + nums[j] + nums[k] == 0
 
### Example 1:
**Input:** [-1, 0, 1, 2, -1, -4]

**Output:** [[-1, 0, 1], [-1, -1, 2]]

### Constraints
* 0 <= nums.length <= 3000
* -10^5 <= nums[I] <= 10^5

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
    	List<List<Integer>> threeSumTriplets = new ArrayList<>();

	if(nums.length < 3){
		//If length of num is less than 3, we should be returning an empty list, as there are no possible triplets.
		return threeSumTriplets; 
	}
	
	Arrays.sort(nums);

	for ( int i = 0; i < nums.length; i++ ) {
        if ( i > 0 && nums[i] == nums[i-1]) //skipping duplicates
				continue;
		int target = 0 - nums[i];
		int j = i + 1;
		int k = nums.length - 1;
		while( j < k) {
			if ( nums[j] + nums[k] == target ) {
				List<Integer> triplet = new ArrayList<>();
				triplet.add(nums[i]);
				triplet.add(nums[j]);
				triplet.add(nums[k]);
				j++;
				k--;
				threeSumTriplets.add(triplet);
				while(j<k && nums[j] == nums[j-1]) j++; //skipping duplicates
				while(j<k && nums[k] == nums[k+1]) k--; //skipping duplicates
			}
			else if ( nums[j] + nums[k] > target ) {
				k--;
			} 
			else {
				j++;
			}
		}
	}

	return threeSumTriplets;
    }
}
```
