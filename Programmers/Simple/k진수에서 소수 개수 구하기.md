# k진수에서 소수 개수 구하기
### Accepted
```
function solution(n, k) {
    let k_number = n.toString(k)
    let answer =0;
    const check_p = (item)=>{
        
        if(item<=1) return false;
        if(item ===2) return true;
        if(item % 2 ===0) return false; 
    
        for(let i=2; i<=Math.sqrt(item); i++){
            if(item % i ===0) return false
        }
        return true
    }
    
    let p_arr = k_number.split("0")
    for(let i of p_arr){
        if(i!=="" && check_p(Number(i))) answer++
    }
    return answer
}
```


