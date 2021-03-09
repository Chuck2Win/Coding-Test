# 이진 검색(Binary Search Algorithm)

- 이진 검색은 **정렬된 array**에 한해서 실시함.

- divided & conquer(주로 재귀로 구현) 느낌

  

 ```python
# 단순한 접근 - 시간 복잡도 O(N)
# 정렬이 되어 있으니 시간 복잡도가 O(N)임
min_value = float('inf')
for i in range(N):
	if min_value>A[i]:
        min_value = A[i]
 ```



```python
A = [12,15,15,19,24,31,53,59,60] # 정렬되어 있음 # N = 8
x = [31]
# 기존의 경우 시간 복잡도 N
# 이진 검색의 경우 O(logN)
A = [12,15,15,19,24,31,53,59,60] # 정렬되어 있음 # N = 8
x = 31
# 기존의 경우 시간 복잡도 N
# 이진 검색의 경우 O(logN)
def binary_search(A,x):
    start = 0
    end = len(A)-1
    while start<end: # log2N
        mid = (start+end)//2
        print(A[mid])
        if A[mid]<x:
            
            start = mid
        elif A[mid]>x:
            end = mid
        else:
            return mid
        i+=1
    return False
```

## Codility MinMaxDivision 문제

### 본인은 DFS를 활용한 BruteForce로 풀었음.

- 시간 초과..