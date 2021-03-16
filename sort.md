# sort
## 1. Bubble sort
버블버블(두개두개)  
O(N^2)  

```{.python}
a=[8,7,1,9,0,7,8,4]
for i in range(1,len(a)):
    for j in range(len(a)-i):
        if a[j]>a[j+1]:
            a[j],a[j+1]=a[j+1],a[j]
print(a)
    
```
