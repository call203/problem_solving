### Accepted

```
function solution(s) {

    let res = s.toLowerCase().split("")

    for(let i=0; i<res.length; i++){
        if(i>0 && res[i-1]===" " && res[i] !==" "){
            res[i] = res[i].toUpperCase();
        } 
    }
    res[0] = res[0].toUpperCase();

    return res.join("")
}
```

You need to be ware that the `space` can be placed more than once. Therefore,splitting by " " does not work, and should consider that the first letter of each word is places next to `space`.

#### Note
String is immutable, which means once a string is created, its characters cannot be changed. The code below does not work.

```
for(let i=0; i<s.length; i++){
    if(i>0 && s[i-1]===" " && s[i] !==" "){
        s[i] = s[i].toUpperCase(); // Attempt to modify s[i]
    }else{
        s[i] = s[i].toLowerCase(); // Attempt to modify s[i]
    }
}
```

### Time Complexity
O(n)
