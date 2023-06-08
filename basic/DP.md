
## 선행

- 배열
- 재귀/백트래킹

## 연관

- 분할 정복
- 배낭 문제
- 투 포인터

# 다이나믹 프로그래밍


> 계산 결과를 저장해서 중복되는 계산을 최대한 줄이는 테크닉

쉬운 다이나믹 프로그래밍 문제들은 점화식을 찾는 것으로 쉽게 풀 수 있다.

스펙트럼이 정말 정말 넓은 문제이다. 다양한 문제를 접해보고 풀어보아야 한다.

### 타뷸레이션과 메모이제이션

다이나믹 프로그래밍은 두 가지 방법으로 풀 수 있다: 타뷸레이션, 메모이제이션.

k번째 피보나치 수열을 구하는 문제를 풀어본다고 가정한다.

타뷸레이션은 1, 2번째 피보나치 수에서부터 시작해서 k번째 피보나치 수열을 구하는 것이다.

```
int dp[100'001];
dp[1] = dp[2] = 1;
for(int i=3;i<=k;i++) {
    dp[i] = dp[i - 1] + dp[i - 2];
    // dp[i] %= MOD;
}
```

위와 같이 구하면 모든 피보나치 수열을 구하므로 $O(k)$만큼의 시간이 걸리지만, k 이하의 피보나치 수를 구할 때 $O(1)$만큼의 시간이 걸리게 된다.

메모이제이션은 필요한 만큼만 계산하는 방식이다. 재귀 함수를 이용하며, 복잡한 DP 문제에서 주로 활용하게 된다.

```
int dp[100'001];
// dp 배열을 모두 -1로 채우는 함수.
memset(dp, -1, sizeof(dp));
dp[1] = dp[2] = 1;

int kth(int i) {
    int& m = dp[i];
    if(m != -1) return m;
    return m = kth(i - 1) + kth(i - 2);
}
```
위 함수를 이용하면 타뷸레이션보다 Lazy하게 문제를 해결할 수 있게 된다. 피보나치 수열에서는 $O(k)$로 동일한 시간이 걸리지만, 복잡한 DP 문제로 변하면 해당 방식이 풜씬 유리해진다.

### 최적 부분 구조

DP 테이블을 구성할 때에는 어떤 상태에서 어떤 값을 기록할 것인지를 생각하는 것이 좋다.
피보나치 수열에서는 "k번째"가 상태가 되고, dp[k]에 k번째 피보나치 수가 기록된다.
잘 모르겠다면, 점화식을 생각해보는 것도 좋다.

해당 상태에서부터 결과까지의 값을 기록해야 할지, 아니면 처음 시작점에서부터 해당 상태까지의 결과값을 기록해야할지를 고민해보아야 한다. 이는 "최적 부분 구조"가 어느 곳에 있는지 파악하면 된다.

## 문제

쉬운 문제부터 어려운 문제까지.

### 기초

- [피보나치 수 4[S5]](https://www.acmicpc.net/problem/10826)

- [파스칼의 삼각형[S5]](https://www.acmicpc.net/problem/16395)

- [설탕 배달[S4]](https://www.acmicpc.net/problem/2839)

- [1로 만들기[S3]](https://www.acmicpc.net/problem/1463)

- [1, 2, 3 더하기[S3]](https://www.acmicpc.net/problem/9095)

- [RGB 거리[S1]](https://www.acmicpc.net/problem/1149)

- [오르막 수[S1]](https://www.acmicpc.net/problem/11057)

- [게임을 클리어하자[S1~G5]](https://www.acmicpc.net/problem/28017)

- [암호코드[G5]](https://www.acmicpc.net/problem/2011)

- [동전 1[G5]](https://www.acmicpc.net/problem/2293)

- 배낭 문제

    - [평범한 배낭[G5]](https://www.acmicpc.net/problem/12865)

    - [카우버거 알바생[G4]](https://www.acmicpc.net/problem/17208)

- 누적합

    - ...

### 초급

- 위상 정렬

    - [ACM Craft[G3]](https://www.acmicpc.net/problem/1005)

- 누적합

    - [파일 합치기[G3]](https://www.acmicpc.net/problem/11066)


- 비트마스킹을 이용한 DP

    - [그림 교환[G1]](https://www.acmicpc.net/problem/1029)

    - [외판원 순회[G1]](https://www.acmicpc.net/problem/2098)

    - [발전소[P5]](https://www.acmicpc.net/problem/1102)

- 그래프와 트리

    - [여행[G4]](https://www.acmicpc.net/problem/2157)

    - 트리에서의 DP

        - [트리와 쿼리[G5]](https://www.acmicpc.net/problem/15681)

        - [사회망 서비스[G3]](https://www.acmicpc.net/problem/2533)

    - 다익스트라

        - ...

- 복잡한, 또는 추상적인 상태

    - [타일 채우기[G5]](https://www.acmicpc.net/problem/2133)

    - [로봇 조종하기[G2]](https://www.acmicpc.net/problem/2169)

- 수학

    - [Ezreal 여눈부터 가네 ㅈㅈ[G5]](https://www.acmicpc.net/problem/20500)

**코딩테스트를 준비하시는 분들은 여기까지만 보시면 됩니다.**
<hr>

### 중급

- [다이아몬드 광산[P5]](https://www.acmicpc.net/problem/1028)

- [연세워터파크[P5]](https://www.acmicpc.net/problem/15678)

- 복잡한, 또는 추상적인 상태

    - [보안 업체[P3]](https://www.acmicpc.net/problem/4243)
    
    - [가로등 끄기[P3]](https://www.acmicpc.net/problem/2315)

    - [사수아탕[P1]](https://www.acmicpc.net/problem/2419)

- 수학

    - [k번째 이진십진수[P3]](https://www.acmicpc.net/problem/28143)

### 고급

- 벌러캠프 매시

    - [IQ 테스트[P4]](https://www.acmicpc.net/problem/9334)

    - [피보나치 수열처럼 보이지만...[D5]](https://www.acmicpc.net/problem/13716)

- DP 최적화

    - 볼록 껍질을 이용한 최적화

    - 분할 정복을 이용한 최적화

    - 큐를 이용한 최적화