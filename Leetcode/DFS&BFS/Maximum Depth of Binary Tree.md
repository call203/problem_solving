```
var maxDepth = function(root) {

    if(!root){
        return 0 ;
    }

    let left = maxDepth(root.left);
    let right = maxDepth(root.right);

    return 1 + Math.max(left, right)
    
};
```

**DFS** using recursive
1. `return` for finish the recursive
   if the root is null, return 0.
2. `return` for the result
   The length is increased by 1 with the previous sum, choosing the larger between the right and left.