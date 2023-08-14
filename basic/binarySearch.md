## 선행

- 없음

## 연관

- 매개 변수 탐색
- 가장 긴 증가하는 부분 수열($O(NlogN)$)

# 이분 탐색

> $O(logN)$ 안에 숫자를 찾아봅시다.

사실 웬만한 숫자 찾기는 $O(1)$ 안에 찾는 방법이 있지만, 숫자의 범위가 어마어마하게 큰 경우 등에서 사용하기 좋다.

### STL

C++에는 이분 탐색을 STL로 지원한다. lower_bound와 upper_bound가 있다.

lower_bound는 주어진 값과 같거나 큰 숫자의 시작점을 반환하고, upper_bound는 주어진 값보다 큰 숫자의 시작점을 반환한다.

```
#include <algorithm> // 해당 헤더에 이분 탐색 함수가 존재한다.
#include <vector>

vector<int> v;
int m[10];

int main () {

    for(int i = 0; i < 10; i++) {
        v.push_back(i); m[i] = i;
    }

    // 이분 탐색을 사용하려면, 배열이 정렬이 되어 있어야 한다.
    // 여기서는 숫자가 순서대로 입력되었으므로 정렬은 건너뛴다.
    // sort(v.begin(), v.end()); sort(m, m + 10);
    
    // 이분 탐색 함수는 이터레이터를 반환한다.
    auto iter = lower_bound(v.begin(), v.end(), 5);

    // 배열에 대해서도 사용할 수 있다.
    auto iter2 = lower_bound(m, m + 10, 5);
    
}

```

map과 set에서도 lower_bound와 upper_bound 메소드가 존재한다.

```
// 웬만한 STL을 한번에 불러오는 헤더
#include <bits/stdc++.h>

int main () {
    set<int> se;
    for(int i=0;i<10;i++) se.insert(i);
    auto iter = se.lower_bound(5);
}
```

## 연습 문제

- 연습 문제
    - [수 찾기[S4]](https://www.acmicpc.net/problem/1920)
    - [숫자 카드[S4]](https://www.acmicpc.net/problem/10816)