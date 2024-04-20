# Longest Substring Without Repeating Characters


### Accepted

```

var lengthOfLongestSubstring = function(s) {
    let map = new Map();
    let maxValue= 0;
    let left = 0

    for(let i=0; i<s.length; i++){
        while(map.has(s[i])){
            let len = map.size;
            map.delete(s[left]);
            left++;
        }
        map.set(s[i]);
        maxValue = Math.max(maxValue, map.size);
    }

    return maxValue;

};

```

With Sliding window, using two pointer 

Right pointer : for checking the value in set as well as adding the value in the set.
Left pointer : to removing the value from set and shrinking the substring.

### Time complexity
O(n) , where n is the length of the input string s. it just iterate through the entire string.

### Space complexity
O(1)


