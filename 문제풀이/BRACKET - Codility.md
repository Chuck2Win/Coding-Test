# BRACKET - Codility

## STACK

First in Last Out

:comet: 보통 stack과 queue는 `같이` 쓰이는 경우가 많지

괄호는 (), [], {} 세 형태로 주어집니다.

예를 들어 {[()()]}은 알맞은 형태이지만, ([)()]은 틀린 형태입니다.

```python
from collections import deque
def solution(S):
    stack = deque([])
    for i in S:
        if i in ['(','{','[']:
            stack.append(i)
        else:
            if len(stack)==0:
                return 0
            else:
                next = stack.pop()
                if i == '}':
                    if next == '{':
                        continue
                    else:
                        return 0
                elif i==']':
                    if next == '[':
                        continue
                elif i==')':
                    if next =='(':
                        continue
                    else:
                        return 0
    return 1
```

