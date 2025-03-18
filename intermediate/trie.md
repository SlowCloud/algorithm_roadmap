## 선행


## 연관

- DFS
- 트리

# 트라이

> 주어지는 문자열이, 찾고자 하는 여러 문자열에 포함되어 있는지 O(N)에 확인하는 알고리즘

여기서 N은 문자열의 길이를 나타낸다.

여기까지 들으면 이분 탐색의 하위호환처럼 들리지만, 특유의 구조를 이용한 트라이만의 독특한 문제 풀이가 가능하다.

구조도 원리도 크게 어렵지 않아서 쉽게 배울 수 있다.


트리의 원리를 사용한다. 각 노드는 각 문자열들마다의 분기를 가지고 있고, 해당 분기를 계속 타고 내려가면서 노드를 생성하는 형태이다.  
문자열의 끝에 다다르면, 해당 노드에 exist를 체크하고 빠져나오는 식이다.

최근 코딩 테스트 등에서 자주 나오고 있다.

```C++
// find를 통해서, put으로 입력한 동일한 문자열이 존재하는지 확인하는 로직을 작성했다. 필요에 따라 조금씩 수정해서 사용하면 된다.
// find에 입력한 문자열을 prefix로 가지는 문자열의 개수를 구한다던지 등등.
struct Trie {
  map<char, Trie*> next;
  bool exist = false;
  void put(string s) {
    Trie* now = this;
    for(char c : s) {
      if(now->next.find(c) == now->next.end()) {
        now->next[c] = new Trie();
      }
      now = now->next[c];
    }
    now->exist = true;
  }
  bool find(string s) {
    Trie* now = this;
    for(char c : s) {
      if(now->next.find(c) == now->next.end()) {
        return false;
      }
      now = now->next[c];
    }
    return now->exist;
  }
}
```
