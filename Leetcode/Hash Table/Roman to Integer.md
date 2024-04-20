# Roman to Integer

### Accepted

```
var romanToInt = function(s) {
    const roman= new Map();
    roman.set("I",1)
    roman.set("V",5)
    roman.set("X",10)
    roman.set("L",50)
    roman.set("C",100)
    roman.set("D",500)
    roman.set("M",1000)
    let total = 0;
    for(let i=0; i<s.length; i++){
        const num = roman.get(s[i]);
        const prev = roman.get(s[i-1])
        if(i>0 && num>prev){
            total = total + num - 2 * prev
        }else{
            total+= num
        }     
    }
    return total
};

```

Used Map to store the integer value to retrieve the item effectively 

### Time complexity
O(n) , where n is the length of the input string s. it just iterate through the entire string.

### Space complexity
O(1)