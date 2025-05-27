
```python
import sys
from collections import deque
sys.setrecursionlimit(10000) #재귀함수 실행횟수 제한->만번

input = sys.stdin.readline #표준입력스트림의 readline함수

n,m,v = map(int,input().split()) #input함수가 받은 값을 정수형으로 변환(int)해서 공백으로 구분->ex)6ㅁ5

A = [ [] for _ in range(n+1) ] #2차원 리스트 선언(인접리스트) , _(반복변수 지정x)
visited_dfs = [False] * (n+1) #방문리스트 선언,n+1만큼 false
visited_bfs = [False] * (n + 1) 

for _ in range(m):
    s , e = map(int, input().split()) #간선의 시작->s,끝->e
    A[s].append(e) # 양방향 엣지이므로 양쪽에 엣지 추가
    A[e].append(s)

for i in range(1, n + 1):
    A[i].sort()


def DFS(v):
    visited_dfs[v] = True #방문하면 -> true
    print(v, end=' ')
    for i in A[v]:
        if not visited_dfs[i]:
            DFS(i)

def BFS(v):
    queue = deque([v])
    visited_bfs[v] = True
    while queue:
        now = queue.popleft()
        print(now, end=' ')
        for i in A[now]:
            if not visited_bfs[i]:
                visited_bfs[i] = True
                queue.append(i)

DFS(v)
print()
BFS(v)
