# StoneWall

## 해결 방법

1. H[i+1]>H[i] - 새로운 블록이 생김
2. H[i+1]<H[i] - 벽을 닫는다.

:star: 길이를 체크할 stack 생성

``` {python}
# 같은 경우는 무시하는 구나...
def solution(H):
    stack = []
    count = 0
    for i in H:
        # 작아질 경우
        while len(stack)>0 and stack[len(stack)-1]>i:
            stack.pop()
        if len(stack)==0 or stack[len(stack)-1]<i: # stack에 아무것도 없거나, 커질 같은 경우
            stack.append(i)
            count+=1
    return count
```

