## 선행

- 세그먼트 트리

# 느리게 갱신되는 세그먼트 트리(Lazy Propagation)

> 구간 질의, 구간 갱신을 $O(logN)$ 안에 수행하는 자료구조

크기가 $N$인 $l$, $r$ 사이의 구간에 대해 갱신이 필요할 경우, 세그먼트 트리는 $O(NlogN)$만큼의 시간복잡도를 가진다. Lazy Propagation을 사용하면 $O(logN)$ 안에 구간 갱신이 가능하다.

구간 갱신을 미루기 위해, 각 구간마다 갱신값을 기억해 둘 새로운 배열과 갱신함수가 필요해진다.

```
// 크기는 세그먼트 트리의 크기와 동일하다.
vector<int> lazy;

void prop(int n, int s, int e) {
    /* Lazy하게 갱신시켜주는 코드 */
}
```

위의 함수는 기존 세그먼트 트리의 갱신/질의 함수의 처음에 추가된다.

```
void update(/* ... */) {
    prop(n, s, e); // 새로 추가되는 함수
    /* ... */
}
```
```
int query(/* ... */) {
    prop(n, s, e); // 새로 추가되는 함수
    /* ... */
}
```

구간합을 구하는 세그먼트 트리가 있고, $l$, $r$ 구간에 $v$를 더하는 쿼리가 있다고 가정한다.

기존의 업데이트 함수는 아래와 같았다.
```
void update(int i, int v, int n, int s, int e) {
    if(i < s || e < i) return;
    if(s == e) {
        seg[n] = v; return;
    }
    /* ... */
}
```

이 업데이트 함수는 아래와 같이 변한다.

```
void update(int l, int r, int v, int n, int s, int e) {
    prop(n, s, e); // 느리게 갱신
    
    if(r < s || e < l) return;

    // 구간 내에 들어오면 느린 갱신 설정
    if(l <= s && e <= r) {
        lazy[n] = v; // 갱신값 설정
        prop(n,s,e); // 느리게 갱신
        return;
    }

    /* ... */
}
```

느리게 갱신하는 함수는 아래와 같다.
```
void prop(int n, int s, int e) {
    // 갱신값이 존재한다면
    if(lazy[n]) {

        // 구간 값을 갱신한다.
        seg[n] += lazy[n] * (e - s + 1);

        // 리프 노드가 아니라면, 하위 노드로 갱신값을 전달한다.
        if(s != e) {
            lazy[n * 2] += lazy[n];
            lazy[n * 2 + 1] += lazy[n];
        }

        // 갱신값을 초기화한다.
        lazy[n] = 0;
    }
}
```

위와 같이 코드를 작성하면, 구간 갱신 시 리프 노드까지 진입하지 않고 lazy 배열에 값을 저장하게 된다. 그리고 갱신/질의 시 각 구간에 진입할 때에만 prop 함수를 통해 구간 값을 갱신하게 되므로 불필요한 갱신이 줄어들게 된다.

## 구현

## 연습 문제

- 연습 문제
    - [구간 합 구하기[P4]](https://www.acmicpc.net/problem/10999)

- 응용 문제
    - 미술 시간[?]

- 어려운 문제
    - 복잡한 Lazy Prop
        - [수열과 쿼리 13[P1]](https://www.acmicpc.net/problem/13925)