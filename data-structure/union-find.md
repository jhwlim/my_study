# Union-Find 알고리즘
## Disjoint Set
- 서로 중복되지 않는 부분 집합들로 나눠진 원소들에 대한 정보를 저장하고 조작하는 자료구조
- 서로소 집합 자료구조
- ex : {1, 2}, {3, 4} → {1, 2, 3, 4}의 부분집합에서 서로 중복되지 않는다.

## Union-Find 알고리즘
- Disjoint Set을 표현할 때 사용한다.
- 배열, 연결리스트를 이용하여 구현할 수 있으나, 트리구조를 이용하는 것이 효율적이다!

## 구현 Step
1. 초기화
- 각 원소를 유일한 유일한 원소로 하는 집합을 생성한다.
- ex : {1, 2, 3} → {1}, {2}, {3}

2. union (x, y)
- x가 속한 집합과 y가 속한 집합을 합친다.
- ex : {1}, {2} → {1, 2}

3. find (x)
- x가 속한 집합의 대표값(루트노드)을 반환한다.
- x가 어떤 집합에 속해있는지 찾는다.

## 배열로 구현하기
1. 초기화
- 새로운 배열을 생성하고 값을 자기 번호로 셋한다.
```java
int[] parents = new int[];
for 
    parents[i] = i;
```

2. union (x, y) 구현
- 배열을 순회하면서 y의 집합 번호를 x로 변경한다.
```java
union(x, y) {
    px = find(x);
    py = find(y);
    parents[py] = px;
}
```

3. find (x) 구현
- x가 속한 집합 번호를 반환한다. (자기 자신이라면 종료)
```java
find(x) {
    while (x != parents[x]) {
        x = parents[x];
    }
    return x;
}
```

## 트리로 구현하기
```java
class Node {
    int data;
    Node parent;
}
```

1. 초기화
- 각 노드를 생성한다. 부모 노드를 설정하지 않았기 때문에 null이며, 각 노드가 루트 노드를 의미한다.

2. union
```java
union(Node x, Node y) {
    Node px = find(x);
    Node py = find(y);
    py.parent = px;
}
```

3. find
```java
find(Node x) {
    while (x != null) {
        x = x.parent;
    }
    return x;
}
```

## 최적화 방법
정리 필요

## Reference
<https://gmlwjd9405.github.io/2018/08/31/algorithm-union-find.html>