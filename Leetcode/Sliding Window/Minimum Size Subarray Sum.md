### Accepted
```
var minSubArrayLen = function(target, nums) {
    let start=0;
    let minValue = Infinity;
    let subArraySum = 0;

    for(let end=0; end<nums.length; end++){
        subArraySum+=nums[end];

        while(subArraySum>=target){
            minValue = Math.min(minValue, (end - start) + 1)
            subArraySum-=nums[start];
            start++;
        }
    }

    return minValue === Infinity ?0 : minValue;
};
```

This is the basic problem of the sliding window algorithm.
Extend the `end` value of the sliding window until the the sum of the sliding window is greater than `target`. Reduce the `start` value of the window until the sum value is less or equal to `target`.
