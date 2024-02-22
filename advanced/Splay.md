## 선행

- 세그먼트 트리
- 느리게 갱신되는 세그먼트 트리

## 연관

- 링크/컷 트리
- 문제가 요구하는 세그먼트 트리 테크닉

# 스플레이 트리

> Amortized $O(logN)$ 안에 노드 삽입, 노드 삭제, 구간 갱신, 구간 뒤집기, 구간 질의가 가능한 균형 이진 검색 트리(BBST)

트리 자료구조의 (거의) 끝판왕.

트리를 회전시켜 가장 최근에 사용한 노드를 루트 노드로 끌어올려 사용하는 형태의 자료구조이다.

스플레이 트리는 회전(rotate) 함수와 스플레이(splay) 함수를 기반으로 작동한다.


### rotate 함수

노드 x를 각 방향으로 회전시키는 함수이다.

아래의 노드를 한 칸 위로 끌어올릴 때 사용한다.

### splay 함수

splay 함수는 rotate 함수를 활용하여 주어진 노드를 root 노드까지(혹은 특정 노드 위치까지) 끌어올리는 함수이다.

끌어올릴 때, zig-zag, zag-zig와 zig-zig, zag-zag의 노드를 올리는 방식이 다른데, 이는 매 쿼리 시 트리가 이진 트리의 모습을 갖추도록 하기 위함이다.

자세한 내용은 [해당 문서](https://www2.hawaii.edu/~nodari/teaching/f19/scribes/notes06.pdf)를 참고하는 것을 추천한다.


### 구간 질의

스플레이 트리에서의 구간 질의는 위 함수를 기반으로 작동한다.

gather(int s, int e)는 s ~ e 사이의 노드의 정보를 가진 노드를 반환한다.

splay(e+1) 이후, 루트 노드의 왼쪽 노드에 대해 splay(s-1)을 수행하면, 루트 노드의 왼쪽 자식 노드의 우측 자식 노드에 원하는 구간에 대한 정보를 담는 노드가 생기게 된다.  
이 노드를 반환하면 된다.

lazy한 갱신은, 매 노드에 접근할 때마다 propagation하면 된다.


## 이모저모

트리 자료구조의 진짜 끝판왕은 모든 갱신/질의를 $O(logN)$ 안에 수행하는 레드 블랙 트리지만, 보통 STL map이나 set 등에 사용되고 있어 해당 자료구조로 해결할 수 있고,  구현 난이도가 높아서 복잡한 쿼리가 필요할 경우 비교적 간결한 스플레이 트리를 대신 사용한다.

## 연습 문제

- 연습 문제
    - [배열[P2]](https://www.acmicpc.net/problem/13159)

# 코드

> Short Version


> Long Version

```C++

struct Node {
    Node* l, Node* r;
    int v;
}

Node* rotateRight(Node* node) {
    /*
        node
        /
      left
        \
        middle
    
    becomes

         left
            \
            node
            /
        middle
    */
    Node* left = node.l, *middle = left.r;
    node.l = middle; left.r = node;
    return left;
}

Node* rotateLeft(Node* node) {
        /*
        node
            \
            right
            /
        middle
    
    becomes

        right
        /
    node
        \
        middle
    */
    Node* right = node.r, *middle = right.l;
    node.r = middle; right.l = node;
    return right;
}

Node* splay(Node* root, int value) {
    if(root == nullptr) return root;
    if(root->v == value) return root;

    /*
            root
            /
        ...
    */
    if(value < root->v) {
        /*
                root
                /
            target
        */
        if(root->l == value) {
            /*
                    target
                        \
                        root
            */
            root = rotateRight(root);
            return root;
        }

        /*
                    root
                    /
                left
                /
            ...
        */
        if(value < root.l.v) {
            /*
                        root
                        /
                    left
                    /
                target
            */
            root->l->l = splay(root->l->l);
            /*
                        left
                        /   \
                    target  root


            */
            root = rotateRight(root);
        }

        /*
                    root
                    /
                left
                    \
                    ...
        */
        else {
            /*
                        root
                        /
                    left
                        \
                        target
            */
            root->l->r = splay(root->l->r);
            /*
                        root
                        /
                    target
                    /
                left
            */
            root->l = rotateLeft(root->l);
        }

        /*
                target
                    \
                    root
        */
        root = rotateRight(root);
        return root;
    }

    // 오른쪽도 비슷하게 진행함.
    else {
        if(root->r->v == value) {
            root =rotateLeft(root);
            return root;
        }

        if(root->r->v < value) {
            root->r->r = splay(root->r->r);
            root = rotateLeft(root);
        }
        else {
            root->r->l = splay(root->r->l);
            root->r = rotateRight(root->r);
        }
        root = rotateLeft(root);
        return root;
    }

}

```