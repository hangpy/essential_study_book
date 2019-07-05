# 다익스트라 알고리즘

- 간선에 가중치가 있는 방향성 그래프에서 쓰임.

- '**한 정점**'으로부터 '**모든 정점**'으로의 최단 거리, 혹은 최단 경로를 알고 싶을 때 쓰임

- '특정 정점'으로의 최단 거리를 알고싶을 때도 쓸 수 있음. (최단 거리를 구하면 멈추면 됨)

- 다익스트라의 `핵심 뿌리`는 다음과 같다

  > 최단거리는 최단거리를 포함한다. 예를들어 1부터 4까지의 최단 경로가 1, 5, 7, 4 라면, 1부터 5, 1부터 7, 5부터 7, 5부터 4, 7부터 4의 최단 경로를 포함한다.

- [도움이 많이 된 블로그 설명글](https://jason9319.tistory.com/307)

<br>

<br>

<br>

## 다익스트라를 이해할 때의 의문점

1.  왜 `max_heap`을 사용해서 최상단에 있는 후보군만 업데이트를 하는가?
2.  그렇다면 이후 삽입되는 후보에 대해서 더 짧은 최단 거리의 가능성은 없는 것인가?

<br>

<br>

<br>

## 위 의문에 대한 답

1.  여기서 간과하지 말아야 할 것이 있다. 다익스트라는 `한 정점`으로부터의 **최단거리**이다. 정해진 정점으로부터 각 노드의 최단거리 후보군이 지속적으로 `priority_queue`에 삽입이 되는데, 이 때, `거리`는 그 **길이가 점점 더 늘어난다**. 때문에 그 이후의 정점에 대한 후보군은 최단거리가 아니게 되는 것이다.
2. `heap`은 이전에 구해놨던 최단거리 후보군을 모두 기억하고 있다. 때문에 이미 출발 노드에서 해당 노드까지의 최단 경로 및 최단 거리가 업데이트 되었다면, 그 뒤에 나오는 해당 노드에 대한 경로, 거리는 무시할 수 있는 것.
3. 최단 경로는 특정 노드까지의 경로에서 구하고자 하는 노드까지의 최단거리가 구해졌다면, ''특정 노드까지의 경로 + 구하고자 하는 노드'' 식으로 구하면 된다.

<br>

<br>

<br>
