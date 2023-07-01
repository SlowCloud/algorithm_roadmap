## 선행

- 분할 정복
- 수학(행렬)

## 연관

- 그래프 이론

# 분할정복을 이용한 빠른 거듭제곱

> $a^N$ 연산을 $O(logN)$ 안에 수행해 봅시다.

$a^N$ 연산은 보통 $O(N)$ 만큼의 시간복잡도를 가지지만, 분할 정복을 이용해서 $O(logN)$ 안에 해결할 수 있다.

일반적으로는 행렬의 제곱을 빠르게 계산할 때 사용한다.

분할 정복의 원리는 아래의 식을 활용하는 것이다.

> $a^N = a^{\frac{N}{2}} \times a^{\frac{N}{2}} (\times a)$

코드는 재귀로도 작성할 수 있고, 반복문으로도 작성할 수 있다.

```
// 재귀 코드

int mult(int a, int n) {
    if(n % 2) {
        return a * mult(a, n - 1) % MOD;
    }
    int tmp = mult(a, n/2);
    return tmp * tmp % MOD;
}
```

```
// 반복문 코드

while(n) {
    if(n % 2) {
        answer *= a;
        answer %= MOD;
        n -= 1;
    }
    a *= a;
    a %= MOD;
    n >>= 1;
}
```

문제로 주어질 때에는, 어떤 그래프의 정점 A에서 N번 이동하였을 때 B까지 갈 수 있는 방법의 수를 구할 때 따위에서 사용된다.

그래프를 구성한 뒤, 해당 그래프를 N번 행렬곱하여 구할 수 있다.

## 연습문제

- 연습 문제
    - [곱셈[S1]](https://www.acmicpc.net/problem/1629)
    - [행렬 거듭제곱[G4]](https://www.acmicpc.net/problem/10830)


실제 코딩테스트에서는 아래와 같은 식으로 나온다.

- 응용 문제
    - [본대 산책 2[G1]](https://www.acmicpc.net/problem/12850)