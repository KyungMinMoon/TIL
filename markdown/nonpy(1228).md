## STACK (통 이라 생각해)
First In Last Out
1) 들어가는 거 push
2) 나오는 거 pop


함수 def factorial (7):
    return factorial (n-1) * n

칸이 있다면
f(1)
f(2)
f(3)
f(4) = 4 * f(3)
f(5) = 5 * f(4)

f(5)가 가장 먼저 들어갔지만, 가장 먼저 나오는 건 f(1)

## Queue(대기줄 이라 생각해)

First In First Out
1) 들어가는 거 enqueue(인큐) = append
2) 나가는 거 dequeue(디큐) = pop(0)


표를 그릴 때,
1) 리스트 안에 딕셔너리
2) graph


### graph
1) 방향 그래프
2) 무방향 그래프
3) 가중치 그래프

cycle이 있으면 graph
없으면 Tree ex) 정부

graph by 2 array (선이 많고, 시간에 있어서 우세)

장점 : 관계 찾는데에 드는 시간이 굉장히 짧음 

단점 : 공간을 많이 차지함

graph by adj list(공간에 있어서 좋음)

장점 : 공간을 적게 차지함

단점 : 관계 찾는데에 시간이 오래 걸림. 하나하나 '너 맞냐?' 확인해야하니까

####
1부터 N까지의 자연수를 모두 더하는 알고리즘
O(1) = n(n+1) / 2 
O(n) = 1+2+3+4+5+...

n 이 낮으면 낮을수록 좋다. 간단한 거니까! o(1)이 더 좋은거야!
