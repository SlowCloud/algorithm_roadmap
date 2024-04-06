## 선행

- 기하학
- 선형대수

## 연관

대부분의 PS 기하학 문제에서 쓰이는 알고리즘이 해당 알고리즘을 기반으로 한다.

- 선분 교차 판정
- 삼각형의 넓이 구하기
- 다각형의 넓이 구하기
- 볼록 껍질
- 회전하는 캘리퍼스
- 볼록 다각형 내 점 판정

# CCW, 외적

> 외적을 구해 봅시다.

    설명 추가 예정

## 구현

> C++

```cpp
// 1이면 반시계, 0이면 직선, -1이면 시계를 이룬다.

using ll = long long;
using pll = pair<ll, ll>;

int ccw(pll a, pll b, pll c) {
    int t = (a.first - b.first) * (c.second - b.second) - (a.second - b.second) * (c.first - b.first);
    return (t>0) - (t<0);
}
```
