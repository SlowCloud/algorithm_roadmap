## 기초

- 자료구조

  - 트리와 그래프
  - 해시맵, 집합
  - [스택](basic/Stack.md)
  - 큐
  - 덱
  - 우선순위 큐

- 알고리즘

  - 정렬
  - 브루트 포스
  - [이분 탐색](basic/binarySearch.md)
    - 매개 변수 탐색
  - 분할 정복
  - [DFS/BFS](basic/FirstSearch.md)
    - 0-1 너비 우선 탐색
  - [그리디 알고리즘](basic/greedy.md)
  - 재귀/백트래킹
  - [**다이나믹 프로그래밍**](basic/DP.md)
    - 비트마스킹을 이용한 DP
    - 트리에서의 DP
    - 가장 긴 증가하는 부분수열(LIS)
  - 최단 경로
    - [다익스트라](basic/dijkstra.md)
    - [플로이드-워셜](basic/floid.md)
    - [벨만-포드](basic/bellman.md)
  - [분리 집합](basic/unionFind.md)
  - 최소 간선 트리
    - [크루스칼](basic/kruskal.md)
    - [프림](basic/prim.md)
  - [투 포인터](basic/twoPointer.md)
  - 비트마스킹
  - [**구현**](basic/implementation.md)

- 수학

  - 정수론
    - 모듈로 연산
    - 소수 판별
      - [에라토스테네스의 체](basic/math/eratosthenes.md)
    - 최대공약수/최소공배수
      - 유클리드 호제법
  - 선형대수
    - 행렬 연산
  - [분할정복을 이용한 빠른 거듭제곱](basic/FastPower.md)
  - 조합론
    - DFS를 이용한 조합 구하기
    - 비트마스킹을 이용한 조합 구하기
    - STL을 이용한 조합 구하기

- 기타
  - STL

## 초급

- 자료구조

  - [**세그먼트 트리**](beginner/SegmentTree.md)
  - [펜윅 트리, 인덱스 트리](beginner/Fenwick.md)

- 알고리즘
  - [위상 정렬](beginner/topologicalSort.md)
  - 다이나믹 프로그래밍
    - 가장 긴 증가하는 부분수열(LIS) ( $O(NlogN)$ )
    - 최장 공통 문자열(LCS)

코딩 테스트를 준비하시는 분은 여기까지 공부하시면 좋습니다.

- 수학

  - [페르마의 소정리](beginner/ferma.md)
    - [모듈로 역원](beginner/modular_inverse.md)

- 기하학

  - [외적(CCW)](beginner/ccw.md)
  - 선분 교차
  - 다각형의 넓이 구하기

- 기타
  - bits/stdc++.h
  - 무작위화

## 중급

- 자료구조

  - [느리게 갱신되는 세그먼트 트리](intermediate/LazyProp.md)
  - 머지 소트 트리
  - \*트라이

- 알고리즘

  - 그래프
    - [오일러 투어 트릭](intermediate/ETT.md)
    - [단절점/단절선](intermediate/Articulation.md)
    - [강한 연결 요소](intermediate/scc.md)
      - 이중 연결 요소
    - [네트워크 플로우](intermediate/NetworkFlow.md)
      - [이분 매칭](intermediate/BipartiteMatching.md)
      - 2-SAT
      - 최대 유량/최소 컷(MFMC)
      - 최소 거리 최대 유량(MCMF)
  - 희소 배열
    - 최소 공통 조상(LCA)
  - 문자열 알고리즘
    - [KMP](intermediate/kmp.md)
    - [트라이](intermediate/trie.md)
    - 라빈-카프
    - 매내쳐
  - [오프라인 쿼리](intermediate/offline_query.md)
    - [mo's](intermediate/mo's.md)
  - 제곱근 분할법
  - 삼분 탐색

- 기하학

  - 볼록 껍질(Convex Hull)
  - 회전하는 캘리퍼스
  - 볼록 다각형 내 점 판정

- 수학

  - 정수론
    - 밀러-라빈 소수 판별법
    - 폴라드 로
    - 확장 유클리드 호제법
  - 조합론
    - 뤼카 정리
  - 비둘기집 원리
  - 포함-배제의 원리
  - ...

- 기타
  - 런타임 전의 전처리
  - 애드 혹
  - 오일러 회로
  - 해밀턴 경로

## 고급

자주 변경될 예정

- 자료구조

  - 다차원 세그먼트 트리
  - 세그먼트 트리 비츠
  - [스플레이 트리](advanced/Splay.md), 트립
    - 링크/컷 트리
  - 레드 블랙 트리
  - 리 차오 트리
  - 동적 세그먼트 트리
  - 퍼시스턴트 세그먼트 트리
  - 키네틱 세그먼트 트리
  - ...

- 알고리즘

  - [헤비-라이트 분할](advanced/HLD.md)
  - [센트로이드 분할](advanced/CentroidDivison.md)
  - 문자열 알고리즘
    - 아호-코라식
    - 접미사 배열과 LCP 배열
    - Z 알고리즘
    - 접미사 트리
  - 스프라그 그런디 정리
  - 병렬 이분 탐색
  - 다이나믹 프로그래밍
    - DP 최적화
      - monge array
      - [볼록 껍질을 이용한 최적화(Convex Hull Trick)](advanced/CHT.md)
      - [분할 정복을 이용한 최적화(DnC Optimization)](advanced/DnCOpt.md)
      - 크누스 최적화(Knuth)
      - 단조 큐를 이용한 최적화(monotone queue opt)
      - [에일리언 트릭(Aliens Trick)](advanced/aliens.md)
      - 함수 개형을 이용한 최적화(Slope Trick)
      - 히르쉬버그
    - 커넥션 프로파일 DP
    - 키타마사법
      - 벌러켐프 매시
  - ...

- 수학

  - 정수론
    - 중국인의 나머지 정리(CRT)
    - ...
  - 고속 푸리에 변환(FFT)
    - z변환
    - ...
  - BigInteger
    - 카라추바의 빠른 곱셈
  - ...

- 기타
  - 알고리즘 외적인 최적화
    - FAST I/O(fread)
    - 컴파일 단계에서의 최적화
      - 실행 속도 향상 컴파일 옵션(GCC Ofast, O3, ...)
      - 병렬 연산 옵션(SIMD)
      - 컴파일 단계에서의 계산(constexpr)
    - 공간복잡도 최적화
      - Bitset을 이용한 최적화
  - bits/extc++.h
