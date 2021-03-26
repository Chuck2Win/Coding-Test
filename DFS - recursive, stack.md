# DFS - recursive, stack

## 전역 변수 관련

자주 생겼다 지우는 변수가 나오면 전역변수를 쓰는 것이 좋다고 하네.

## DFS recursive - 현재상태, 후보 
- 주로 MAP관련인 경우는 DFS recursive를 쓰자

# process stack - 함수 호출시

```python
def recursive(data):
    if data==0:
        print('ended')
    else:
        print(data)
        recursive(data-1)
        print('returned',data)
```
- 순서
```{python}
recursive(3)

print(3)
recursive(2)
print('returned 3')

print(3)
print(2)
recursive(1)
print('returned 2')
print('returned 3')

print(3)
print(2)
print(1)
recursive(0)
print('returned 1')
print('returned 2')
print('returned 3')

print(3)
print(2)
print(1)
print('ended')
print('returned 1')
print('returned 2')
print('returned 3')
```


![312](https://github.com/Chuck2Win/Coding-Test/blob/master/img/312.png)

![3121](https://github.com/Chuck2Win/Coding-Test/blob/master/img/3121.png)

```{python}
# dfs recursive로 만든 조합
def dfs_recur(comb,candi,R): # 메모장, 후보
    if R == r:
        visited.append(comb)
        return
    else:
        for i in candi:
            new_candi = list(range(n))[i:]
            dfs_recur(comb+[i],new_candi,R+1) # 현재 지점, 다음 조건, 조건
```
