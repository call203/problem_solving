# Minimum Depth of Binary Tree

## BFS
### Accepted
```
var minDepth = function(root) {

    if(root ===null) return 0
    let result = 0;
    let queue = [root];

    while(queue.length > 0){
        let len = queue.length;
        result++;
        for(let i=0; i<len; i++){
            let current = queue.shift();
            if(current.left ===null && current.right ===null) return result
            if(current.left) queue.push(current.left);
            if(current.right) queue.push(current.right);
        }
        
    }

    return result;
};

```

This is the basic solution of BFS algorithm
1. Create a queue to start the search with the root node.
2. Create a while loop to traverse the nodes.
3. Traverse all node at the current level.
4. If `current` node has children, add them to the queue <= All nodes at the same floor will be inserted in the queue.


## DFS
### Accepted
```
var minDepth = function(root) {
    if(root ===null) return 0
    let result = Infinity;
    var countMin = (node, depth)=>{
        // the node is reached to the end of the three
        if(!node.left && !node.right){
            result = Math.min(result, depth)
            return;
        } 
        if(node.left){
            countMin(node.left,depth+1)
        }
        if(node.right){
            countMin(node.right,depth+1) 
        }
        
    }
    countMin(root,1)

    return result

};

```


