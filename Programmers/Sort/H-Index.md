# H-Index
### Accepted
```
unction solution(citations) {
    let count=0;

    let check = citations.some(i => i>0);
    if(!check) return 0

    while(true){
        count++;
        let temp = citations.filter(a => a >=count)
        if(temp.length ===count) break;
        if(temp.length < count){
            count--;               
            break;
        }
    }
    return count
}
```

### Solution from other person
```
function solution(citations) {
    var answer = 0;

    citations.sort((a, b) => b - a);

    for(let i = 0; i < citations.length; i++) {
        if(citations[i] > i) answer++;
        else break;
    }

    return answer;
}
```

- `Sort()` is important to reduce the time in for loop
- Most of people count with for loop 
	-increase the answer, if the citation is bigger than current count
	-If the current item is lower than current count, break 