```java
    /**15. 3Sum 
     * @param nums
     * @return
     */
    public List<List<Integer>> threeSum(int[] nums) {
    	List<List<Integer>> list = new ArrayList<List<Integer>>();
    	Arrays.sort(nums);
    	for (int i = 0; i < nums.length-2; i++) {
    		if (i > 0 && nums[i] == nums[i-1]) {
    			continue;
    		} else {
    			int s = i+1;
    			int e = nums.length-1;
    			int num = nums[i];
    			while (s < e) {
    	    		if (nums[s] + nums[e] == -num) {
    	    			List<Integer> l = new ArrayList<Integer>();
    	    			l.add(num);
    	    			l.add(nums[s]);
    	    			l.add(nums[e]);
    	    			list.add(l);
    	    			while(s < nums.length-2 && nums[s] == nums[s+1]) {
    	        			s++;
    	        		}
    	        		while(e > 0 && nums[e] == nums[e-1]) {
    	        			e--;
    	        		}
    	        		s++;
    	        		e--;
    	    		}else if (nums[s] + nums[e] > -num) {
    	    			e--;
    	    		}else if (nums[s] + nums[e] < -num) {
    	    			s++;
    	    		}
    	    		
    	    	}
    		}
    	}
    	return list;
    }
```
//先找一个a，然后在剩下的里面枚举-a,利用s和e表示枚举时开始和结束，每次移动s或e，注意去除重复