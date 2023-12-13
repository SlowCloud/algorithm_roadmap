## 선행
- 분할 정복
- monge array

## 연관
- DP 최적화

# 분할 정복을 이용한 최적화(DnC Optimization)

> 분할 정복을 이용해서 DP 계산을 최적화시켜 봅시다.

DnC Optimization을 하려면 몇 가지 선행조건이 존재한다.
우선 점화식이 대략 아래와 같이 나와야 한다.
- $DP(i, j) = min_{1 \le k \le j}(DP(i-1, k) + C(k, j))$

그리고 $C(i, j)$가 monge array가 되어야 한다. 간단히 설명하자면, 아래 조건을 만족하는 배열 또는 계산식을 가리킨다.

- $a \le b \le c \le d$ 일 때, $C(a,b) + C(c,d) \le C(a,d) + C(b,c)$

### 계산 방법

설명 추가 예정

### 왜 최적화되는가?

설명 추가 예정

### 이모저모

최댓값을 찾는 것은 하지 못한다. 최댓값은 [CHT](CHT.md)를 사용해야 한다.

## 연습 문제

- [김치[P1]](https://www.acmicpc.net/problem/11001)
- [탈옥[P1]](https://www.acmicpc.net/problem/13261)


## 도움이 된 글
- https://koosaga.com/242
- https://cp-algorithms.com/dynamic_programming/divide-and-conquer-dp.html