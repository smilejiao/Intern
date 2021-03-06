```java
    /**33. Search in Rotated Sorted Array 
     * @param nums
     * @param target
     * @return 有序数组旋转一次，查找target
     */
    public int search(int[] nums, int target) {
    	int s = 0;
    	int e = nums.length-1;
    	while (s<=e) {
    		int mid = (s+e)/2;
    		if (nums[mid] == target){ 
    			return mid;
    		} else if (target < nums[mid]){
    			if (nums[mid] < nums[e]) {//后
    				e = mid-1;
    			} else {
    				if (target < nums[s]) {
    					s = mid + 1;
    				} else {
    					e = mid - 1;
    				}
    			}
    		} else {
    			if (nums[mid] > nums[s]) {//左
    				s = mid + 1;
    			} else {
    				if (target > nums[e]) {
    					e = mid - 1;
    				} else {
    					s = mid + 1;
    				}
    			}
    		}
    	}
    	return -1;
    }
```
明确rotated sorted array的特性，那么就是至少有一侧是排好序的（无论pivot在哪，自己画看看）。接下来就只需要按照这个特性继续写下去就好。以下就以伪代码方法来说明：

    如果target比A[mid]值要小
          如果A[mid]右边有序（A[mid]<A[high])
                那么target肯定不在右边（target比右边的都得小），在左边找
          如果A[mid]左边有序
                那么比较target和A[low]，如果target比A[low]还要小，证明target不在这一区，去右边找；反之，左边找。
    如果target比A[mid]值要大
         如果A[mid]左边有序（A[mid]>A[low]）
               那么target肯定不在左边（target比左边的都得大），在右边找
         如果A[mid]右边有序
               那么比较target和A[high]，如果target比A[high]还要大，证明target不在这一区，去左边找；反之，右边找。