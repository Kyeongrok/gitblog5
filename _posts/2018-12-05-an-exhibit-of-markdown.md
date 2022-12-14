---
layout: post
title: 최적전략(Optimal Strategy) 알고리즘
subtitle: 최적전략 알고리즘을 이용한 항상 승리하는 알고리즘 만들기
categories: markdown
tags: [dynamic, programming, algorithm]
---


## 최적전략 알고리즘 문제 설명

```java
int list = {2, 7, 40, 19, 4, 9}
```

위 배열과 같이 짝수개의 숫자 카드가 일렬로 놓여있습니다. 나와 상대방 
이 번갈아 가면서 카드를 가지고 올 수 있는데 현재 놓여있는 카드 중에서 맨 앞에 있는 카드 또는 맨 뒤에 있는 카드를 가지고 올 수 있습니다.

예를들어 [2, 7, 40, 19, 4, 9] 카드가 있다면 카드를 가지고 올 때 맨 앞에 있는 2 또는 맨 뒤에 있는 9를 가지고 올 수 있습니다. 처음부터 40이나 19를 가지고 올 수는 없습니다.

[2, 7, 40, 19, 4, 9]여기에서 9를 가지고 왔다면 상대방은 [2, 7, 40, 19, 4] 중 2와 4를 가지고 갈 수 있습니다.

이 게임은 가지고온 카드의 숫자 총 합이 많은 사람이 이기는 게임입니다.

내가 먼저 카드를 가지고 올 수 있을 때. 이 게임에서 항상 승리 할 수 있는 알고리즘을 만들어 보세요. 여기에서 상대방은 단순히 남아있는 숫자 중 큰 숫자를 가지고 가는 것이 아니라 그 순간에 최적의 선택을 합니다.


### 목차

1. 문제 풀이 방향 설명
2. 단계1 - 숫자가 1개만 있는 경우 최적 선택


## 문제 풀이 방향

> Dynamic Programming을 적용하여 풀 예정입니다.

숫자가 4개만 있는 경우의 최적 선택은 숫자가 3개만 있는 최적 선택을 기준으로 최적 선택 값을 특정 할 수 있습니다.

예를들면 2, 7, 40, 19가 있을 때 최적 선택은

2, 7, 40만 있을때의 최적선택과 7, 40, 19만 있을때의 최적 선택을 참고하여 어떤것이 최적인지를 알 수 있습니다.

마찬가지로 숫자가 3개만 있을 때의 최적 선택은 숫자가 2개만 있을때의 최적 선택을 참고하여 알 수 있습니다. 2, 7, 40 이렇게 3개의 숫자만 있는 경우의 최적 선택은 2, 7만 있을때와 7, 40만 있을때의 최적 선택을 했을때를 참고할 수 있습니다.


## 단계 1 - 숫자가 1개만 있는 경우 최적 선택

숫자가 1개만 있을 때의 최적 선택은 아래와 같이 **dp**에 기록 할 수 있습니다.

| 2   | 7   | 40   | 19   |
|-----|-----|------|------|
| 2,0 |     |      |      |
|     | 7,0 |      |      |
|     |     | 40,0 |      |
|     |     |      | 19,0 |



*Note: 숫자가 1개인 경우 상대방은 가져갈 카드가 없기 때문에 0으로 표시 합니다.




