# 탐색알고리즘 - 깊이 우선 탐색

<aside>
💡 탐색알고리즘: 그래프의 모든 정점들을 특정한 순서에 따라 방문하는 알고리즘

</aside>

- 가장 직관적이고 구현하기 쉬운 탐색 방법
- 현재 정점과 연결된 정점들을 하나씩 갈 수 있는지 검사하고, 특정 정점으로 갈 수 있다면 그 정점에 가서 같은 행위를 반복한다.
- 같은 정점을 다시 방문하지 않도록 정점에 방문했다는 것을 표시해준다.
- [**재귀 함수**](https://www.notion.so/Recursion-87a7c5e5bf4947158773e54dc9a899a8)를 통해 구현한다.

---

바이너리 트리의 루트노드에서 말단 노드까지 가는 최단 루트의 길이를 찾는 알고리즘을 구현하고자 한다.

```java
class Node {
    int data;
    Node_9 lt, rt;

    public Node_9(int value){
        data = value;
        lt = null;
        rt = null;
    }
}
```

바이너리 트리의 노드를 클래스로 구현한다.

```java
public static void main(String[] args) {
    _9_Shortest_Path_DFS tree = new _9_Shortest_Path_DFS();
    tree.root = new Node_9(1);
    tree.root.lt = new Node_9(2);
    tree.root.rt = new Node_9(3);
    tree.root.lt.lt = new Node_9(4);
    tree.root.lt.rt = new Node_9(5);

    tree.DFS(tree.root, 0);
    System.out.println(tree.minDist);
}
```

바이너리 트리를 초기화한다.

DFS 메서드의 매개변수로 루트노드와 루트노드와의 거리를 넘겨준다.

```java
int minDist = Integer.MAX_VALUE;

public void DFS(Node node, int dist){
		if(disf > minDist) return;
    if(isTerminalNode(node))
            minDist = Math.min(count, dist);
    else {
            DFS(node.lt, dist+1);
            DFS(node.rt, dist+1);
    }
}

public boolean isTerminalNode(Node node){
    return node.lt == null && node.rt == null;
}
```

좌측 노드부터 탐색을 시작한다.

isTerminalNode 메서드를 사용하여 현재 탐색중인 노드가 말단 노드 라면

minDist 의 값과 비교하여 최소 값을 저장한다.

매개변수로 넘어온 dist 값이 minDist 값보다 크다면 더이상 탐색할 필요가 없기 때문에 돌아간다.

모든 탐색이 종료되면 minDist를 출력한다.