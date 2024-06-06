
### Accepted
```
var lengthOfLongestSubstring = function(s) {
    let start =0;
    let maxValue = -1;
    let subString = "";

    for(let end=0; end<s.length; end++){
        subString+=s[end];
        
        while(start<end && subString.indexOf(s[end]) !== subString.length - 1){
            subString = subString.slice(1);
            start++;
        }
        
        maxValue = Math.max(maxValue, subString.length);

    }
    return maxValue ===-1 ?0 :maxValue;

};
```

1. Move `end` to extend the length of the window.
2. If the `s[end]` existed excepted for the last elements in range of window, just remove until duplicated items are completely gone.
3. Calculate the max length of the window.