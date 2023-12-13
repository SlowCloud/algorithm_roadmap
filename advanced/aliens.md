## 선행
- monge array

## 연관
- convex hull trick
- dnc optimization

# Aliens Trick(Lagrange Optimization)

> 이분 탐색으로 DP 최적해 찾기

식이 아래와 같이 정리될 수 있을 때 사용할 수 있다.

> $DP[i][j] = min_{k \lt j}(DP[i-1][k] + C[k+1][j])$