### Accepted
```
var isPalindrome = function(head) {
    let left = head
    const checkPalindrome =(list)=>{
        
        if(!list) return true
        //the mismsatch back up the call stack
        if(!checkPalindrome(list.next)) return false

		//if the right and left side is same, move left side next
        if(left.val === list.val){
            left = left.next
            return true

        }else return false
    }
    return checkPalindrome(head)
};
```

1. `Left`
   Move next, after the children is compared with the right side.	
2. `Right`
   Stack(FILO) is effective for moving to the end on the right side. The stack technique can be implemented using function calls.