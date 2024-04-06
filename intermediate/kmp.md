## 선행

## 연관

- 아호-코라식

# CCW, 외적

> 문자열 탐색을 $O(NM)$보다 빠르게 진행해 봅시다.

문자열 검색 실패 시, 동일한 문자열을 중복해서 검사하지 않도록 index table을 만들어서 검사를 진행하는 알고리즘입니다.

## 구현

> C++

```cpp
vector<int> build(string s) {
    vector<int> p(s.size());
    for(int i=1,j=0;i<s.size();i++) {
        while(j && s[i] != s[j]) j = p[j - 1];
        if(s[i] == s[j]) {
            p[i] = ++j;
        }
    }
    return p;
}

bool kmp(string text, string target) {
    vector<int> p = build(target);
    for(int i=0,j=0;i<text.size();i++) {
        while(j && text[i] != target[j]) j = p[j -1];
        if(text[i] == target[j]) {
            if(j == target.size() - 1) {
                return true;
            }
            else j++;
        }
    }
    return false;
}
```
