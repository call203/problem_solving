### Accepted
```
var searchInsert = function(nums, target) {

    let start= 0;
    let end = nums.length - 1;
    while(start <= end){

        let mid = Math.floor((start + end)/2);

        if(nums[mid] ===target){
            return mid;
        }else if(nums[mid]>target){
            end = mid-1;
        }else{
            start = mid+1;
        }
    }

    return start
};
```

This is basic problem of `Binary Search`.

### What is Binary Search?
- Find the specific item in large range or a sorted range.
- choose the random mid to find the result.
- The important thing is to determine the proper minimum and maximum values.
- The Time complexity is `O(log n)`.
