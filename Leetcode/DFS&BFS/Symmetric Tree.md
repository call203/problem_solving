# Symmetric Tree
### Accepted
```
const isMirror= (t1, t2)=>{
    if(t1 ===null&& t2 ===null) return true;
    if(t1 ===null || t2 ===null) return false;

    return (t1.val ===t2.val) && isMirror(t1.left, t2.right) && isMirror(t1.right, t2.left);
}

var isSymmetric = function(root) {
    return isMirror(root.left,root.right)

};
```

**DFS** using recursive 
1. `return` condition for finish recursive
   consider left and right if it is null or not
2. `return` condition for the result
   the val of node should be equal and their left and right should be symmetric.