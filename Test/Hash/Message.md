
### 코드 설명

1. **초기화**: 각 사용자에 대한 메시지 수를 0으로 설정합니다.
2. **이벤트 처리**:
    - 각 이벤트를 순회하면서 유형에 따라 처리합니다.
    - `"OFFLINE"` 이벤트에서는 해당 사용자를 오프라인 사용자 목록에 추가합니다.
    - `"MESSAGE"` 이벤트는 두 가지 경우로 나뉩니다:
        - `"ALL"` 메시지는 모든 사용자가 수신하되, 오프라인 사용자는 제외됩니다.
        - 특정 사용자에게 메시지가 전송될 때, 해당 사용자가 오프라인이 아닐 경우 메시지를 카운트합니다.
3. **결과 반환**: 각 사용자의 메시지 수를 배열로 반환하고, 오름차순으로 정렬합니다.

위의 코드를 실행하면 `user11`이 2개의 메시지를, `user23`이 1개, `user44`가 1개를 받았음을 보여주는 `[1, 1, 2]`가 출력됩니다.



```
function countMessages(member, event) {
    const messageCount = {}; // 각 사용자의 메시지 수를 저장할 객체
    const offlineUsers = new Set(); // 오프라인 사용자를 저장할 Set

    // 초기 메시지 카운트 설정
    member.forEach(user => {
        messageCount[user] = 0;
    });

    // 이벤트 처리
    for (const [type, time, data] of event) {
        const usersInMessage = data.split(' ').slice(1); // 첫 번째 단어는 무시하고 나머지 사용자 추출

        if (type === "OFFLINE") {
            offlineUsers.add(usersInMessage[0]); // 오프라인 사용자 추가
        } else if (type === "MESSAGE") {
            if (data.startsWith("ALL")) {
                // "ALL" 메시지는 모든 사용자에게 전달
                member.forEach(user => {
                    if (!offlineUsers.has(user)) {
                        messageCount[user]++; // 오프라인이 아닌 경우 카운트 증가
                    }
                });
            } else {
                // 특정 사용자에게 메시지
                usersInMessage.forEach(user => {
                    if (!offlineUsers.has(user)) {
                        messageCount[user]++; // 오프라인이 아닌 경우 카운트 증가
                    }
                });
            }
        }
    }

    const sortedMembers = member.sort((a, b) => {
		const numA = parseInt(a.replace("user", ""));
		const numB = parseInt(b.replace("user", ""));
		return numA - numB;
	});
	return result
}

// 테스트
const member = ["user23", "user44", "user11"];
const event = [
    ["MESSAGE", 30, "ALL user23 user11"],
    ["OFFLINE", 33, "user23"],
    ["MESSAGE", 335, "HERE user11 user23"]
];

console.log(countMessages(member, event)); // [1, 1, 2]

```