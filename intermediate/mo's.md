## 선행

- 오프라인 쿼리

## 연관

- 평방분할 / 제곱근 분할법

# mo's 알고리즘

> 구간 쿼리를 $O((N + Q)sqrt(N))$ 안에 처리하는 알고리즘

쿼리를 sqrt(N)을 기준으로 재정렬한 뒤 처리하는 알고리즘.

구간의 양 끝을 가리키는 $l$, $r$을 움직이면서 구간 내 쿼리를 갱신하면서 푼다.

쿼리의 좌측을 $sqrt(N)$을 기준으로 정렬하므로, 매 쿼리마다 최대 $O(sqrt(N))$번 움직이고, 


작성중