# Dijstra Algorithm

#### # `비음` 가중치 그래프 +  `우선순위 Queue`

말이 우선순위 큐, 그냥 거리+지점을 넣어주는 의미라고 생각하면 될듯.

## BFS와의 비교

|            |      BFS      |    Dijstra    |
| :--------: | :-----------: | :-----------: |
|  내부구조  |     queue     | PriorityQueue |
| 시간복잡도 |       E       |     ElogV     |
|  활용경우  | `동일` 가중치 |    가중치     |

:heavy_check_mark: 시간복잡도

1) 각 정점(V)마다 인접한 간선(E) 계산 :arrow_right: 모든 간선은 1번만 검사된다(O(E))

2) 우선 순위 큐에 원소를 넣고 삭제 : E * 비교 연산 logE :arrow_right: O(ElogE)

- E의 max값 $2*C^V_2$

보통 E<=V이므로,  O(ElogV)

그리고, BFS에서 Edge는 Depth와 Breadth를 계산한 느낌이라고 생각하면 됨.

### **WHY** 우선순위  큐?

우선 순위 큐를 활용해야, 거리가 갱신되는 횟수가 줆.(거리가 중구 난방이면, 갱신되는 횟수 증가.)

## 구현

인접 노드 방문 :arrow_right:현재 알고 있는 거리보다 짧으면 갱신 

:heavy_check_mark: 이미 방문한 곳이라면 다시 방문하지 않는다. (이는  BFS에서와 유사) - 거리를 INF로 초기하는 이유

```python
import heapq
def dijstra(graph,start):
    visited=[]
    distance = {_:float('inf') for _ in graph.keys()}
    distance[start]=0
    next_visit=[]
    heapq.heappush(next_visit,(distance[start],start)) # 우선순위(수능등급), 지점
    while next_visit:
        print(distance)
        cur_distance, cur_point = heapq.heappop(next_visit) 
        # 만약 지금 꺼낸 것보다 짧은 경로를 안다면 무시!
        # 여기에, 이미 방문한 node에 대한 부분이 처리된다.
        # 이 비교를 하는 까닭은, 갱신되기 전의 값이 있을 수도 있기에.
        if cur_distance>distance[cur_point]: # 이 연산이 결국 E만큼 일어날 것임.
            continue
        # 근데 왜 priorityqueue를 쓰는가?
        # distance가 갱신되는 횟수가 줆.
        for next_point,next_distance in graph[cur_point].items():
            # 거리가 기존보다 짧아질 경우에만 추가
            if distance[next_point]>next_distance+distance[cur_point]:
                # 거리 역시 갱신
                distance[next_point]=next_distance+distance[cur_point]
                heapq.heappush(next_visit,(distance[next_point],next_point))
    return distance


```



:mag: queue.PriorityQueue 또는 heapq에서 활용

### Reference

https://wordbe.tistory.com/entry/%EC%B5%9C%EB%8B%A8%EA%B2%BD%EB%A1%9C-%EB%8B%A4%EC%9D%B5%EC%8A%A4%ED%8A%B8%EB%9D%BC-%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98#:~:text=%EC%8B%9C%EA%B0%84%EB%B3%B5%EC%9E%A1%EB%8F%84,%EB%94%B0%EB%9D%BC%EC%84%9C%20O(%7CE%7C)%2C&text=%EB%94%B0%EB%9D%BC%EC%84%9C%20%EC%B4%9D%20%EC%8B%9C%EA%B0%84%EB%B3%B5%EC%9E%A1%EB%8F%84%EB%8A%94,%7C)%EB%9D%BC%EA%B3%A0%20%EB%B3%BC%20%EC%88%98%EB%8F%84%20%EC%9E%88%EC%8A%B5%EB%8B%88%EB%8B%A4.



https://velog.io/@diddnjs02/%EC%A0%9C%EB%8C%80%EB%A1%9C%EC%95%8C%EA%B3%A0%EB%A6%AC%EC%A6%98%EB%8B%A4%EC%9D%B5%EC%8A%A4%ED%8A%B8%EB%9D%BC