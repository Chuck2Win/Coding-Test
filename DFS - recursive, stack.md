# DFS - recursive, stack

## 전역 변수 관련

자주 생겼다 지우는 변수가 나오면 전역변수를 쓰는 것이 좋다고 하네.



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

![312](https://github.com/Chuck2Win/Coding-Test/blob/master/img/312.png)

![3121](https://github.com/Chuck2Win/Coding-Test/blob/master/img/3121.png)
