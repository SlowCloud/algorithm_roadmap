## 선행

- 재귀/백트래킹
- 스택
- 큐

## 연관

- DFS
    - 분할 정복
    - 다이나믹 프로그래밍
    - 단절점/단절선
    - 오일러 투어 트릭
    - 이분 매칭
    - 헤비-라이트 분할

- BFS
    - 네트워크 플로우

# 깊이 우선 탐색/너비 우선 탐색

> 그래프, 또는 추상적인 상태나 자료들을 탐색하는 알고리즘


### 깊이 우선 탐색

설명 추가 예정

#### DFS로 조합 구하기

문자열이나 배열에 대해서 DFS 탐색을 하면 탐색 모양이 이진 트리처럼 변한다. 이 때, DFS 호출 시마다 방문기록을 모조리 기록하면 해당 문자열이나 배열의 모든 조합을 구할 수 있게 된다. 이는 재귀로 구현하는 것이 편하다. 분할 정복이나 백트래킹과 비슷하다.

### 너비 우선 탐색

탐색 깊이가 깊거나, 그 끝을 알 수 없을 때 사용하기 좋은 탐색 알고리즘이다.

설명 추가 예정

## 구현

- DFS
    - 재귀

    ```
    // 그래프
    vector<int> G[/* 정점 개수 */];

    // 정점 개수
    int V;

    // 그래프의 정점 s에서 e로 갈 수 있으면 참 반환
    bool dfs(int s, int e) {
        vector<int> vst(V + 1);
        vst[s] = 1;
        for(int next : G[now]) {
            if(vst[next]) continue;
            if(dfs(next, e)) return true;
        }
        vst[s] = 0;
        return false;
    }
    ```

    - 반복문

    ```
    // 그래프
    vector<int> G[/* 정점 개수 */];

    // 정점 개수
    int V;

    // 그래프의 정점 s에서 e로 갈 수 있으면 참 반환
    bool dfs(int s, int e) {
        vector<int> vst(V + 1);
        vst[s] = 1;
        stack<int> st; st.push(s);
        while(st.size()) {
            int now = st.top(); st.pop();
            for(int next : G[now]) {
                if(vst[next]) continue;
                vst[next] = 1;
                if(next == e) return true;
                st.push(next);
            }
        }
        return false;
    }
    ```

- BFS
    
    BFS는 반복문으로 해결하는 것이 좋다.
    ```
    // 그래프
    vector<int> G[/* 정점 개수 */];

    // 정점 개수
    int V;

    // 그래프의 정점 s에서 e로 갈 수 있으면 참 반환
    bool bfs(int s, int e) {
        vector<int> vst(V + 1);
        vst[s] = 1;
        queue<int> q; q.push(s);
        while(q.size()) {
            int now = q.front(); q.pop();
            for(int next : G[now]) {
                if(vst[next]) continue;
                vst[next] = 1;
                if(next == e) return true;
                q.push(next);
            }
        }
        return false;
    }
    ```


## 연습 문제

- 기초

- 초급

- 중급