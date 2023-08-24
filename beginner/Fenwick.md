## 선행

- 배열
- 2의 보수
- 비트마스킹

## 연관

- 세그먼트 트리

# 펜윅 트리(인덱스 트리)

> 구간합 세그먼트 트리를 간결하게 작성해 봅시다.

2의 보수의 특성을 이용해서 빠르게 세그먼트 트리의 원리를 구현하는 자료구조이다.

어떤 변수 i가 3이라는 숫자를 가지고 있다고 가정한다.<br>
비트로 나타내면 0b00000101이라는 값을 가지고 있다.<br>
-i를 비트로 나타내면 0b11111011를 가진다.<br>
i & -i를 하면 현재 i가 가리키는 숫자의 가장 오른쪽 비트를 가리키게 된다.<br>
이는 다른 모든 숫자에서도 동일하다.<br>
이 원리를 이용하여 세그먼트 트리를 구성하는 것이다.


## 구현

> C++

```

int fenwick[100'001];
int size = 100'000;

// 배열의 i에 v만큼의 값을 추가한다.
void add(int i, int v) {
    while(i <= size) {
        fenwick[i] += v;
        i += (i & -i);
    }
}

// 배열의 1 ~ i까지의 원소들의 합을 구한다.
// u ~ v 사이의 값을 구하려면 sum(v) - sum(u - 1)을 구하면 된다.
void sum(int i) {
    int ans = 0;
    while(i) {
        ans += fenwick[i];
        i -= (i & -i);
    }
    return ans;
}

```

> 구조체로 구현
```
// 세그먼트 트리보다 확실히 구현량이 적은 것을 확인할 수 있다.
struct Fenwick {
    int n; vector<long long> seg; Fenwick(int n): n(n), seg(n+1) {}
    void add(int i, int v) { while(i <= size) { fenwick[i] += v; i += i & -i; } }
    void query(int i) { long long res = 0; while(i) { res += seg[i]; i -= i & -i; } return res; }
}
```

[더 자세한 설명](https://www.acmicpc.net/blog/view/21)