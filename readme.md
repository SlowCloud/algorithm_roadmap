## 기초

코딩 테스트를 준비하시는 분은 여기까지만 공부하셔도 좋습니다.

- 자료구조
  - 트리와 그래프
  - 해시맵, 집합
  - [스택](https://github.com/SlowCloud/algorithm_roadmap/blob/main/basic/Stack.md)
  - 큐
  - 데큐
  - 우선순위 큐

- 알고리즘
  - 정렬
  - 브루트 포스
  - 이분 탐색
    - 매개 변수 탐색
  - 분할 정복
  - [DFS/BFS](https://github.com/SlowCloud/algorithm_roadmap/blob/main/basic/FirstSearch.md)
  - 그리디 알고리즘
  - 재귀/백트래킹
  - [**다이나믹 프로그래밍**](https://github.com/SlowCloud/algorithm_roadmap/blob/main/basic/DP.md)
  - 최단 경로
    - [다익스트라](https://github.com/SlowCloud/algorithm_roadmap/blob/main/basic/dijkstra.md)
    - 플로이드-워셜
    - 벨만-포드
  - 분리 집합
  - 최소 간선 트리
    - 크루스칼
    - 프림
  - 투 포인터
  - [**구현**](https://github.com/SlowCloud/algorithm_roadmap/blob/main/basic/implementation.md)

- 수학
  - 정수론
    - 모듈로 연산
    - 소수 판별
      - 에라토스테네스의 체
    - 최대공약수/최소공배수
      - 유클리드 호제법
  - 분할정복을 이용한 빠른 거듭제곱
  - 조합론
    - DFS를 이용한 조합 구하기
    - 비트마스킹을 이용한 조합 구하기

- 기타
  - STL

## 초급

- 자료구조
  - [**세그먼트 트리**](https://github.com/SlowCloud/algorithm_roadmap/blob/main/beginner/SegmentTree.md)
  - 펜윅 트리, 인덱스 트리

- 알고리즘
  - 위상 정렬
  - 비트마스킹
  - 다이나믹 프로그래밍
    - 비트마스킹을 이용한 DP
    - 트리에서의 DP
    - 덱을 이용한 DP
    - 가장 긴 증가하는 부분수열(LIS)
    - Longest Common Subsequence

- 수학
  - 정수론
    - 페르마의 소정리를 이용한 소수 판별
  - 선형대수
    - 행렬 연산
  - 비둘기집 원리

- 기타
  - bits/stdc++.h

## 중급

- 자료구조
  - [느리게 갱신되는 세그먼트 트리](https://github.com/SlowCloud/algorithm_roadmap/blob/main/intermediate/LazyProp.md)
  - 머지 소트 트리

- 알고리즘
  - [오일러 투어 트릭](https://github.com/SlowCloud/algorithm_roadmap/blob/main/intermediate/ETT.md)
  - [단절점/단절선](https://github.com/SlowCloud/algorithm_roadmap/blob/main/intermediate/Articulation.md)
  - 강한 연결 요소
  - [네트워크 플로우](https://github.com/SlowCloud/algorithm_roadmap/blob/main/intermediate/NetworkFlow.md)
    - 이분 매칭
    - 2-SAT
    - 최대 유량/최소 컷
    - 최소 거리 최대 유량
  - 최소 공통 조상(LCA)
    - 희소 배열
  - 기하학
    - 선분 교차
    - 외적(CCW)
      - 볼록 껍질(Convex Hull)
      - 회전하는 캘리퍼스
  - 문자열 알고리즘
    - KMP
    - 트라이
  - 오프라인 쿼리
    - mo's
  - 삼분 탐색

- 수학
  - 정수론
    - 밀러-라빈 소수 판별법
    - 확장 유클리드 호제법
  - 포함-배제의 원리
  - ...

- 기타
  - 런타임 전의 전처리
  - 애드 혹

## 고급

공사중 - 자주 변경될 예정

- 자료구조
  - 다차원 세그먼트 트리
  - 퍼시스턴트 세그먼트 트리
  - 세그먼트 트리 비츠
  - 스플레이 트리, 트립
  - 링크/컷 트리
  - 레드 블랙 트리
  - 키네틱 세그먼트 트리
  - 리 차오 트리
  - ...

- 알고리즘
  - [헤비-라이트 분할](https://github.com/SlowCloud/algorithm_roadmap/blob/main/advanced/HLD.md)
  - 센트로이드 분할
  - 고급 문자열 알고리즘
    - 라빈-카프
    - 아호-코라식
    - 접미사 배열과 LCP 배열
    - Z 알고리즘
    - 매내쳐
    - 접미사 트리
  - 스프라그 그런디 정리
  - 병렬 이분 탐색
  - 제곱근 분할법
  - 다이나믹 프로그래밍
    - DP 최적화
      - monge array
      - 볼록 껍질을 이용한 최적화(Convex Hull Trick)
      - 분할 정복을 이용한 최적화(DnC Optimization)
      - 크누스 최적화(Knuth)
      - 단조 큐를 이용한 최적화
      - 에일리언 트릭(Aliens Trick)
      - 함수 개형을 이용한 최적화(Slope Trick)
    - 커넥션 프로파일 DP
    - 벌러켐프 매시
    - 히르쉬버그
    - 키타마사법
  - 무작위화
  - ...

- 수학
  - 정수론
    - 중국인의 나머지 정리(CRT)
    - 뤼카의 정리
    - ...
  - 고속 푸리에 변환(FFT)
  - ...

- 기타
  - 알고리즘 외적인 최적화
    - FAST I/O
    - 컴파일 단계에서의 최적화
      - 실행 속도 향상 컴파일 옵션
      - 병렬 연산 옵션(SIMD)
    - 공간복잡도 최적화
      - Bitset을 이용한 최적화
  - bits/extc++.h