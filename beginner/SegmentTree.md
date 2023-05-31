## 선행

- 재귀

## 연관

- 분할 정복
- 누적합

# 세그먼트 트리

세그먼트 트리는 구간 내 값 갱신 및 질의에 강력한 자료구조이다.
한 번 배워두면, 많은 문제들을 세그먼트 트리로 비틀어 풀 수 있게 된다.

세그먼트 트리로 들 수 있는 가장 대표적인 에시는 구간합을 구하는 문제이다.
갱신이 이루어지지 않는 구간합 문제의 경우, 누적합을 이용하여 빠르게 풀 수 있다.

누적합을 이용한다면 전처리에 $O(n)$, 구간합 확인 시 $O(1)$만큼이 걸린다. 하지만 갱신이 필요해질 경우, 매 갱신 시마다 $O(n)$ 만큼의 시간이 걸린다. 갱신을 요구하는 쿼리가 $Q$만큼 주어진다면, 시간복잡도가 $O(Qn)$이 된다.

일반적인 문제에서는 보통 $100'000$만큼의 $n$과 $100'000$ 이상의 $Q$가 주어지므로 시간 내로 계산하는 것은 불가능하다.

세그먼트 트리를 사용한다면, 전처리에 $O(nlogn)$, 갱신과 확인 시 $O(logn)$만큼의 시간이 걸린다.

크기가 $n$인 배열에 대해 세그먼트 트리를 구성할 경우, 세그먼트 트리의 크기는 $O(2n)$이 된다.

## 구현

구간합을 구하는 세그먼트 트리를 작성하였다.

## C++

> 재귀 세그먼트 트리

```
// 웬만한 STL들을 한번에 불러올 수 있는 헤더입니다.
#include <bits/stdc++.h>

vector<int> seg;

// 값을 갱신하는 함수이다.
// i는 값을 갱신할 배열의 위치, v는 값을 가리킨다.
// n은 세그먼트 트리의 노드를 가리키고 있다.
// s와 e는 현재 노드가 커버하고 있는 범위를 나타낸다.
void update(int i, int v, int n, int s, int e) {
    // 만약 인덱스가 현재 노드의 범위를 벗어났다면, 함수를 벗어난다.
    if (i < s || e < i) return;

    // s와 e가 같다면, 배열 한 칸을 가리키고 있다.
    if (s == e) {
        seg[n] = v; return;
    }

    // s와 e의 중간값을 구한다.
    int m = (s + e) / 2;

    // 왼쪽 범위와 오른쪽 범위에 대해 재귀로 갱신한다.
    update(i, v, n*2, s, m);
    update(i, v, n*2+1, m+1, e);

    // 갱신한 결과를 구한다.
    seg[n] = seg[n*2] + seg[n*2+1];
}

void query(int l, int r, int n, int s, int e) {
    if (r < s || e < l) return 0;
    if (l <= s && e <= r) return seg[n];

    int m = (s + e) / 2;

    return query(l, r, n*2, s, m) + query(l, r, n*2+1, m+1, e);
}

int main() {
    // cin, cout의 입출력을 scanf, printf만큼 빠르게 해 주는 코드이다.
    ios::sync_with_stdio(0); cin.tie(0);

    int N; cin >> N;
    seg.resize(N*2 + 1);
    for(int i = 1; i <= N; i++) {
        int n; cin >> n;
        update(i, n);
    }

    int Q; cin >> Q;
    while(Q--) {
        int op, a, b; cin >> op >> a >> b;
        if(op == 1) {
            update(a, b, 1, 1, N);
        }
        else {
            cout << query(a, b, 1, 1, N) << endl;
        }
    }
}
```

> 비트 반복문 세그먼트 트리

```
vector<int> seg;
int bias;

void update(int i, int v) {
    i |= bias;
    seg[i] = v;
    while(i >>= 1) {
        seg[i] = seg[i << 1] + seg[i << 1 | 1];
    }
}

int query(int l, int r) {
    l |= bias; r |= bias;
    int ans = 0;
    while(l <= r) {
        if(l & 1) ans += seg[l++];
        if(~r & 1) ans += seg[r--];
        l >>= 1; r >>= 1;
    }
    return ans;
}

int main() {
    // cin, cout의 입출력을 scanf, printf만큼 빠르게 해 주는 코드이다.
    ios::sync_with_stdio(0); cin.tie(0);

    int N; cin >> N;
    bias = 1 << ((int)floor(log2(N)) + 1);
    seg.resize(bias << 1 | 1);
    for(int i = 1; i <= N; i++) {
        int n; cin >> n;
        update(i, n);
    }

    int Q; cin >> Q;
    while(Q--) {
        int op, a, b; cin >> op >> a >> b;
        if(op == 1) {
            update(a, b, 1, 1, N);
        }
        else {
            cout << query(a, b, 1, 1, N) << endl;
        }
    }
}
```

## 연습 문제

- [#2042 구간 합 구하기 [G1]](https://www.acmicpc.net/problem/2042)
- [#2357 최소값과 최대값 [G1]](https://www.acmicpc.net/problem/2357)
